# NLP-Based Topic Extraction of Consumer Complaints

**Author:** Daniela de Sousa Silva

## Description

This project applies NLP techniques to extract recurring themes from unstructured consumer complaint narratives. The scenario mirrors a real-world governance context in which decision-makers must identify the most relevant issues from large volumes of free-text citizen feedback.

To simulate it, the project uses the Consumer Complaint Database published by the Consumer Financial Protection Bureau. Due to size and licensing considerations, the original dataset is not included in this repository and must be downloaded separately.

The project follows a complete exploratory NLP pipeline, from data filtering and linguistic preprocessing to vectorization, topic extraction, and quantitative evaluation using multiple modeling approaches.

---

## Key NLP Features

- **Text Preprocessing Pipeline:** Lowercasing, noise removal, stopword filtering, and context-aware lemmatization using spaCy.
- **Length-Based Filtering and Sampling:** Removal of very short complaints and random sampling to balance computational efficiency and thematic diversity.
- **N-gram Integration:** Extraction of unigrams and bigrams during vectorization to capture meaningful multi-word expressions such as _"credit report"_ or _"identity theft"_.
- **Vectorization Comparison:** Bag-of-Words and TF-IDF representations are applied and compared directly, highlighting differences in how each method weights frequent vs. distinctive terms.
- **Comparative Topic Modeling:** LDA applied to BoW features and NMF applied to TF-IDF features, reflecting the mathematical formulation of each model.
- **Independent Model Evaluation:** LDA is evaluated using C_v coherence; NMF using reconstruction error (Frobenius norm) — each assessed with the metric suited to its optimization objective.
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
│   ├── complaints.csv                  # To be downloaded manually (not included)
│   ├── complaints_sample.pkl
│   └── complaints_sample_cleaned.pkl
│
├── notebooks/
│   └── topic_modeling.ipynb
│
├── requirements.txt                    # Project dependencies
└── README.md
```

---

## Setup and Installation

### 1. Local Environment Setup

1. **Clone the Repository**

```
git clone https://github.com/sousa-daniela/consumer-complaints-nlp.git
cd consumer-complaints-nlp
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
    - compare BoW and TF-IDF vectorization outputs,
    - extract topics using LDA and NMF,
    - evaluate each model independently and visualize results.

Intermediate artefacts are automatically saved in `data/`.

---

## Methodological Notes

- Topic modeling is performed in an unsupervised, exploratory setting with no ground-truth labels. Topic quality is assessed using quantitative metrics (C_v coherence for LDA, reconstruction error for NMF), as well as qualitative inspection of keyword interpretability.
- LDA and NMF are evaluated independently using metrics suited to each model's mathematical formulation, and the optimal number of topics is determined separately for each.
- N-grams are incorporated directly during vectorization to improve topic interpretability without introducing additional preprocessing complexity.
- LDA and NMF are paired with BoW and TF-IDF respectively, reflecting the generative assumptions of LDA and the signal quality requirements of NMF.

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
