## Top P Sampling and Top K Sampling

Top-p takes what the AI considers the top percentile of most likely responses based on a user provided number - if I say top-p=0.4 it'll take all the top ones it can until they add up to 40%. This is also known as nucleus sampling.

Top-k takes the exact user defined number of what the AI sees as the most likely responses counting from top down. For instance let's say I set top-k=2 and behind the scenes the AI evaluates the most likely words next: hat=35%, chair=22%, rug=15%, and so on.
Top-k is only taking hat and chair since they're the top two as my top-k=2. So why have a narrowed pool of words for consideration and not just use the top word every time? Well using a most predictable response all the time rapidly slips the AI, any AI, into repeating whatever satisfies its function endlessly. That's why there are a whole three parameters on repetition penalty with KoboldAI's system. Natural language doesn't involve repeating the exact same phrase over and over unless all work and no play makes jack a dull boy.

top-p and top-k basic explainer:
https://docs.cohere.ai/token-picking/

Here's problem - earlier I stated being repetitive is a common issue. Well increasing repetition penalty just barely beyond a certain level (that spot is different per AI model) can cause obscene randomness. Reeling it back just enough from that point may ensure things stay coherent yet ever changing and fresh. Regardless, top-p and top-k rely too heavily on the top most likely responses despite their different approaches and researchers have been working on ways to increase creativity with coherence instead of making them a dichotomy.

So now we have new stuff like typical sampling, tail-free sampling, and top-a sampling. These are a pain in the ass to understand so I work with them based on a mix of my intuition and the gist of what I think they do from what I've read. The below is my best understanding.

## Tail-Free Sampling

Tail-free seems to increase the quality of the lower likely responses making more randomness (which can be introduced by raising temp, rep penalty, or both) not so bad since the bottom of the barrel isn't a cesspool of incoherence. Could be worth cranking this to a high value and raising temp a bunch. Strange note the KoboldAI interface tooltip highly recommends disabling top-k and top-p when this is in use. Maybe the nature of how they work is entirely incompatible, but I have had success leaving everything on but in moderate levels.

tail-free explainer:
https://www.trentonbricken.com/Tail-Free-Sampling/

## Typical Sampling

Typical sampling appears to be a shot at next gen latent space sampling for AI response. I read the papers on it and remember next to nothing of how it works other than it's supposed to be very good at narrowing down the most likely human responses without having problems with being repetitive. Literally this is the explanation from the researchers themselves "Rather than always choosing words from the high-probability region of the distribution--which have a low Shannon information content--we sample from the set of words with information content close to the conditional entropy of our model, i.e., close to the expected information content." What the fuck does any of that mean. Just say it's magic. Here's the paper on it if you're super smart or hate yourself and desire a headache.

typical sampling explainer:
https://arxiv.org/abs/2202.00666

## Top A Sampling

And the last one top-a. I can't find a single article on it. The KoboldAI interface's tooltip says:
"Alternative sampling method that reduces the randomness of the AI whenever the probability of one token is much higher than all the others. Higher values have a stronger effect. Set this setting to 0 to disable its effect." best guess is if a word is just a small percent above the others in a pool of word candidates, top-a ensure that word is next to post in a generated sentence.. (maybe even bypassing repetition penalty to do so? Who knows there's no further documentation lol go go gadget guesswork). The higher top-a is set, the more likely it will grab the highest rated word from the pool of remaining candidates regardless of being the highest by a narrow margin (this is my guess since it has a non binary value, so I suppose the higher the top-a the more sensitive it is to small margin word superiority).

## Samplers Order

Now that I barely understand samplers outside top-k and top-p there's a new feature where I can fidget with their order. 🫠
Further confusing is my impression has ways been that 'temp' is a basal setting that some samplers directly reference and build off of. But I can change the order of that one too which either means I'm free to break stuff or my impression was wrong.
Plus side is I can cheat in so many ways by having control over sampler order - if I wanted to, set temp high in the range of 0.8-1.2, use typical sampling to do it's magic, then cut to the top 70 results from that using top-k, then remove the shit results at the bottom probability of those 70 with tail-free sampling, further reducing my word pool somewhat, and set a low top-a which would only grab the top candidate in that pool if it has a relatively higher score compared to its siblings.

Or what I do now is _temp0.8>typical0.19>tfs0.97>top-p0.6_ which works wonders for me across the board on Fairseq13B, even Opt. The top-p being optional, top-k and top-a off for now. All repetition penalties left at default.

Ordering the sampler stack changes everything. The order can make an enormous impact in output coherence.