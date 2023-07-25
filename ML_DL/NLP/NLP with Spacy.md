# Introduction

spaCy is like the Sklearn of natural language processing. It is an industry standard with vast features to solve many NLP tasks with state-of-the-art speed, accuracy, and performance.

At its core are pipelines, which you can think of as language-specific models already trained on millions of text instances.

It is also at the head of the [spaCy ecosystem](https://spacy.io/universe) that includes dozens of libraries and tools such as Prodigy, Forte, displaCy, explacy, ADAM, Coreferee, etc.

spaCy can also shake hands with custom models from TensorFlow, PyTorch, and other frameworks.

Right now, spaCy supports 66 languages as separate pipelines, and new languages are being added slowly.

# Getting Started with spaCy

If you are new to spaCy, there are a couple of things you should be aware of:

-   spaCy’s Statistical Models
-   spaCy’s Processing Pipeline

# spaCy’s Statistical Models

These models are the power engines of spaCy. These models enable spaCy to perform several NLP related tasks, such as part-of-speech tagging, named entity recognition, and dependency parsing.

I’ve listed below the different statistical models in spaCy along with their specifications:

-   **en_core_web_sm:** English multi-task [CNN](https://www.analyticsvidhya.com/blog/2018/12/guide-convolutional-neural-network-cnn/?utm_source=blog&utm_medium=spacy-tutorial-learn-natural-language-processing) trained on OntoNotes. Size — 11 MB
-   **en_core_web_md:** English multi-task CNN trained on OntoNotes, with GloVe vectors trained on Common Crawl. Size — 91 MB
-   **en_core_web_lg:** English multi-task CNN trained on OntoNotes, with GloVe vectors trained on Common Crawl. Size — 789 MB

Importing these models is super easy. We can import a model by just executing _spacy.load(‘model_name’)_ as shown below:

import spacy   
nlp = spacy.load('en_core_web_sm')

# spaCy’s Processing Pipeline

The first step for a text string, when working with spaCy, is to pass it to an **NLP object**. This object is essentially a pipeline of several text pre-processing operations through which the input text string has to go through.

![](https://miro.medium.com/max/870/0*AifEqFz-2wSPoDIy.png)

_Source:_ [_https://course.spacy.io/chapter3_](https://course.spacy.io/chapter3)

As you can see in the figure above, the NLP pipeline has multiple components, such as _tokenizer_, _tagger_, _parser_, _ner_, etc. So, the input text string has to go through all these components before we can work on it.

Let me show you how we can create an _nlp_ object:

You can use the below code to figure out the active pipeline components:

nlp.pipe_names

**Output:** [‘tagger’, ‘parser’, ‘ner’]

Just in case you wish to disable the pipeline components and keep only the tokenizer up and running, then you can use the code below to disable the pipeline components:

```python
nlp.disable_pipes('tagger', 'parser')
```
Let’s again check the active pipeline component:

```python
nlp.pipe_names
```

**Output:** [‘ner’]

When you only have to tokenize the text, you can then disable the entire pipeline. The tokenization process becomes really fast. For example, you can disable multiple components of a pipeline by using the below line of code:

```python
nlp.disable_pipes('tagger', 'parser')
```

# Basics of spaCy

Before seeing how spaCy works, let's install it:

pip install -U spacy

spaCy has three pipelines for English, with varying sizes and functionality for complex tasks. In this tutorial, we will only need to install the small and medium pipelines, but I included the large one as well for completeness:

After importing spaCy, we need to load one of the pipelines we just installed. For now, we will load the small one and store it to `nlp`:

It is a convention to name any loaded language models `nlp` in the spaCy ecosystem. This object can now be called on any text to start information extraction:


```python
# Create the Doc object  
doc = nlp(txt)
```

The `doc` object is also a convention, and now it is already filled with extra information about the given text’s sentences and words.

In general, the `doc` object is just an iterator:

```python
for token in doc[:5]:
	print(token)

"""[OUT]
The
tallest
living
man
is"""
#You can use slicing or indexing notations to extract individual tokens:

type(token)
#spacy.tokens.token.Token
len(doc)
#31
```

> Tokenization is splitting sentences into words and punctuation. A single token can be a word, a punctuation or a noun chunk, etc.

If you extract more than one token, then you have a span object:

```python
span = doc[3:10]
type(span)
# spacy.tokens.span.Span
span.text
#'man is 37-year-old'
```

spaCy is also built for memory efficiency. That's why both `token` and `span` objects are just views of the `doc` object. There is no duplication.

The pre-trained English pipeline and many other pipelines have language-specific rules for tokenization and extracting their lexical attributes. Here are 6 of such attributes:

```python
print("Index: ", [token.i for token in doc[3:10]])
print("Text: ", [token.text for token in doc[3:10]])
print("is_alpha: ", [token.is_alpha for token in doc[3:10]])
print("is_punct: ", [token.is_punct for token in doc[3:10]])
print("like_num: ", [token.like_num for token in doc[3:10]])
print("Base word:", [token.lemma_ for token in doc[3:10]])

[OUT]:
Index: [3, 4, 5, 6, 7, 8, 9]
Text: ['man', 'is', '37', '-', 'year', '-', 'old']
is_alpha: [True, True, False, False, True, False, True]
is_punct: [False, False, False, True, False, True, False]
like_num: [False, False, True, False, False, False, False]
Base word: ['man', 'be', '37', '-', 'year', '-', 'old']
```

Some interesting attributes are `lemma_`, which returns the base word stripped from any suffixes, prefixes, tense, or any other grammatical attributes, and the `like_num` which recognizes both literal and lettered numbers.

You will be spending most of your time on these four objects — `nlp`, `doc`, `token` and `span`. Let's take a closer look at how they are related.
# Tokenization

Tokenizing is task of splitting sentence into meaningful segments called **tokens**. These segments could be words, punctuations, numbers or other special characters that are building blocks of sentence.

SpaCy’s default pipeline also preforms rule based matching. This annotates the text with more information and adds value during preprocessing.

**Preprocessing:**

With spaCy, stop words are easy to identify, each token has IS_STOP attribute, which lets us know if word is stopword or not.

We can add our on stopwords to list of stop words.

```python
stop_words = ['say', 'said', 'it', 'an', 'none', 'all', 'saying']  
for stopwords in stop_words:  
  lexeme = nlp.vocab[stopwords]  
  lexeme.is_stop = True
```

Stop words can also be added using :

```python
from spacy.lang.en.stop_words import STOP_WORDS  
print(STOP_WORDS) # SpaCy's default stop words  
STOP_WORDS.add("your_additional_stopwords_here")
```

If you have noticed _say, said, saying_ provide the same information - gramatical difference aside, it wont affect the results.

Stemming and lemmatization are popular techniques. **Stemming** involves removing suffix in general. But often it may result in meaningless words. For example removing suffix from **laziness** will result in **lazi**, it dosen’t rely on parts of speech. Where as **lemmatization** on the other hand helps convert word into **root word**.

In spacy, the lemmatized form of word is accessed with the .**_lemma__** attribute.

Lets check the sentence “_Real-time training during global emergencies is critical for effective preparedness and response._”:


```python
doc = nlp(‘Real-time training during global emergencies is critical for effective preparedness and response. ‘)
sentence = []
for w in doc:  # if it’s not a stop word or punctuation mark, add it to our     article!  
	if w.text != ’n’ and not w.is_stop and not w.is_punct and not   w.like_num:    # we add the lemmatized version of the word    
	sentence.append(w.lemma_)
print(sentence)
```

By using the .**is_stop , is_punct ,** and **w.like_num** attributes, we could remove the parts of the sentence we did not need.

Output would be:

['real', 'time', 'training', 'global', 'emergency', 'critical', 'effective', 'preparedness', 'response']

We can further remove or not remove words based in use-case.

# Vectorizing text and transformations and n-grams

We can think of **_vectors_** as a way of projecting words onto mathematical space while preserving the information provided by these words. In machine learning this feature is called **_feature vector_** as each value corresponds to some feature, which are used to make predictions.

Some concepts for these vector representation are…

**Bag-of-words(BOW)**

It is one of the straight forward form of representing a sentence as a vector. For example:

P1: “The dog sat near the door.”  
P2: ”The bird likes grains.”

Follow the same pre-processing steps mentioned above, the above sentences become:

P1: “dog sat near door.”P2: “birds like grains.”

Vocabulary vector would be unique words from the sentences.

vocab = [‘dog’, ‘sat’, ‘near’, ‘door’, ‘birds', 'like', 'grains']

We can think of mapping each word in vocabulary to a number.

**BOW** model use word frequencies to construct vectors. Now our sentence looks like..

P1: [1, 1, 1, 1, 0, 0, 0]  
P2: [0, 0, 0, 0, 1, 1, 1]

There is 1 occurrence of word _dog_ and 0 occurrence of word _birds, like and grains_ in first sentence and so on.

# TF-IDF

**_Term frequency_ and _inverse document frequency_** is largely used in search engines to find relevant document based on the query. Imagine you have a search engine and someone looks for _Ronoldo_. The results will be displayed in the order of relevance. The most relevant sports articles will be ranked higher because TF-IDF gives the word _Ronoldo_ a higher score.

TF(t) = (number of times term t appears in a document) / (total    number of terms in the document)

IDF(t) = log_e (total number of documents / number of documents with term t in it)

TF_IDF is simply the product of these 2 factors TF and IDF.

TF_IDF makes the rare words more prominent and ignore common words like is, or, an, that which may appear lot of time but may be less prominent.

**N-grams**

N-grams is the adjacent sequence of n-items in the text.

Bi-gram is one of the most popular n-gram. Removing stop words is necessary before running bigram model on your corpus or else there could be meaningless **bi-gram** formed.

For example: Machine Learning, Artificial Intelligence, New Delhi, Data Analytics, Big Data could be possible pairs of words created by bi-grams.

If you want to know more about n-grams refer the link([ngrams](https://en.wikipedia.org/wiki/N-gram)).
# Part-of-Speech (POS) Tagging

**In English grammar, the parts of speech tell us what is the function of a word and how it is used in a sentence.** Some of the common parts of speech in English are Noun, Pronoun, Adjective, Verb, Adverb, etc.

POS tagging is the task of automatically assigning POS tags to all the words of a sentence. It is helpful in various downstream tasks in NLP, such as feature engineering, language understanding, and information extraction.

Performing POS tagging, in spaCy, is a cakewalk:

**Output:**

He -> PRON  
went -> VERB  
to -> PART  
play -> VERB  
basketball -> NOUN

So, the model has correctly identified the POS tags for all the words in the sentence. In case you are not sure about any of these tags, then you can simply use _spacy.explain()_ to figure it out:

spacy.explain("PART")

**Output:** ‘particle’

# Dependency Parsing

Every sentence has a grammatical structure to it and with the help of dependency parsing, we can extract this structure. It can also be thought of as a directed graph, where nodes correspond to the words in the sentence and the edges between the nodes are the corresponding dependencies between the word.

![](https://miro.medium.com/max/375/0*nCEjt8KqqmuQ_lKP.png)

Dependency Tree

Performing dependency parsing is again pretty easy in spaCy. We will use the same sentence here that we used for POS tagging:

**Output:  
**He -> nsubj  
went -> ROOT  
to -> aux  
play -> advcl  
basketball -> dobj

The dependency tag ROOT denotes the main verb or action in the sentence. The other words are directly or indirectly connected to the ROOT word of the sentence. You can find out what other tags stand for by executing the code below:

spacy.explain("nsubj"), spacy.explain("ROOT"), spacy.explain("aux"), spacy.explain("advcl"), spacy.explain("dobj")

**Output:  
**(‘nominal subject’,  
None,  
‘auxiliary’,  
‘adverbial clause modifier’,  
‘direct object’)

# Named Entity Recognition

Let’s first understand what entities are. Entities are the words or groups of words that represent information about common things such as persons, locations, organizations, etc. These entities have proper names.

For example, consider the following sentence:

![](https://miro.medium.com/max/875/0*HIQqEva_HQz6ZuVS.png)

In this sentence, the entities are “Donald Trump”, “Google”, and “New York City”.

Let’s now see how spaCy recognizes named entities in a sentence.

**Output:**  
Indians NORP  
over $71 billion MONEY  
2018 DATE

spacy.explain("NORP")

**Output:** ‘Nationalities or religious or political groups’

# Rule-Based Matching

Rule-based matching is a new addition to spaCy’s arsenal. With this spaCy matcher, you can find words and phrases in the text using user-defined rules.

**It is like Regular Expressions on steroids.**

While Regular Expressions use text patterns to find words and phrases, the spaCy matcher not only uses the text patterns but lexical properties of the word, such as POS tags, dependency tags, lemma, etc.

Let’s see how it works:

So, in the code above:

-   First, we import the spaCy matcher
-   After that, we initialize the matcher object with the default spaCy vocabulary
-   Then, we pass the input in an NLP object as usual
-   In the next step, we define the rule/pattern for what we want to extract from the text.

Let’s say we want to extract the phrase “lemon water” from the text. So, our objective is that whenever “lemon” is followed by the word “water”, then the matcher should be able to find this pattern in the text. That’s exactly what we have done while defining the pattern in the code above. Finally, we add the defined rule to the matcher object.

Now let’s see what the matcher has found out:

matches = matcher(doc) matches

**Output:** [(7604275899133490726, 6, 8)]

The output has three elements. The first element, ‘7604275899133490726’, is the match ID. The second and third elements are the positions of the matched tokens.

**Output:** lemon water

So, the pattern is a list of token attributes. For example, ‘TEXT’ is a token attribute that means the exact text of the token. There are, in fact, many other useful token attributes in spaCy which can be used to define a variety of rules and patterns.

You can check out the other token attributes at [_https://spacy.io/usage/rule-based-matching_](https://spacy.io/usage/rule-based-matching)

Let’s see another use case of the spaCy matcher. Consider the two sentences below:

1.  You can read this book
2.  I will book my ticket

Now we are interested in finding whether a sentence contains the word “book” in it or not. It seems pretty straight forward right? But here is the catch — _we have to find the word “book” only if it has been used in the sentence as a noun._

In the first sentence above, “book” has been used as a noun and in the second sentence, it has been used as a verb. So, the spaCy matcher should be able to extract the pattern from the first sentence only. Let’s try it out:

matches = matcher(doc1)   
matches

**Output:** [(7604275899133490726, 3, 4)]

The matcher has found the pattern in the first sentence.

matches = matcher(doc2)   
matches

Nice! Though “book” is present in the second sentence, the matcher ignored it as it was not a noun.