## Introduction

When the AI generates text, the general procedure is as follows:

1. Your story is converted into tokens and input to the model.
1. The AI tries to predict what the next token in your story should be. However, the AI doesn't know how to explicitly pick a particular token. Instead, it ranks every possible token in its token vocabulary by assigning each one a "logit"<sup name="_logit">[[1]](#logit)</sup> value. Logits are real numbers,<sup name="_logit-real">[[2]](#logit-real)</sup> with very little consistent meaning other than the fact that tokens with higher logits are the ones the model is more confident in putting at the end of your story.<sup name="_logit-consistency">[[3]](#logit-consistency)</sup>
1. KoboldAI's code somehow uses the logits to help pick one token from the model's vocabulary to put at the end of your story.
1. The story with the one token added at the end is fed to the model again to generate another token. This process repeats until we have generated the number of tokens requested by the user (80 by default).

One of the central problems in AI story generation is related to that step where we have to pick one token based on the logits&mdash;how to pick the token so that the story is neither incoherent nor robotic.

No, we cannot just pick the token with the highest logit. That's called ***greedy search***; you can try it in KoboldAI by setting the top-p sampling value to 0.<sup name="_greedy-search-methods">[[4]](#greedy-search-methods)</sup> Greedy search leads to repetitive, boring text.

