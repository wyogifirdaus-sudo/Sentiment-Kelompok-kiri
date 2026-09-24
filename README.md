# Indonesian Historical & Political Text Analysis

An end-to-end **data analysis and Natural Language Processing (NLP) project** exploring Indonesian historical and political discourse through news scraping, YouTube comment analysis, sentiment analysis, and machine learning.

This project combines two related workflows:

1. **Communism-Related News Scraping** — collecting and analyzing news articles related to communism.
2. **G30S YouTube Comment Sentiment Analysis** — analyzing public comments related to the film *Penumpasan Pengkhianatan G30S*.

The project demonstrates how computational methods can be applied to historical, political, and media research.

---

## Project Overview

This repository applies a combination of:

* Web scraping
* Data collection
* Data cleaning
* Exploratory Data Analysis (EDA)
* Indonesian text preprocessing
* Sentiment analysis
* TF-IDF feature extraction
* Machine learning classification
* Data visualization

The overall workflow can be summarized as:

```text
Data Collection
      ↓
Data Cleaning
      ↓
Text Preprocessing
      ↓
Exploratory Data Analysis
      ↓
Sentiment Labeling
      ↓
TF-IDF Feature Extraction
      ↓
Machine Learning
      ↓
Model Evaluation
      ↓
Visualization & Insights
```

---

# 1. Communism-Related News Scraping

### Notebook

```text
scrapping_komunisme.ipynb
```

This notebook collects news articles related to **communism** through Google News RSS and transforms the collected information into a structured dataset.

### Data Collection Process

The workflow includes:

1. Defining a search query related to communism.
2. Encoding the search query.
3. Retrieving Google News RSS results.
4. Parsing RSS data using BeautifulSoup.
5. Extracting news information.
6. Storing the results in a CSV file.
7. Checking the structure and quality of the dataset.
8. Identifying duplicate records.
9. Checking missing values.
10. Removing unnecessary columns.
11. Analyzing publication dates.
12. Visualizing the frequency of collected news articles.

### Main Libraries

```text
Pandas
Requests
BeautifulSoup
urllib
Matplotlib
```

### Output

The scraping process produces a dataset containing collected news information:

```text
beritakomunis.csv
```

The dataset can subsequently be used for media monitoring, historical research, trend analysis, and text-mining applications.

---

# 2. G30S YouTube Comment Sentiment Analysis

### Notebook

```text
sentiment (1).ipynb
```

This notebook analyzes YouTube comments related to the film:

> *Penumpasan Pengkhianatan G30S*

The project focuses on identifying sentiment patterns within Indonesian-language user comments and evaluating machine learning models for sentiment classification.

---

## Data Collection

YouTube comments are collected using the **YouTube Data API v3**.

The collected information includes:

* Publication date
* Username
* Comment text
* Like count

The collected data is stored in:

```text
youtube-g30s-22sep26.csv
```

Comments containing only URLs are removed before the text-analysis stage.

---

# Text Preprocessing

The collected Indonesian-language comments are processed through several stages.

### 1. Data Cleaning

Unnecessary characters and textual noise are removed from the comments.

### 2. Case Folding

All text is converted into lowercase.

Example:

```text
Film G30S Sangat Menarik
```

becomes:

```text
film g30s sangat menarik
```

### 3. Word Normalization

Non-standard Indonesian words are converted into standardized forms using a slang-word dictionary.

### 4. Tokenization

Sentences are separated into individual tokens or words.

Example:

```text
film ini sangat menarik
```

becomes:

```text
["film", "ini", "sangat", "menarik"]
```

### 5. Stopword Removal

Common Indonesian stopwords are removed using an Indonesian stopword list.

### 6. Stemming

Words are converted into their root forms using **Sastrawi**.

The processed data is stored in:

```text
data_preprocessing.csv
```

---

# Sentiment Analysis

Sentiment labels are generated using Indonesian sentiment lexicons based on the **InSet (Indonesia Sentiment Lexicon)**.

The comments are classified into three categories:

```text
Positive
Neutral
Negative
```

The labeled dataset is stored in:

```text
data_labelling.csv
```

The analysis also includes sentiment distribution and word-cloud visualization.

---

# TF-IDF Feature Extraction

After preprocessing and sentiment labeling, the text is transformed into numerical features using:

**TF-IDF — Term Frequency-Inverse Document Frequency**

TF-IDF represents the importance of individual words within the dataset and provides numerical features that can be used by machine learning algorithms.

The processed text is used as the input feature:

```python
X = data["stemming"]
```

while sentiment labels are used as the target:

```python
y = data["label"]
```

---

# Machine Learning Classification

Several machine learning algorithms are evaluated for sentiment classification:

| Model                   | Accuracy |
| ----------------------- | -------: |
| Logistic Regression     |      88% |
| Support Vector Machine  |      84% |
| Random Forest           |      82% |
| Multinomial Naive Bayes |      72% |
| K-Nearest Neighbors     |      58% |

