---
title: "Term Frequency-Inverse Document Frequency-TF-IDF"

categories: ['']

tags: ['Term', 'Frequency', 'Inverse', 'Document', 'Frequency', 'TF', 'IDF']

arabic: ['تردد الكلمة-تردد المستند العكسي']

publishers: ['معجم مصطلحات التعلم الآلي والتعلم العميق وعلم البيانات']

types: "word"

slug: ""
---


'''python

import pandas as pd
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.preprocessing import normalize
import nltk
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
from nltk.stem.isri import ISRIStemmer
import re

# Download required NLTK resources
nltk.download('punkt')
nltk.download('stopwords')

# Sample Arabic documents
documents = [
    "أنا أحب البرمجة",
    "البرمجة ممتعة وتساعد على التفكير",
    "تعلم البرمجة مهم في عصر التكنولوجيا",
    "البرمجة تساعد في حل المشكلات"
]

# Preprocessing function for Arabic text
def preprocess(text):
    # Remove diacritics
    text = re.sub(r'[\u064B-\u0652]', '', text)
    # Tokenization
    words = word_tokenize(text)
    # Remove stop words
    stop_words = set(stopwords.words('arabic'))
    words = [word for word in words if word not in stop_words]
    # Stemming
    stemmer = ISRIStemmer()
    words = [stemmer.stem(word) for word in words]
    return ' '.join(words)

# Preprocess the documents
preprocessed_docs = [preprocess(doc) for doc in documents]

# Create TF-IDF Vectorizer
vectorizer = TfidfVectorizer()
tfidf_matrix = vectorizer.fit_transform(preprocessed_docs)

# Normalize the TF-IDF matrix
tfidf_matrix = normalize(tfidf_matrix, norm='l2')

# Convert the matrix to a DataFrame for better readability
df = pd.DataFrame(tfidf_matrix.toarray(), columns=vectorizer.get_feature_names_out())

print(df)

'''