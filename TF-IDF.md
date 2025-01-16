# TD-IDF : Interview Prepration
---

## 1. What is TF-IDF
TF-IDF is a statistical method used in natural language programming(NLP) to evaluate the importance
of a word in a document relative to a collection of documents(corpus). It combines the Term Frequency (TF)
and Inverse Document Frequenct (IDF).

## 2. What is the Term Frequency (TF)?
TF measures how often a term appeard in document. It is calculated as
$$TF = \frac{\text{Number of times term } t \text{ appears in a document}}{\text{Total number of terms in the document}}$$

## 3. What is Inverse Document Frequency (IDF)?
Inverse Document Frequency (IDF) is calculated to give more weight to terms that rarely occur in a document,
as these terms might hold valuable information. In contrast, terms that occur frequently across many documents are given less weight.
It is worth noting that the logarithm of this value is calculated, This is done to scale down the final value of IDF, as logarithms help to dampen large values.
For example, log(1000)=3. 

$$IDF = \log\left(\frac{\text{Total Number of Documents in the Corpus}}{\text{Number of Documents Containing the Term}} + 1\right)$$

`+1` is added to prevent division by 0

## 4. How is TF-IDF calculated?
$$TF-IDF(t,d) = TF(t,d)*IDF(t)$$

## 5. Why do we use TF-IDF in text processing?
TF- IDF helps in identifing the most important words in a document by redcing the weights in a document,
by reducing the weight of common occuring words (example, "the", "is") and emphasizing less frequent,
and more inforative terms.

## 6. What are the limitations of TF-IDF?
- High Dimtionalility, that leads to the sparse matrix especialy for the large set of documents.
- Does not capture semantics or context of words.
- Sensitive to outliers and noise in the data.
- Favors rare terms excessively, which may not always be meaningful.
- Requires pre-processing(example, stemming, stop-words removal).

## 7. What are common use cases of TF-IDF?
- Text Summarization.
- Keyword extraction.
- Document Similarity Measurement
- Feature Extraction for Machine Learning models.
- Search engine ranking.

## 8. How TF-IDF handle stop words?
Stop words like "the", "and", etc., tend to have low IDF values because they appear in most documents,
reducing their overall TF-IDF scor.

## 9. What preprocess steps are necessary before applying TF-IDF?
- Lowercasing
- Tokenization
- Stop-words removal
- Stemming or Lemmatization
- Removing punction and special characters.

## 10. Can you give example where TF-IDF might fail?
TF-IDF may fail to identify the importcance of words with semantic similarity. For example,
it treats "car" and "automobile" as completely different, even though they are synonyms.

## 11. What are alternatives to tf-idf?
- Word embeddings (e.g., Word2Vec, GloVe).
- Frequency-based methods (e.g., Bag of Words).
- Pre-trained models (e.g., BERT, GPT).

## 12. What is the impact of the IDF smoothing constant (+1) in the formula?
Adding 1 ensures that the denominator in the IDF calcilation never becomes zero,
preventing undefined values forb terms not appearing in any document.

## 13. How is TF-IDF implement in Python
```python
from sklearn.feature_extraction.text import TfidfVectorizer
documents = ["example document one", "example document two"]
vectorizer = TfidfVectorizer()
tfidf_matrix = vectorizer.fit_transform(documents)
print(tfidf_matrix.toarray())
```

## 14. How does TF-IDS handle large corpora efficiently?
Libraries like scikit-learn use sparse matrix representations to handle the large number of terms and documents efficiently.

## 15. Explain the difference between TF-IDF and Bag of Words (BoW).
- **BoW:** Represents the freuency of terms without considering importance or relevance.
- **TF-IDF:** Adjusts term frequency by factorising in the term's importance across the corpus.

## 16. How can TF-IDF be used for document similarity?
Compute the TF-IDF vectors for all documents, then calculate cosine similarity between vectors to measure similarity.

## 17. How would you handle a term that appears in every document using TF-IDF?
Such terms will have IDF of near zero, resulting in a very low TF-IDF score.
This behavior appropriately reduces their weight in the analysis.

## 18. How can TF-IDF improve search engine ranking?
TF-IDF priortise documents where query terms are more relevant by calculating higher weights for documents containing important terms.

## 19. What challenges arise when using TF-IDF on a multilingual corpus?
- Handling multiple languages during preprocessing.
- Stop-word removal and stemming for different languages.
- Need to seperate a combined IDF calculations depending on the use case.

## 20. How would you explain TF-IDF to non-technical audience?
TF-IDF is like a ranking system that highlights important to a document but less common in others.
It helps identify what makes a document unique in a group of documents.



