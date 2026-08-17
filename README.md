# NLP Complete Guide

Personal learning notes and hands-on notebooks covering classical/traditional Natural Language
Processing (NLP) — text preprocessing, feature extraction, word embeddings, text classification,
and part-of-speech tagging. This is a study log, not a packaged library or production project:
notebooks mix theory (plain-language explanations) with runnable code and small experiments.

It's the NLP counterpart to [`Deep-learning-complete-guide`](https://github.com/Engrziaullah/Deep-learning-complete-guide),
a companion repo in the same "complete guide" series.

## Contents

| # | Notebook | Topics covered |
|---|----------|-----------------|
| 01 | [`Text preprocessing.ipynb`](<01%20Text%20preprocessing.ipynb>) | Lowercasing, HTML/URL removal, punctuation removal, chat-word normalization, text cleaning with Ekphrasis, spelling correction (TextBlob), stop-word removal, emoji handling, word/sentence tokenization, stemming (Porter), lemmatization (WordNet), intro to NLTK vs. spaCy |
| 02 | [`Feature Extraction.ipynb`](<02%20Feature%20Extraction.ipynb>) | Corpus/vocabulary/document terminology, One-Hot Encoding, Bag of Words, N-grams, TF-IDF, custom hand-crafted text features |
| 03 | [`Word2vac.ipynb`](<03%20Word2vac.ipynb>) | Word embeddings, Word2Vec (via `gensim`), pretrained vector loading |
| 04 | [`Text Classification.ipynb`](<04%20Text%20Classification.ipynb>) | End-to-end text classification pipeline: CountVectorizer features, `RandomForestClassifier`, `GaussianNB`, train/test split, accuracy and confusion matrix |
| 05 | [`POS Tagging.ipynb`](<05%20POS%20Tagging.ipynb>) | Part-of-speech tagging and dependency visualization with spaCy (`displacy`) |

Supporting reference diagrams (not auto-rendered by any notebook, kept as visual notes):

- `Bag of Words Example.png`
- `TF-IDF Diagram.png`
- `Summary important NLP feature extraction techniques.png`

## Tech stack

Classical NLP tooling — no deep learning frameworks (no PyTorch/TensorFlow/`transformers`) are
used in this repo; embeddings are handled via `gensim`'s Word2Vec and classification via
`scikit-learn`.

- **NLTK** — tokenization, stopwords, stemming, lemmatization
- **spaCy** (`en_core_web_sm` model) — tokenization, POS tagging, dependency parsing
- **TextBlob** — spelling correction
- **Ekphrasis** — social-media text normalization
- **gensim** — Word2Vec word embeddings
- **scikit-learn** — `CountVectorizer`, `TfidfVectorizer`, `RandomForestClassifier`, `GaussianNB`
- **pandas / numpy** — data handling
- **emoji**, **wget** — utility libraries used in a couple of cells

## Data

Two CSV files are included for the classification/preprocessing notebooks:

- `IMDB Review.csv` — despite the filename, this is **not** the standard IMDB movie-review
  sentiment dataset. Its columns (`Review_ID, Game_Title, Sentiment_Label, Review_Text`) and
  contents (tweets about entities like Borderlands, Amazon, Microsoft) match the
  [Twitter Entity Sentiment Analysis dataset](https://www.kaggle.com/datasets/jp797498e/twitter-entity-sentiment-analysis)
  from Kaggle. Notebook 01 also references a separate, not-present `IMDB Dataset.csv` — see
  **Known issues** below.
- `twitter_validation.csv` — the validation split of the same Twitter Entity Sentiment
  Analysis dataset.

## Setup

```bash
pip install pandas numpy nltk spacy textblob ekphrasis emoji gensim wget scikit-learn jupyter

python -m spacy download en_core_web_sm
python -m nltk.downloader stopwords punkt wordnet
```

Then open any notebook with Jupyter/JupyterLab and run cells top to bottom:

```bash
jupyter notebook
```

Notebooks were written independently as topic-by-topic notes rather than a single linear
pipeline, but 01 → 05 roughly follows a learning order (cleaning → features → embeddings →
classification → POS tagging).

## Known issues

- **`01 Text preprocessing.ipynb`** loads a dataset via `pd.read_csv('IMDB Dataset.csv')`, but
  no file with that name exists in the repo — only `IMDB Review.csv` is present, and (per the
  note above) it isn't the same dataset that filename implies. Running that cell as written will
  raise `FileNotFoundError`. Left unmodified rather than guessed at, since either the notebook's
  filename or the committed CSV needs to change and it isn't clear which was intended.

## Status

This is an active personal reference/learning collection, not a maintained package — expect
notebook-style exploratory code rather than tested, production-ready modules.
