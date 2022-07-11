In order for a transformer model to understand your story, it first has to convert it to a format that its hidden layers understand.

After your story is converted into tokens and sent to the model, the tokens are converted to another internal format for the model's use via a process known as "embedding". The end product is a two-dimensional array of "[word embeddings](https://en.wikipedia.org/wiki/Word_embedding)", often just called "embeddings".

Every transformer model comes with an embedding matrix, which is a two-dimensional array. There is one row in this two-dimensional array for every possible token in the model's token vocabulary. Embedding just involves taking the rows from this two-dimensional array that correspond to the tokens in your story and concatenating them together. The result is the embeddings that get sent to the rest of the model.

Consider this toy example, wherein your story, " a long time ago in a galaxy far far away..." is tokenized and embedded.

1. Your story gets converted into tokens. For example, maybe the tokens are [1, 4, 2, 3, 5, 1, 6, 8, 8, 0, 7] for [" a", " long", " time", " ago", " in", " a", " galaxy", " far", " far", " away", "..."].
2. We locate the rows in the model's embedding matrix that correspond to the token IDs, where row 0 is the first row, row 1 is the second row and so on.
3. We concatenate the rows that correspond to the tokens together in the same order that they were in the story. Then this gets sent to the rest of the model.

![](https://user-images.githubusercontent.com/89268918/178172074-9a16e323-6455-46ab-a763-73ead4d0b717.png)

Soft prompts, also known as "modules", are two-dimensional arrays that can be concatenated at the beginning of the embeddings directly after the embedding step (row-wise, so we are adding extra rows to the top of the embeddings, not extra columns to the left of the embeddings). This allows us to inject extra information to the model. The idea of soft prompts was introduced by the paper *[The Power of Scale for Parameter-Efficient Prompt Tuning](https://arxiv.org/pdf/2104.08691v2.pdf)*.

What makes this different from memory? Unlike memory, where the stuff we add at the beginning of your story (and thus at the beginning of the embeddings) consists of tokens that the model has seen before, the stuff a soft prompt adds to the beginning of the embeddings need not actually be from the model's embedding matrix&mdash;it can be anything we want!

Whereas normal memory only allows us to add rows to the embeddings that are from the model's embedding matrix, a soft prompt can add completely novel, never-before-seen rows. The embedding matrix usually has at least 1000 columns, so by using a soft prompt we get higher information density than with normal memory. You can put an entire dataset's worth of information in a few dozen tokens' worth of memory.

However, like when you write your memory, the model itself actually has to be familiar with the particular genre/style of text. If the model has not been trained on stories containing supernatural elements at all, a Lovecraftian fanfiction soft prompt is unlikely to work very well.

To use a soft prompt in KoboldAI, download it first. It will be a zip file. *Without* extracting it first, put it into the "softprompts" folder in your KoboldAI folder if you are running KoboldAI locally, or in the "KoboldAI/softprompts" folder in your Google Drive account if you are using Colab. Then, load KoboldAI. If the soft prompt is compatible with your model, you will be able to see it in the Soft Prompts menu in the KoboldAI interface.

Soft prompts, when used in KoboldAI, reduce the maximum context size of the model by a few tokens. The amount of tokens it decreases by is equal to the number of rows in the soft prompt two-dimensional array. This number can be seen for each soft prompt in the soft prompt selection menu.

A soft prompt will work on a model other than the specific model it was made for if the two models have the same base type (e.g. GPT-NeoX, GPT-J, fairseq dense, OPT) *and* the same number of parameters (e.g. 6B, 13B, 20B). This is caused by these two main prerequisites:

* The soft prompt and the embedding matrix of your model must have the same number of columns for the concatenation operation to be defined. Typically, models with different numbers of parameters don't have the same number of columns in their embedding matrices. In a model from huggingface.co, the number of columns in the embedding matrix can be found in the config.json, usually called something along the lines of "hidden_size", "d_model", "model_dim" or "n_embed".
* The embedding matrices of the two models must be sufficiently similar so that the embeddings from one model can be understood by the other. We have repeatedly experimentally verified that all finetunes of a particular model, including the base model itself, have sufficiently similar embeddings for this to occur.

Rarely, a soft prompt may work somewhat on a model of the same size but different base type. Currently the only documented occurrence of this happening is of soft prompts made for fairseq dense models working for OPT models of the same size.

If you open up one of KoboldAI's soft prompt zip files, you will see a file called tensor.npy inside. This is the two-dimensional array (in NumPy array format) that we concatenate at the beginning of the embeddings, if you are curious.

*TODO: Add information on how to train a soft prompt and on dataset making.*
