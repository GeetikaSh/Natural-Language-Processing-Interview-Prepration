# Gensim: Interview Questions

---

## 1. What is Gensim, what is it used for?
Gensim is an open source Python library used for topic modeling, document indxing, and similarity retrieval.
It provides efficient implementation of popular algorithm like Dirichlet Allocation(LDA), Latent Semantic Indeing(LSI),
and word embeddings such as Word2Vec, FastText, and Doc2Vec.

## 2. What are the core components of Gensim?
- **Corpus:** A collection of documenys represented in a spese format (bag-f-words or TF-IDF).
- **Dictionary:** A mapping of unique words in the corpus to integer IDs.
- **Models:** Algorithms like LDA, LSI, Word2Vec, FastText, and Doc2Vec used for topic modeling,
  word embeddings, and similarity tasks.
- **Similarity:** Method to compute similaritities between documents or vectors.

## 3. How does Gensim handle large datasets?
Gensim is designed for scalability and memory efficiency. It:
- Processed data in a streaming manner using iterators (no need to load dataset into memory).
- Uses sparse matrix representation to save memory.
- Implements distributed computing for tasks like training Word2Vec on large corpora.

## 4. How can you preprocess text data for Gensim models?
Text preprocessing typicall includes:
1. **Tokenization:** Splitting texts into words.
2. **Lowercasing:** Converting all text to lowercase for uniformity.
3. **Removing Stopwords:** Removing common words like "the", "and", "etc"., that don't add meaning.
4. **Stemming/ Lemmatization:** Reducing words to their root form.
```
Stemming: Reduces words to their root form without considering the meaning (e.g., 'better' → 'better').
Lemmatization: Converts words to their base form based on their meaning (e.g., 'better' → 'good')
```
5. **Creating a Dictionary:** Using `gensim.corpora.Dictionary` to map to unique IDs.
```python
from gensim.utils import simple_preprocess
from gensim.corpora.dictionary import Dictionary

texts = ["This is a sample document.", "Text preprocessing is crucial for NLP."]
preprocessed_texts = [simple_preprocess(doc) for doc in texts]
dictionary = Dictionary(preprocessed_texts)
```

## 5. How does the Word2Vec Model in Gensim work?
Word2Vec in Gensim learns vector representations of words using two architectures:
- **Skip-gram:** Predicts the surrounding words(cintext) given a target word.
- **CBOW (Continuous Bag of Words):** Predicts a target word on its surrounding context.
```python
from gensim.models import Word2Vec

sentences = [["this", "is", "a", "sentence"], ["another", "sentence"]]
model = Word2Vec(sentences, vector_size=100, window=5, min_count=1, workers=4)
vector = model.wv["sentence"]  # Get the word vector for "sentence"
```

## 6. How is Latent Dirichlet Allocation (LDA) implemnted in Gensim?
Gensim's LDA implementation models a corpus as mixture of topics, where each topic is distribution over words.
You can train an LDA model using the `LdaModel` class.
```python
from gensim.models import LdaModel
from gensim.corpora.dictionary import Dictionary

texts = [["data", "science", "machine", "learning"], ["deep", "learning", "neural", "networks"]]
dictionary = Dictionary(texts)
corpus = [dictionary.doc2bow(text) for text in texts]

lda_model = LdaModel(corpus=corpus, num_topics=2, id2word=dictionary, passes=10)
topics = lda_model.print_topics()
```

## 7. How can you calculate document similarity using Gensim?
You can calculate document similarity by:
1. Converting documents to a vectorized format using bag-of-words, TF-IDF, or Word2Vec embeddings.
2. Using Gensim's `Similarities` class to compute similarity scores.
```python
from gensim.similarities import MatrixSimilarity
from gensim.models import TfidfModel

# Preprocessing
texts = [["data", "science"], ["machine", "learning", "science"]]
dictionary = Dictionary(texts)
corpus = [dictionary.doc2bow(text) for text in texts]

# TF-IDF model
tfidf = TfidfModel(corpus)
tfidf_corpus = tfidf[corpus]

# Similarity
similarity_index = MatrixSimilarity(tfidf_corpus)
similarities = similarity_index[tfidf_corpus[0]]
```

## 8. What are the advantages of using Gensim over other NLP libraries?
- Scalability for large datasets.
- Efficient implementations of algorithms like LDA, LSI, and Word2Vec.
- Stemming data processing to save memory.
- Compatibility with other libraries like NLTK, spaCy, and scikit-learn.

## 9. What is the difference between Word2Vec and Doc2Vec in Gensim?
- **Word2Vec:** Creates vector representations of individual words.
- **Doc2Vec:** Extends Word2Vec to represents entire documents or paragraph as vectors by adding a unique document ID.
```python
from gensim.models.doc2vec import Doc2Vec, TaggedDocument

documents = [TaggedDocument(words=["data", "science"], tags=["doc1"]),
             TaggedDocument(words=["machine", "learning"], tags=["doc2"])]
model = Doc2Vec(documents, vector_size=100, window=5, min_count=1, workers=4)
doc_vector = model.dv["doc1"]  # Get vector for "doc1"
```

## 10. What is the role of `passes` and `iterations` in Gensim models?
- **Passes:** The number of times the algorithm processes the entire corpus.
- **Iterations:** The number of times the algorithm iterates over each document during a single pass.

  Higher values can improve accuracy but increase computational time.