The evaluation uses:

* Accuracy
* Classification Report
* Confusion Matrix

The notebook reports Logistic Regression with an accuracy of **88%** on the evaluated dataset.

These results are specific to the dataset, preprocessing pipeline, train-test split, and model configuration used in the notebook.

---

# Exploratory Data Analysis

The project generates several visualizations to explore the collected data.

### News Data

* News frequency by publication date
* Temporal distribution of articles

### YouTube Comments

* Word frequency before preprocessing
* Word frequency after preprocessing
* Sentiment distribution
* Sentiment percentage
* Positive sentiment word cloud
* Negative sentiment word cloud
* Neutral sentiment word cloud

### Machine Learning

* Model accuracy comparison
* Confusion matrices

---

# Repository Structure

```text
.
├── README.md
│
├── scrapping_komunisme.ipynb
├── sentiment (1).ipynb
│
├── beritakomunis.csv
├── youtube-g30s-22sep26.csv
├── data_preprocessing.csv
└── data_labelling.csv
```

Dataset files may be excluded from the repository depending on their size, data availability, or API restrictions.

---

# Technologies

### Programming Language

```text
Python
```

### Data Collection

```text
Requests
BeautifulSoup
Google News RSS
YouTube Data API v3
Google API Client
```

### Data Processing

```text
Pandas
NumPy
NLTK
Sastrawi
Regular Expressions
```

### Natural Language Processing

```text
TF-IDF
InSet Indonesian Sentiment Lexicon
WordCloud
Indonesian Stopwords
```

### Machine Learning

```text
Scikit-learn
```

### Data Visualization

```text
Matplotlib
Seaborn
WordCloud
```

### Development Environment

```text
Google Colab
Jupyter Notebook
```

---

# Installation

Clone this repository:

```bash
git clone https://github.com/yourusername/your-repository.git
cd your-repository
```

Install the required libraries:

```bash
pip install pandas numpy requests beautifulsoup4
pip install matplotlib seaborn wordcloud
pip install nltk Sastrawi scikit-learn
pip install google-api-python-client
```

If using the Google Generative AI components included in the notebook:

```bash
pip install langchain-google-genai
```

---

# API Configuration

The YouTube scraping workflow requires a **YouTube Data API v3 key**.

For security, API keys should never be committed directly to GitHub.

When using Google Colab, the API key can be stored using Colab Secrets:

```python
from google.colab import userdata

api_key = userdata.get("GOOGLE_API_KEY")
```

Never expose your actual API key in the notebook or repository.

---

# Reproducibility

To reproduce the analysis:

1. Open the notebooks in Google Colab or Jupyter Notebook.
2. Install the required dependencies.
3. Configure the required API credentials.
4. Run the data collection process.
5. Clean and preprocess the data.
6. Perform exploratory analysis.
7. Generate sentiment labels.
8. Extract TF-IDF features.
9. Train the machine learning models.
10. Evaluate model performance.
11. Generate visualizations and interpret the results.

---

# Research Applications

This project demonstrates potential applications of computational methods in:

* Data Journalism
* Computational Journalism
* Historical Research
* Digital Humanities
* Media Monitoring
* Public Discourse Analysis
* Natural Language Processing
* Sentiment Analysis
* Text Mining
* Social and Political Research

The combination of historical research and computational analysis provides a way to examine large amounts of textual information while maintaining a research-oriented approach to data interpretation.

---

# Limitations

Several limitations should be considered:

* Google News RSS results depend on search availability and the structure of the RSS feed.
* YouTube comments represent users who commented on the selected content and should not automatically be treated as representative of the entire population.
* Lexicon-based sentiment labeling may have difficulty interpreting sarcasm, irony, negation, slang, and context-dependent expressions.
* Indonesian informal language can introduce challenges during normalization and stemming.
* Machine learning performance depends on the dataset and experimental configuration.
* Accuracy alone does not fully describe model performance.

Therefore, the results should be interpreted within the scope of the dataset and research methodology used in the notebooks.

---

# Author

**Wisnu Yogi Firdaus**

History Graduate | Researcher | Journalist | Data & AI Enthusiast

### Research Interests

* Historical Research
* Journalism
* Data Journalism
* Natural Language Processing
* Machine Learning
* Digital Humanities
* Social History
* Political History
* Media Analysis

---

# License

This project is intended for **educational, research, and portfolio purposes**.

Users should comply with the terms of service, copyright policies, and API usage policies of external platforms when collecting or processing data.

---

# Acknowledgements

This project uses publicly available tools, libraries, APIs, and resources, including:

* Google News RSS
* YouTube Data API
* InSet Indonesian Sentiment Lexicon
* NLTK
* Sastrawi
* Scikit-learn
* Pandas
* NumPy
* Matplotlib
* Seaborn
* WordCloud
* Google Colab

---