While there are many methods to pick tokens, the one that has received the most attention is ***sampling***, where we convert the logits into a probability distribution by using the ***[softmax function](https://en.wikipedia.org/wiki/Softmax_function)***.<sup name="_softmax">[[5]](#softmax)</sup>

Here's a layman's description of what the softmax function does, given example logits 2, -2.3, 1.12 and -3.9:

1. We raise [e (a mathematical constant approximately equal to 2.718)](https://en.wikipedia.org/wiki/E_(mathematical_constant)) to the power of each logit. We get the values 7.389, 0.100, 3.065 and 0.020 since ![](https://math.vercel.app/?color=gray&from=e^2) is approximately 7.389 and ![](https://math.vercel.app/?color=gray&from=e^{-2.3}) is approximately 0.100 and so on.
1. We normalize the values so that they add up to 1. In other words, we divide by their sum. So we get 0.699, 0.009, 0.290 and 0.002, because ![](https://math.vercel.app/?color=gray&from=\frac{7.389}{7.389%2B0.100%2B3.065%2B0.020}\approx0.699), etc.

The softmax function has some interesting properties, the most important of which are listed below:
* The probabilities are always greater than or equal to 0 and less than or equal to 1.
* The probabilities always add up to 1.
* The softmax function preserves the ordering of the tokens&mdash;token A has a higher probability than token B if and only if token A has a higher logit than token B.
* Adding the same number to the logits does not change the probabilities. If we add 1 to every logit, the probabilities do not change, but they will change if the values we add to each logit are not the same. *Multiplying* the logits by the same nonzero real number *does* almost always change the probabilities.
* In math libraries such as PyTorch, we can set logits to negative infinity. If a logit is negative infinity, the corresponding probability is always zero (since ![](https://math.vercel.app/?color=gray&from=\displaystyle\lim_{x\to-\infty}e^x=0)) as long as there is at least one logit that isn't negative infinity. Of course, there has to be at least one logit that isn't negative infinity, or else the behaviour is undefined.

With the logit values converted into ***probabilities*** that add up to 1, we just pick one using these probabilities as a probability distribution. So the token that had the logit of 2 would have a 69.9% probability of being picked.

The problem with sampling is that it still usually gives every token a possibility of appearing, so every once in a while a token that makes no sense will be inserted into your story. This is very noticeable when it happens, so ideally it shouldn't happen at all. There are many methods to improve sampling that involve inserting extra steps right before this sampling step.

## Sampling techniques

### Temperature / Randomness

One of the most basic methods is called temperature-controlled sampling.<sup name="_temperature-name">[[6]](#temperature-name)</sup> Temperature-controlled sampling was originally described in a 1985 paper, *[A Learning Algorithm for Boltzmann Machines](https://www.cs.toronto.edu/~fritz/absps/cogscibm.pdf)*, as a technique for controlling the randomness of an old type of neural network, but has proven itself to be an important technique for controlling randomness of modern text generation models.

Temperature-controlled sampling just involves dividing the logits by the temperature value. So if the temperature value is 0.5, then we divide all the logits by 0.5 prior to sampling.

The temperature value can be set to any real number not equal to zero (since setting it to zero would result in division by zero), but ideally it would be set to a positive real number so that the order of the tokens, when sorted by logit, does not invert. Setting the temperature value to exactly one disables temperature-controlled sampling.

Values greater than 0 and less than 1 cause the probabilities output by the softmax function to move further apart, thus decreasing randomness by making high probability tokens more likely and low probability tokens less likely. Values greater than 1 cause the probabilities to move closer together, increasing randomness. If the temperature value is set to exactly 1, the logits do not change, hence the probabilities remain unaffected.

### Top-k sampling

Another simple method is top-k sampling, a technique from mainstream statistics.

The top-k value can be set to any nonnegative integer. If it is set to 0, top-k sampling is disabled.

Given the top-k value k, we leave the largest k logits as is and set all the other ones to negative infinity. This has the effect of restricting the pool of considered tokens to the k most likely ones. This is intended to directly strike a balance between greedy search and pure sampling.

In practice, top-k sampling has proven to be worse at its job than most of the other sampling techniques and is usually used as a highly permissive filter to remove a small amount of low probability tokens before getting a more advanced sampling method to work on the remaining tokens.

Because of how top-k sampling works, it's highly recommended to have it as the first sampler in KoboldAI (other than temperature, it is okay to have that before top-k). This is because most of the other samplers also set some logits to negative infinity while leaving the others intact, but in a more intelligent way. If top-k comes after a more intelligent sampler and removes at least one token, then it just basically nullified the effects of the previous samplers.

### Top-p sampling / Nucleus sampling

Top-p sampling, also known as nucleus sampling,<sup name="_nucleus-sampling-name">[[7]](#nucleus-sampling-name)</sup> is one of the most widely used sampling methods in text generation. It was first described by the paper *[The Curious Case of Neural Text Degeneration](https://arxiv.org/pdf/1904.09751.pdf)*.

The top-p value must be greater than or equal to 0 and less than or equal to 1. Top-p sampling can be disabled by setting it to 1.

We first use the softmax function to convert the logits into probabilities. Then, we keep as many tokens as possible such that both of these rules are satisfied (by leaving the logits of the kept tokens unmodified and setting the logits of the other tokens to negative infinity):

* If a token is not kept, then all of the tokens with probability lower than its probability must also not be kept.
* The sum of the probabilities of the kept tokens must not exceed the top-p value, unless the highest probability is greater than the top-p value, in which case the token with the largest probability must always be kept (if there are multiple highest probability tokens then we pick an arbitrary one out of those) and all of the other tokens must not be kept.

Lower top-p values cause fewer tokens to be kept. Setting the top-p value to 0 is equivalent to greedy search.

It is intended to use a relatively high value like 0.9 or 0.95, since even values as high as these often keep at most a dozen tokens. Lower values would be detrimental to the creativity of the model.

### Top-a sampling

This is a relatively new sampling method intended for use with BlinkDL's RWKV language models. A description can be found at: https://github.com/BlinkDL/RWKV-LM/tree/4cb363e5aa31978d801a47bc89d28e927ab6912e#the-top-a-sampling-method.

The top-a value can be any real number greater than or equal to zero. Setting this to 0 disables top-a sampling.

In the top-a algorithm, the logits are converted to probabilities using the softmax function, then the tokens with probability less than ![](https://math.vercel.app/?color=gray&from=ax^2) have their logits set to negative infinity, where a is the top-a value and x is the largest probability.<sup name="_top-a-exponent">[[8]](#top-a-exponent)</sup>

Like in the top-p algorithm, one of the highest probability tokens must be kept, even if the highest probability is less than ![](https://math.vercel.app/?color=gray&from=ax^2).

This has the effect of removing more tokens when the maximum probability is very high and of removing few to no tokens when the maximum probability is low. In other words it reduces the randomness when the AI is extremely sure of what is supposed to come next, because chances are the AI is right in that specific case.

I have found that top-a sampling produces basically zero effect on the creativity of output text, which may be desirable, but if you want to change the creativity of your model, you should use something else in conjunction with this.

### Tail free sampling

A relatively complicated sampling method described at https://www.trentonbricken.com/Tail-Free-Sampling/.

This sampling method is designed with the hypothesis that when you sort the tokens in descending order of logit, the probabilities of these tokens usually plateaus after 10 or so tokens and forms an easily detectable "tail" of undesirable tokens that this algorithm can get rid of, hence the name "tail free" sampling.

Like in top-p sampling, the tail free sampling value must be a real number greater than or equal to 0 and less than or equal to 1. Setting this to 1 disables tail free sampling.

The following is a description of Trenton Bricken's TensorFlow implementation of the algorithm:

1. Apply the softmax function to the logits to get their corresponding probabilities.
1. Sort the tokens in descending order of probability (i.e. token with highest probability comes first and token with lowest probability comes last).
1. Calculate the first differences<sup name="_tail-free-sampling-differences">[[9]](#tail-free-sampling-differences)</sup> of these sorted probabilities. For example, if the sorted probabilities are 0.4, 0.3, 0.15, 0.1 and 0.05, then the first differences are -0.1, -0.15, -0.05 and -0.05 because 0.3 - 0.4 = -0.1, 0.15 - 0.3 = -0.15, 0.1 - 0.15 = -0.05 and 0.05 - 0.1 = -0.05.
1. Then calculate the second differences (the differences of the first differences) which in this case are -0.05, 0.1 and 0.
1. Take the absolute values of the second differences, so we have 0.05, 0.1 and 0.
1. Divide these values by their sum. We have 0.333, 0.667 and 0.
1. Compute the [cumulative sums](https://en.wikipedia.org/wiki/Prefix_sum) of these values (0.333, 1 and 1).
1. Add a 0 at the beginning and a 1 at the end (0, 0.333, 1, 1, 1).<sup name="_tail-free-sampling-centering">[[10]](#tail-free-sampling-centering)</sup>
1. Remove the tokens whose value as computed in the previous step is greater than the tail free sampling value (by setting their logits to negative infinity).

Note that this algorithm always keeps at least one of the highest probability tokens.

This sampling technique is supposed to not have as noticeable of an effect on story creativity as the other ones. It's pretty much designed exclusively to help you get rid of low probability tokens without touching creativity. In practice, top-a sampling does a better job at not affecting creativity.

Some people have recommended not using tail free sampling on extremely short stories. Maybe don't turn it on until your story is at least 10 sentences long.

### Typical sampling

An even more complex sampling method from the paper *[Typical Decoding for Natural Language Generation](https://arxiv.org/pdf/2202.00666.pdf)*. This sampling method produces a very pronounced effect on the output that you may or may not like.

Typical sampling is based on observations of the differences between the information content of human-generated text versus that of computer-generated text. It aims to keep the information content of text at a consistent level throughout the text as opposed to containing noticeable deviations of information content.

The typical sampling value must be larger than or equal to zero and less than or equal to one. Setting this to 1 disables it.

1. Use the softmax function on the logits to get the probabilities of the tokens.
1. Determine the entropy which is the additive inverse of the sum of the product of each probability with its own natural logarithm.<sup name="_typical-sampling-entropy">[[11]](#typical-sampling-entropy)</sup> The natural logarithm of zero is zero for the purposes of this calculation.
1. Sort the tokens in ascending order of the absolute value of the sum of the entropy and the natural logarithm of the token's probability.<sup name="_typical-sampling-sorting">[[12]](#typical-sampling-sorting)</sup>
1. Keep the minimum possible number of tokens (setting the other tokens' logits to negative infinity) such that:
    * The first token when the tokens are sorted in this order is always kept.
    * If a token is not kept, then all tokens after it when sorted in this order are also not kept.
    * The sum of the probabilities of the kept tokens is greater than or equal to the typical sampling value.

Unlike top-p, top-k, top-a and tail free sampling, a token being removed by the typical sampling algorithm does not imply that all tokens with lower logit are also removed. In other words, the typical sampling algorithm does not always preserve the ordering of tokens.

Typical sampling is known to have a very strong effect on the content of the output. However, even if you set it to an extremely low setting, the output should still be creative. It's kind of hard to explain what happens to the output, you should try it and see.

## Sampler ordering

KoboldAI allows you to use multiple of these sampling techniques at once by applying these modifications to the logits in series. KoboldAI also allows you to change the order of the samplers in this series, which can have a considerably different effect than just leaving the samplers at their default order.

Chasm has recommended the following sampling settings and sampler order for use with fairseq dense 13B models:

> Or what I do now is *temp0.8>typical0.19>tfs0.97>top-p0.6* which works wonders for me across the board on Fairseq13B, even Opt. The top-p being optional, top-k and top-a off for now. All repetition penalties left at default.

The default sampler ordering in KoboldAI is top-k, top-a, top-p, TFS, typical, temperature.

## Repetition penalty

Repetition penalty is a technique used to reduce repetition in generated text. It is an incredibly important setting that should almost always be enabled, especially for smaller models. It was introduced by the authors of the CTRL model in section 4.1 of *[CTRL: A Conditional Transformer Language Model for Controllable Generation](https://arxiv.org/pdf/1909.05858.pdf)*.

Repetition penalty is a real number greater than or equal to 1. Setting repetition penalty to 1 disables it.

When repetition penalty is enabled, the following algorithm is applied to each logit:<sup name="_repetition_penalty_multiplication">[[13]](#repetition_penalty_multiplication)</sup>

* If the token corresponding to the logit has not appeared in the story,<sup name="_repetition-penalty-input">[[14]](#repetition-penalty-input)</sup> we leave the logit as is.
* If the token corresponding to the logit has appeared in the story and the logit is greater than zero, the logit is divided by the repetition penalty value.
* If the token corresponding to the logit has appeared in the story and the logit is less than or equal to zero, the logit is multiplied by the repetition penalty value.

This basically makes it less likely for tokens that have already appeared in the story to appear again, favouring tokens that have not yet appeared.

Tokens that have appeared more than once in the story are *not* penalized more than tokens that have appeared only once.

We have found repetition penalty to be essential for creative story generation. However, when you enable repetition penalty, the good range of values varies with model size:

* 2.7B and smaller models often need repetition penalty in the 1.75&ndash;2 range to be usable.
* ~6B models need repetition penalty at 1.1&ndash;1.2.
* 13B models have a similar range, at 1.05&ndash;1.15.
* 20B models and larger need a repetition penalty value of at most around 1.03.

NovelAI users may be confused at the range of repetition penalty values used in KoboldAI. This is because NovelAI internally scales the repetition penalty value to provide a consistent range for all models. KoboldAI does not in order to allow users more control and to maintain consistency with other platforms.

Repetition penalty is normally applied before all of KoboldAI's samplers. This behaviour can be changed using the sampling order in 1.19 and beyond.

KoboldAI also inherited repetition penalty slope and repetition penalty range from Clover Edition. If *both* of these settings are not equal to 0, this makes it so that the repetition penalty value is different depending on where the token appeared in the story relative to the end of the story. Refer to [this Desmos widget](https://www.desmos.com/calculator/iui9ldyhwg), which shows a graph with the number of tokens relative to the end of the story (0 means the last token, 1 means the second-last token, etc.) on the x-axis and the repetition penalty on the y-axis. Tokens with a position further from the end of the story than the repetition penalty range are not considered. If a token appears more than once in the story, the token's effective repetition penalty value is calculated based on the last occurrence of that token (the occurrence closest to the end of the story).

## Notes and rambling

1. <a name="logit">[&#8593;](#_logit)</a> If you Google the word "logit", chances are you'll see something about a "logit function". Logits in the context of machine learning are numbers. The logit function is something a little different. Logits in machine learning get their name from the fact that the logit function is the inverse of the logistic function. So when we apply the softmax function (a generalization of the logistic function) to the logits, it's like we're reversing the logit function and recovering the original values.

2. <a name="logit-real">[&#8593;](#_logit-real)</a> We can also set logits to negative infinity even though negative infinity is not a real number. However, the raw logit values from the model are, in fact, always real. For the purposes of the softmax function's formula, we assume that ![](https://math.vercel.app/?color=gray&from=e^{-\infty}=0).

3. <a name="logit-consistency">[&#8593;](#_logit-consistency)</a> The actual range of logit values that can be output by a model depends on the model itself and is not consistent across models.

4. <a name="greedy-search-methods">[&#8593;](#_greedy-search-methods)</a> Or by setting top-k to 1, or by setting the tail free sampling value to 0.

5. <a name="softmax">[&#8593;](#_softmax)</a> For all positive integers ![](https://math.vercel.app/?color=gray&from=k) and for all vectors of logits ![](https://math.vercel.app/?color=gray&from=\vec{x}\in\mathbb{R}^k), the softmax function ![](https://math.vercel.app/?color=gray&from=\sigma:\mathbb{R}^k\to\left[0,1\right]^k) is defined as:

<p align="center"><img src="https://math.vercel.app/?color=gray&from=\sigma(\vec{x})_i=\frac{e^{\vec{x}_i}}{\sum_{j=1}^{k}e^{\vec{x}_j}}"></p>

6. <a name="temperature-name">[&#8593;](#_temperature-name)</a> The original name given by the authors is "temperature", which almost everyone uses except for AI Dungeon who calls the temperature setting "randomness" to help new users.

7. <a name="nucleus-sampling-name">[&#8593;](#_nucleus-sampling-name)</a> The original name given by the authors is "nucleus sampling" but many people just call it "top-p sampling", another name that the paper mentions occasionally, because of how common the sampling method is. Examples include Hugging Face transformers (the software library that KoboldAI uses to run transformer models on CPUs and GPUs) and Clover Edition and its derivative AvrilAI.

8. <a name="top-a-exponent">[&#8593;](#_top-a-exponent)</a> The original version of top-a actually has a second parameter that controls the exponent in the ![](https://math.vercel.app/?color=gray&from=ax^2) formula. However, we just leave it at 2 because it's perfectly fine and the author said that the a term is the more important one to tweak.

9. <a name="tail-free-sampling-differences">[&#8593;](#_tail-free-sampling-differences)</a> The author calls them "derivatives" although I have never heard this term being applied to discrete mathematics. It's usually "finite difference", "discrete difference" or some other term containing the word "difference". PyTorch and NumPy both have a function called `diff()` that does this.

10. <a name="tail-free-sampling-centering">[&#8593;](#_tail-free-sampling-centering)</a> The author fails to mention this step anywhere outside of the code. Although, if you think about it, you'd have to do something like this anyway since there are two fewer second differences than there are tokens.

11. <a name="typical-sampling-entropy">[&#8593;](#_typical-sampling-entropy)</a> For all nonnegative integers k and for all vectors of probabilities ![](https://math.vercel.app/?color=gray&from=\vec{x}\in\mathbb{R}^k), the entropy H is defined as:

<p align="center"><img src="https://math.vercel.app/?color=gray&from=H=-\sum_{p\in\vec{x}}p\ln%20p"></p>

12. <a name="typical-sampling-sorting">[&#8593;](#_typical-sampling-sorting)</a> Sort in ascending order of ![](https://math.vercel.app/?color=gray&from=\left|H%2B\ln%20p\right|) where p is the probability of the token.

13. <a name="repetition_penalty_multiplication">[&#8593;](#_repetition_penalty_multiplication)</a> The original algorithm from the paper divided logits for tokens that have appeared in the story by the repetition penalty value regardless of whether the logit is positive or negative. That would result in the negative logit tokens increasing in probability, which is counter to the point of repetition penalty, hence this modified algorithm that we and others use.

14. <a name="repetition-penalty-input">[&#8593;](#_repetition-penalty-input)</a> By "appeared in the story", we mean tokens that have appeared in the input to the model. So if KoboldAI is in the middle of generating 80 tokens and the model has generated 40 of them so far, those 40 tokens are included in the "story".