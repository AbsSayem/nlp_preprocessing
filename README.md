# nlp_preprocessing
Explore all the ways of preprocessing techniques for Natural Language Processing(nlp). Largely, preprossing includes - tokenization, stemming, lemmatization, parts-of-speech tagging(pos-tag), name entity recognition(ner), punctuation and stopwords removing, regular expression(re) etc.
## Tokenization
#### Using Python "split()" function
Python split() method by default split the text by words.
```
# Spliting by words
text = """This is text for testing preprocessing steps for nlp. For nlp, preprocessing steps are very much important. Preprocessing steps improve the accuracy in percentage(%). If you don't follow preprocessing steps, you can't get the desired result. Preprocessing steps varies from purpose to purpose."""
print(text.split())     # This will by default split the text by words
```
```
  ['This', 'is', 'text', 'for', 'testing', 'preprocessing', 'steps', 'for', 'nlp.', 'For', 'nlp,', 'preprocessing', 'steps', 'are', 'very', 'much', 'important.', 'Preprocessing', 'steps', 'improve', 'the', 'accuracy', 'in', 'percentage(%).', 'If', 'you', "don't", 'follow', 'preprocessing', 'steps,', 'you', "can't", 'get', 'the', 'desired', 'result.', 'Preprocessing', 'steps', 'varies', 'from', 'purpose', 'to', 'purpose.']
```
For splitting text into sentences, we can use python split() method providing a separator (. / ? / !).
```
# Spliting by words
text = """This is text for testing preprocessing steps for nlp. For nlp, preprocessing steps are very much important. Preprocessing steps improve the accuracy in percentage(%). If you don't follow preprocessing steps, you can't get the desired result. Preprocessing steps varies from purpose to purpose."""
text.split('.')     # This will  split the text by dots(.)
```
```
  ['This is text for testing preprocessing steps for nlp',
   ' For nlp, preprocessing steps are very much important',
   ' Preprocessing steps improve the accuracy in percentage(%)',
   " If you don't follow preprocessing steps, you can't get the desired result",
   ' Preprocessing steps varies from purpose to purpose',
   '']
```
#### Using Regular Expression
Regular Expression (re) is a special character sequence that helps to find strings or sets of strings using these sequences.
```
# Importing regular expression
import re
```
re.findall() function finds all the words and stores in a list.
> [\w]+ find all alphanumeric character(letters, numbers) and underscore(_) until any other character in encountered.
```
# Word Tokenization
text = """This is text for testing preprocessing steps for nlp. For nlp, preprocessing steps are very much important. Preprocessing steps improve the accuracy in percentage(%). If you don't follow preprocessing steps, you can't get the desired result. Preprocessing steps varies from purpose to purpose."""
tokens = re.findall("[\w']+", text)
print(tokens)
```
```
  ['This', 'is', 'text', 'for', 'testing', 'preprocessing', 'steps', 'for', 'nlp', 'For', 'nlp', 'preprocessing', 'steps', 'are', 'very', 'much', 'important', 'Preprocessing', 'steps', 'improve', 'the', 'accuracy', 'in', 'percentage', 'If', 'you', "don't", 'follow', 'preprocessing', 'steps', 'you', "can't", 'get', 'the', 'desired', 'result', 'Preprocessing', 'steps', 'varies', 'from', 'purpose', 'to', 'purpose']
```
re.compile() split sentences as soon as any of the separator are found.
```
# Sentence Tokenization
# To perform sentence tokenization we can use "re.split()" method. We can pass multiple separators in it.
text = """This is text for testing preprocessing steps for nlp. For nlp, preprocessing steps are very much important. Preprocessing steps improve the accuracy in percentage(%). If you don't follow preprocessing steps, you can't get the desired result. Preprocessing steps varies from purpose to purpose."""
sentences = re.compile('[.!?]').split(text)
sentences
```
```
  ['This is text for testing preprocessing steps for nlp',
   ' For nlp, preprocessing steps are very much important',
   ' Preprocessing steps improve the accuracy in percentage(%)',
   " If you don't follow preprocessing steps, you can't get the desired result",
   ' Preprocessing steps varies from purpose to purpose',
   '']
```
#### Using NLTK
NLTK contains a module named tokenize() which has two sub-categories - 1) Word Tokenize and 2) Sentence Tokenize
  > punkt is a nltk library tool for tokenizing text documents. When we use an old or a degraded version of nltk module we generally need to download the remaining data -
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('corpus')
```
# Download and Import NLTK
!pip install nltk
import nltk
nltk.download('punkt')    #punkt is a nltk library tool for tokenizing text documents.
```
To tokenize in nltk, we can use word_tokenize module from nltk.tokenize class.
```
# Word tokenization
from nltk.tokenize import word_tokenize
text = """This is text for testing preprocessing steps for nlp. For nlp, preprocessing steps are very much important. Preprocessing steps improve the accuracy in percentage(%). If you don't follow preprocessing steps, you can't get the desired result. Preprocessing steps varies from purpose to purpose."""
print(word_tokenize(text))
```
```
  ['This', 'is', 'text', 'for', 'testing', 'preprocessing', 'steps', 'for', 'nlp', '.', 'For', 'nlp', ',', 'preprocessing', 'steps', 'are', 'very', 'much', 'important', '.', 'Preprocessing', 'steps', 'improve', 'the', 'accuracy', 'in', 'percentage', '(', '%', ')', '.', 'If', 'you', 'do', "n't", 'follow', 'preprocessing', 'steps', ',', 'you', 'ca', "n't", 'get', 'the', 'desired', 'result', '.', 'Preprocessing', 'steps', 'varies', 'from', 'purpose', 'to', 'purpose', '.']
```
For sentence tokenization, nltk has sent_tokenize module in nltk.tokenize class.
```
# Sentence tokenization
from nltk.tokenize import sent_tokenize
text = """This is text for testing preprocessing steps for nlp. For nlp, preprocessing steps are very much important. Preprocessing steps improve the accuracy in percentage(%). If you don't follow preprocessing steps, you can't get the desired result. Preprocessing steps varies from purpose to purpose."""
sent_tokenize(text)
```
```
  ['This is text for testing preprocessing steps for nlp.',
   'For nlp, preprocessing steps are very much important.',
   'Preprocessing steps improve the accuracy in percentage(%).',
   "If you don't follow preprocessing steps, you can't get the desired result.",
   'Preprocessing steps varies from purpose to purpose.']
```
