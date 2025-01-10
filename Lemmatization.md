# Lemmatization Interview Questions
---

## 1. What is Lemmatization? How does it differ from Stemming?
- **Lemmatization** is the process of reducing a word to its base or dictionary form (lemma) while considering its context and meaning. 
- **Stemming** trims words to their root form (often ignoring grammar and context), lemmatization uses linguistic knowledge to provide valid words.
- **Example:**
  - Lemmatization: "running" → "run"
  - Stemming: "running" → "runn"

## 2. Why is Lemmatization important in NLP?
Lemmatization helps normalize text, making it easier to analyze. By converting words to their base forms, 
it reduces dimensionality in text data and ensures context-aware preprocessing, improving model performance in NLP tasks.

## 3. What are the common libraries or tools used for Lemmatization?
- **NLTK:** `WordNetLemmatizer`
- **spaCy:** Built-in `lemmatizer` with POS tagging
- **TextBlob:** Provides lemmatization functionality
- **Stanford NLP:** Advanced lemmatization support.

## 4. What is a Lemma in the context of NLP?
A lemma is the base or dictionary of a word.
For example, the lemma of "running" is "run" and the lemma of "better" is "good".

## 5. What role does Lemmatization play in text preprocessing pipelines?
Lemmatization helps by:
- Reducing redundancy in the text.
- Improving consistency.
- Making it easier to group related terms.
- Enhancing performance in text classification, topic modeling, and search systems.

## 6. How does Lemmatization handle different parts of speech (POS)?
- Lemmatization requires the POS tag to identify whether a word is a noun, verb, adjective, etc.
This ensures the correct lemma is returned.
- **Example:**
  - Noun: "better" → "good"
  - Verb: "better" → "better"

## 7. How would you implement Lemmatization in Python using NLTK or spaCy?
- **Using NLTK:**
```python
from nltk.stem import WordNetLemmatizer
from nltk.corpus import wordnet

lemmatizer = WordNetLemmatizer()
print(lemmatizer.lemmatize("running", pos="v"))  # Output: run
```
- **Using spaCy:**
```python
import spacy
nlp = spacy.load("en_core_web_sm")
doc = nlp("running")
print([token.lemma_ for token in doc])  # Output: ['run']
```
