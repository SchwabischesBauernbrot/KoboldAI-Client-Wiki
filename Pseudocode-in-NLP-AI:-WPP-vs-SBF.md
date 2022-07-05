## Quick Explainer
There are two different pseudocode techniques that have been found as best practice for storing dense information in memory such as relational status between characters, how the world operates, and any other information desired to be consistent/persistent. These are two formats, one dubbed W++ which works best with language models that have an understanding of following explicit instructions and basic code, and SBF or Square Bracket Format which works best with language models more focused only on natural language.

The only notable differences between W++ and SBF aside from which models they influence are their basic formatting, and W++ appears to have far more explicit control beyond storing information but can also serve as a means to push instructions.

## W++
Language models influenced by W++ are EleutherAI's GPT-J, GPT-Neo, and Meta's Opt (Open Pre-trained Transformers) series models.

Example: 
While using Opt13B, Despite explcitly stating my character Edward was 37, married to Charlotte, and had two children - Benny and Clara, sometimes the AI would become confused and assume I was a child and Edward was another person. This was easily fixed entirely by placing the following W++ in memory:

[I am("Edward")<br>
{<br>
Husband of("Charlotte")<br>
Father of("Clara" + "Benny")<br>
Gender("Male")<br>
Age("37")<br>
}]

## SBF (Square Bracket Format)
Language models influenced by SBF are Meta's XGLM and Fairseq-dense series models.

Example:
Let's say I'm using a Fairseq model and having the same issue as the W++ example above; I'd clearly stated who I was in relation to the family in my story - I'm a 37 year old husband named Edward but the model keeps assuming Edward is someone else and I'm a child. That can easily be fixed by acting the following SBF pseudocode in memory below:

[ I am: "Edward"; Husband of: "Charlotte"; Father of: "Clara", "Benny"; Gender: "Male"; Age: "37" ]

## W++ and SBF Editor Link
https://nolialsea.github.io/Wpp/
