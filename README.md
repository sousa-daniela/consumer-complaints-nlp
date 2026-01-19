
# NLP-Based Topic Extraction of Consumer Complaints

**Author:** Daniela de Sousa Silva

## 2026-01-19 Status: This project is currently under active development.
The core NLP pipeline and methodology are implemented; documentation and analysis are being refined.

## Description

This project applies NLP techniques to extract recurring themes from unstructured consumer complaint narratives. The scenario mirrors a real-world governance context in which decision-makers must identify the most relevant issues from large volumes of free-text citizen feedback.

To simulate it, the project uses the Consumer Complaint Database published by the Consumer Financial Protection Bureau. Due to size and licensing considerations, the original dataset is not included in this repository and must be downloaded separately.

The project follows a complete exploratory NLP pipeline, from data filtering and linguistic preprocessing to vectorization and topic extraction using multiple modeling approaches.

---

## Key NLP Features

- **Text Preprocessing Pipeline:** Lowercasing, noise removal, stopword filtering, and context-aware lemmatization using spaCy.
- **Length-Based Filtering and Sampling:** Removal of very short complaints and random sampling to balance computational efficiency and thematic diversity.
- **N-gram Integration:** Extraction of unigrams and bigrams during vectorization to capture meaningful multi-word expressions such as _“credit card”_.
- **Vectorization Strategies:** Bag-of-Words and TF-IDF representations for comparative analysis.
- **Comparative Topic Modeling:** Application and comparison of Latent Dirichlet Allocation (LDA) and Non-negative Matrix Factorization (NMF).
- **Reproducibility:** Intermediate results are stored as pickle files to reduce runtime and ensure reproducibility.

---

## Tech Stack

- **Language:** Python
- **Data Handling:** Pandas, NumPy
- **NLP:** spaCy
- **Modeling:** Scikit-learn, Gensim
- **Visualisation:** Matplotlib

---

## Project Structure

```
consumer-complaints-nlp/
│
├── data/
│   ├── complaints.csv   # To be downloaded manually (not included)
│   ├── complaints_sample.pkl
│   └── complaints_sample_cleaned.pkl
│
├── notebooks/
│   └── topic_modeling.ipynb
│
├── requirements.txt   # Project dependencies
└── README.md
```

---

## Setup and Installation

### 1. Local Environment Setup

1. **Clone the Repository**

```
git clone https://github.com/sousa-daniela/consumer-complaints-nlp.git
cd conszmer-complaints-nlp
```
 
2. **Create and Activate a Virtual Environment**

```
python3 -m venv venv
source venv/bin/activate
```
 
3. **Install Dependencies**

```
pip install -r requirements.txt
```

4. **Download spaCy Language Model**

```
python -m spacy download en_core_web_sm
```

---

## Dataset Preparation

1. Download the **Consumer Complaint Database** from:
    - [Data.gov](https://catalog.data.gov/dataset/consumer-complaint-database)

2. Extract the dataset and place the CSV file in the following location:

```
data/complaints.csv
```
 
3. Ensure the file name matches exactly, as it is referenced directly in the notebook.

---

## Usage

1. Open the notebook:

```
notebooks/topic_modeling.ipynb
```
    
2. Run the notebook sequentially from top to bottom to:
    
    - filter and sample complaints,
    - preprocess and lemmatise text,
    - generate n-grams and vector representations,
    - extract topics using LDA and NMF.

Intermediate artefacts are automatically saved in data.

---

## Methodological Notes

- Topic modeling is performed in an unsupervised, exploratory setting. Topic quality is assessed qualitatively based on interpretability and semantic coherence.  
- N-grams are incorporated directly during vectorization to improve topic interpretability without introducing additional preprocessing complexity.
- LDA and NMF are compared to highlight differences between probabilistic and matrix-factorization-based approaches.

---

## Dataset Source

Consumer Complaint Database - Consumer Financial Protection Bureau (CFPB)

[Data Gov](https://www.consumerfinance.gov/data-research/consumer-complaints/)

---

## Author Notes

This project was developed as part of an NLP-focused coursework assignment with a governance-oriented framing. The emphasis is placed on methodological transparency and interpretability rather than predictive performance.

---

## License

This project is licensed under the MIT License. See the LICENSE.md file for details.
