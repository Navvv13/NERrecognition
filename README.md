# NERrecognition

# Named Entity Recognition
The main objective that we achieved with this was that given a text containing medicine names and medicine quantity, we created an
NER model, which can classify medicines and their respective quantities.




## Gathering data and Annotation

- The first thing I did was copy the names of the medications from the list in medicine.xls and type
  them into the chat.openai platform.
- For example for a medicine named Flucold Clear Syrup I wrote something like "write 3
  sentences on medicinal syrup named Flucold Clear Syrup"
  and for medicine like Floxi 200mg Tablet "generate sentence on the medicine Floxi 200mg
  Tablet" etc.


  ![mchatgpt](https://user-images.githubusercontent.com/65205930/210134518-5b92aafe-8582-46fd-88e4-e7e9f563fbf5.png)
- And the next step was to transform the sentences and get the annotated corpus.
- I did these for n-number of medicines and then side by side kept on storing the result in an
  array. The representation of which is in the image below.


![annotation](https://user-images.githubusercontent.com/65205930/210134578-44fbbb2b-8207-4328-8981-906b865bf760.png)
 
## Architecture

- The Language class, Vocabulary, and Doc object are the three main data structures of
  spaCy. Text is processed to create a Doc object using the Language class.

- Usually, it is kept as a variable with the name nlp. The token sequence and each of its
  annotations belong to the Doc object.

- We avoid keeping duplicates of this data by centralizing strings, word vectors, and lexical
  properties in the Vocab. This preserves memory and guarantees that there is only one
  true source.

- The “Doc object”, which owns the data, is another feature of text annotations that allows
  for a single source of truth. The pipeline's elements first modify the Doc object after it
  has been built by the Tokenizer.

- These elements are coordinated by the “Language object”. It starts with raw text and
  runs it through the pipeline to produce a document with annotations. Additionally, it
  coordinates serialisation and training.

- A pipeline component or components are called on the Doc one at a time as part of the
  processing pipeline. Before the components, the tokenizer is executed. Language.add_pipe is a
  method for adding pipeline parts. 

- In addition to making rule-based changes to the Doc, they can
  also include a statistical model and training weights. For various language processing tasks,
  spaCy comes with a variety of built-in components, and it also lets you create your own.
## Accuracy Parameters
The scores supplied by the various pipeline components are contained in the Dict that was returned. The
Token or Doc characteristic being scored comes first in the individual score names for the scoring
methods offered by the Scorer and utilised by the main pipeline components.
For example:
- token_acc: number of correct tokens / number of gold tokens
- token_p, token_r, token_f: precision, recall and F-score for token character spans
- Docs with has_unknown_spaces are skipped during scoring
- morph_acc, morph_micro_p, morph_micro_r, morph_micro_f, morph_per_feat
- cats_score (depends on config, description provided in cats_score_desc), cats_micro_p,
  cats_micro_r, cats_micro_f, cats_macro_p and so on.


## Result
Prototype of the problem statement or the expected output :

![expected](https://user-images.githubusercontent.com/65205930/210134706-13135ac7-e18d-4ca8-b0b5-22685a41608e.png)


This was th final result that we got where we can see that the medicine name and quantity are distinguished and displayed.

![result](https://user-images.githubusercontent.com/65205930/210134654-9f5cfd70-d24c-4673-9c64-5405d5443593.jpeg)
