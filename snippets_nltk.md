# stopwords
from nltk.corpus import stopwords
stop = stopwards.words('english')
filter(lambda x: x not in words)

## process
1. remove punctuation
2. tokenize
3. remove stopwords
4. lemmatize / stem

# tokenize
from nltk.tokenize import word_tokenize
tokens = word_tokenize(text)

# stemming
from nltk. ... import PorterStemmer
ps = nltk.PorterStemmer()
ps.stem('word')

# lemmatize 


# count vectorization
from sklearn.feature_extraction.text import CountVectorize

cvect = CountVectorize(analyzer=[cleaning_function])
counts = cvect.fit_transform(text)

## n-grams
CountVectorize(ngram_range=(low, high))

## tfidf