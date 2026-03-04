# 🕵️‍♂️ Fake News Detection using Machine Learning

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange.svg)](https://scikit-learn.org/)
[![Accuracy](https://img.shields.io/badge/Accuracy-98.55%25-brightgreen.svg)](#-evaluation)

## 📌 Project Overview
In the digital age, misinformation spreads rapidly. This project implements a high-performance **Natural Language Processing (NLP)** pipeline to automatically classify news articles as **Real** or **Fake**. By analyzing textual patterns, the model helps identify deceptive content with high precision.

---

## 📂 Dataset Information
The datasets used in this project are large CSV files containing over 40,000 news articles. Due to their size, they are not hosted directly in this repository. You can download them from Kaggle below:

* **[Download Link: Fake and Real News Dataset](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset)**
    * `True.csv`: Contains authentic news articles.
    * `Fake.csv`: Contains fabricated or misleading news articles.

---

## ⚙️ The Workflow

### 1. Data Preprocessing
Raw text is cleaned to ensure the model focuses on meaningful content:
* **Cleaning:** Removed special characters, punctuation, and URLs.
* **Stopword Removal:** Eliminated common filler words (e.g., "the", "is") using NLTK.
* **Lemmatization:** Words were reduced to their root forms (e.g., "running" → "run") to consolidate meaning.

### 2. Feature Extraction (TF-IDF)
The cleaned text is converted into numerical vectors using **TF-IDF (Term Frequency-Inverse Document Frequency)**. This mathematical approach highlights unique keywords that distinguish "clickbait" or fake reporting from factual journalism.



### 3. Model Training
I utilized a **Logistic Regression** classifier. This algorithm is highly effective for text classification tasks where the relationship between word frequencies and the target class is strong.

---

## 📊 Evaluation Results
The model was evaluated on a test set of **8,980 articles**, achieving exceptional performance:

| Metric | Score |
| :--- | :--- |
| **Accuracy** | **98.55%** |
| **F1-Score** | **98.62%** |

The classification report shows near-perfect **Precision** and **Recall**, indicating that the model is extremely reliable at identifying both news types.



---

## ☁️ Visualizing the Data
Using **Word Clouds**, we can see the most influential terms:
* **Real News:** Focused on government officials, international relations, and factual events.
* **Fake News:** Features sensationalist keywords, "breaking" buzzwords, and politically charged emotional triggers.

*(Note: Upload your word cloud images to an 'images' folder to see them here)*
![Real News Cloud](./images/real_wordcloud.png)
![Fake News Cloud](./images/fake_wordcloud.png)

---

## 🚀 How to Run
1. Clone the repository.
2. Download the datasets from the link in the **Dataset Information** section and place them in the root directory.
3. Install the required libraries:
   ```bash
   pip install -r requirements.txt

   ---
---

## ⚡ Try It Yourself!
Want to see the model in action? Here is a snippet of how the classifier interprets a single headline. This "Live Prediction" capability shows the real-world utility of the trained model.

```python
# A simple look at how the model thinks:
headline = ["BREAKING: Secret documents prove the moon is made of blue cheese!"]
cleaned_headline = preprocess_text(headline)
vectorized_headline = tfidf.transform([cleaned_headline])

prediction = model.predict(vectorized_headline)
status = "🚨 FAKE" if prediction[0] == 1 else "✅ REAL"
print(f"Result: {status}")
