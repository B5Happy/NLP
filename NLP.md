# Natural Language Processing

## Intro 

Check out the following technologies:

![NLP_use_cases](./img/nlp.gif)

What do they have in common?

All of these handy technologies exist because of natural language processing! Also known as NLP, the field is at the intersection of linguistics, artificial intelligence, and computer science. The goal? Enabling computers to interpret, analyze, and approximate the generation of human languages.

But approximating human speech is only one of a wide range of applications for NLP! Applications from detecting spam emails or bias in tweets to improving accessibility for people with disabilities all rely heavily on natural language processing techniques.

## Text Preprocessing

Cleaning and preparation are crucial for many tasks, and NLP is no exception. Text preprocessing is usually the first step you'll take when faced with an NLP task. Without preprocessing, your computer interprets "the", "The", and "<p>The" as entirely different words. There is a LOT you can do here, depending on the formatting you need. Lucky for you, Regex and NLTK will do most of it for you! Common tasks include:

Noise removal — stripping any text formatting (e.g., HTML tags).

Tokenization — breaking text into individual words.

Normalization — almost anything else you'd do to clean up your text data:

-Stemming is a blunt axe to chop off word prefixes and suffixes. "booing" and "booed" become "boo", but "sing" may become "s" and "sung" would remain "sung."
-Lemmatization is a scalpel to bring words down to their root forms. For example, NLTK's savvy lemmatizer knows "am" and "are" are related to "be."
-Other common tasks include lowercasing, punctuation removal, stopwords removal, spelling correction, etc.

For example:
```python
# regex for removing punctuation!
import re
# nltk preprocessing magic
import nltk
from nltk.tokenize import word_tokenize
from nltk.stem import PorterStemmer
from nltk.stem import WordNetLemmatizer
# grabbing a part of speech function:
from part_of_speech import get_part_of_speech

# sample
text = "So many squids are jumping out of suitcases these days that you can barely go anywhere without seeing one burst forth from a tightly packed valise. I went to the dentist the other day, and sure enough I saw an angry one jump out of my dentist's bag within minutes of arriving. She hardly even noticed."

# remove ponctuation
cleaned = re.sub('\W+', ' ', text)
# split the sentence into words
tokenized = word_tokenize(cleaned)

# sort the word with same meaning
stemmer = PorterStemmer()
stemmed = [stemmer.stem(token) for token in tokenized]

# make sure it went good
lemmatizer = WordNetLemmatizer()
lemmatized = [lemmatizer.lemmatize(token, get_part_of_speech(token)) for token in tokenized]

# result
print("Stemmed text:")
print(stemmed)
print("\nLemmatized text:")
print(lemmatized)
```

