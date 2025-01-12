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

## 8. Can Lemmatization be used in sentiment analysis? Why or why not?
Yes, it can be used to normalize text and reduce variations, helping in consistent feature extraction. However, excessive lemmatization may lose nuances (e.g., "happy" v/s. "happier"), whicg are critical for sentiment analaysis.

## 9. What challenges might arise when applying Lemmatization to multi-lingual datasets?
- Lack of comprehensive morphological dictionarries for all languages.
- Variations in grammer rules and structures.
- Handling code-mixed (examaple, Hinglish) or transliterated text.

## 10. How does Lemmatization impact computational efficiency compared to Stemming?
Lemmatizaarion is computationally expensive as it requires morphological analysis of POS Tagging, whereas stemming is faster but less accurate.
`Morphological analysis is a method for exploring solutions to complex problems, and can be used in a variety of fields including linguistics, biology, and general problem solving`

## 11. What are the limitations of Lemmatization in handling domain-specific language?
Lemmatizers rely on general purpose dictionaries and may fail with domain specific terms or jargon. Custoizing lemmatizers with domain specific lexicons can address this limitation.

## 12. Explain how a lemmatizer words under the hood?
- Analzes the word structure and identifies the lemma using a morpgological dictionary.
- Leverages POS tagging to choose the appropriate base form.
- Example: For "better", it identifies POS as an adjective and maps it to "good".

## 13. How does Lemmatization affect downstream NLP tasks like topic modeling?
Lemmatization helps reduce word variants, ensuring cleaner and more consistent input for topic modelling algorithms, leading to better topic coherence.

## 14. What is teh impac of Lemmatization on word embedding( example, Word2Vec)?
Lemmatization reduces redundancy in vocabulary, allowing embeddings to focus on sementically signinficant terms. However, it may oversiplify embeddings by removing morphological neuances.

## 15. How would you evaluate the effectiveness of a lemmatization process in an NLP pipeline?
- Compare results with and without Lemmatization in downstream tasks (e.g., classiication accuracy, topic coherence)
- Qualitative inspection of processed text to consistency and relevance.

## 16. Would you use Lemmatization or Stemming for a legal document search engine?
**Lemmatization**, as it ensures context-aware normalization, preserving the legal meaning and validity of terms.

## 17. How would you preprocess tweets using Lemmatization?
- Normalize hastags (#hAPPY --> happy)
- Handle slang or abbriviations (e.g., "gonna" --> "going to"
- Use lemmatization to reduce word variations.

## 18. Why might performance decrease ater Lemmatization in text classification?
Excessive kemmatization may remove meaningful morphological features, reducing the richness of the text.

## 19. How to design a custom lemmatizer for a domain (e.g., medical text)?
- Build a domain-specific morphological dictionary.
- Integrate domain- aware POS tagging rules.
- Test o domain - relevant corpora.
- 
`Corpora is a collection of texts or text samples that are used to study a language. The word "corpora" is the plural of "corpus".
part-of-speech tagging (POS tagging or PoS tagging or POST), also called grammatical tagging is the process of marking up a word in a text (corpus) as corresponding to a particular part of speech, based on both its definition and its context.`

## 20. How to use Lemmatization with NER?
Apply Lemmatization only to non-entity tokens to avoid losing entity-specific nuances critical for accurate recognition.

