# Data Augmentation for Languages with small datasets

Finding annotated data for every target task in every target language is difficult, more so when the target language has only small datasets available. It has been observed that the performance of techniques like neural machine translation (NMT), phrase-based statistical machine translation (PBSMT), drops starkly in low-resource conditions, requiring large amounts of auxiliary data to achieve competitive results. For such scenarios, techniques like weak-supervision, data augmentation, transfer learning, etc. have shown promising results. In this project, we explore data augmentation techniques to improve Machine Translation
for the Hindi language.

We employ 4 different text editing techniques for augmentation (Wei & Zou, 2019). For a given sentence in the training set, we randomly choose and perform one of the following operations:

1. Synonym Replacement (SR): Choose α fraction of random words from the sentence that are not stop words. Replace each of these words with one of its
synonyms chosen at random.
2. Random Insertion (RI): Find a random synonym of a random word in the sentence that is not a stop word and insert that synonym into a random position in the sentence. Do this for α fraction of the total words.
3. Random Swap (RS): Randomly choose two words in the sentence and swap their positions. Do this for α fraction of the total words.
4. Random Delete (RD): Randomly choose n words in the sentence and delete them. Do this for α fraction of the total words.
Data Augmentation for Languages with small datasets For our experiments, we range α from 0 (no augmentation) to 0.5 (half the sentence is augmented).

Dataset used - IIT Bombay English-Hindi Corpus (Anoop Kunchukuttan, 2018)

Sentence generation

The IIT Bombay English-Hindi corpus contains 1.6M sentences in the training set. We randomly took subsets of 100k, 500k, and 1M sentences and applied each of the four editing techniques five times per sentence to generate 500k, 2.5Mvand 5M augmented sentences per technique.

Libraries

Princeton Wordnet was used for finding synonyms in English. For this purpose, we used the wordnet package from Python Natural Language Toolkit (NLTK). For finding
synonyms in Hindi, we used the pyiwn (Panjwani et al., 2017) package in Python which uses Hindi Wordnet from CFILT, IIT Bombay in the background.

We used the Facebook's XLM model for training purposes. Details about results and training are present in the project report.

Notes
- Code for SR is present at https://github.com/thisisabhash/indoWordAug
- Code for RI, RS, RD is present at https://github.com/thisisabhash/cs839-data-augment-nlp
- Code for training the XLM model is at https://github.com/thisisabhash/XLM

Instructions for running the code are present in the respective repositories.

For running code in this repository, place the Hindi-English corpus files at a folder of your preference [here it is inside the 'parallel' folder in the working directory] and run augment.py to generate augmented sentences. Please change the below paths in the code [ and also the respective paths for storing subset/augmented data] 

HINDI_FULL_PATH = '/parallel/IITB.en-hi.hi'

ENGLISH_FULL_PATH = '/parallel/IITB.en-hi.en'

