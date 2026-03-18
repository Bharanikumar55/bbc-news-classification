# 🧠 BBC Hindi News Topic Classification (IndicGLUE)

## 📌 Project Overview

This project focuses on classifying Hindi news articles into different categories using the **IndicGLUE (bbca.hi)** dataset. Multiple machine learning and representation learning techniques were explored to analyze how different approaches impact classification performance.

The project emphasizes **comparative analysis**, showing how feature representation plays a crucial role in NLP tasks.

---

## 📂 Dataset

* Source: IndicGLUE (AI4Bharat)
* Language: Hindi
* Task: News Topic Classification
* Classes: 14 (original dataset)
* Challenges:

  * Class imbalance
  * Overlapping vocabulary between categories (e.g., *sport* vs *international*)

---

## ⚙️ Methodology

### 🔹 1. Data Preprocessing

* Unicode-safe text cleaning (Hindi preservation)
* Removal of punctuation, numbers, and special symbols
* Tokenization of text
* Stopword removal (custom Hindi stopwords)
* Same preprocessing applied to both training and testing data

---

### 🔹 2. Feature Extraction

#### ✅ TF-IDF (Sparse Representation)

* Captures keyword importance
* Effective for topic-based classification

#### ✅ FastText (Dense Representation)

* Word embeddings capturing semantic meaning
* Sentence vectors obtained by averaging word embeddings

---

### 🔹 3. Models Used

#### 🔸 Logistic Regression

* Used with FastText embeddings
* Applied class weighting for imbalance handling

#### 🔸 Support Vector Machine (SVM)

* Used with both TF-IDF and FastText
* Performed best with TF-IDF features

#### 🔸 Autoencoder (PyTorch)

* Used for dimensionality reduction
* Latent representation: 32 dimensions
* Observed performance drop due to information loss

---

### 🔹 4. Handling Class Imbalance

* Used `class_weight='balanced'` in models
* Also experimented with filtered and balanced dataset subsets

---

## 📊 Results & Comparison

| Method                         | Accuracy   | Observation                               |
| ------------------------------ | ---------- | ----------------------------------------- |
| **TF-IDF + SVM**               | **72% 🔥** | Best performance (keyword-based learning) |
| FastText + Logistic Regression | 55%        | Captures semantic meaning                 |
| FastText + SVM                 | 45%        | Not suitable for dense embeddings         |
| FastText + Autoencoder         | 28%        | Information loss during compression       |

---

## 🔍 Key Insights

* 🔥 **TF-IDF outperformed embedding-based methods** due to strong keyword dependency in the dataset
* 📉 Autoencoder reduced dimensionality but lost important classification features
* ⚖️ Class imbalance significantly affected minority classes
* ❌ Increasing embedding dimension did not improve performance
* ❌ N-grams did not provide additional benefit (dataset already keyword-driven)
* ⚠️ Semantic overlap between categories (e.g., sport vs international) leads to unavoidable misclassification

---

## 🧠 Conclusion

The project demonstrates that **feature representation is more important than model complexity** in text classification tasks.

Traditional approaches like TF-IDF can outperform advanced embedding techniques when the task relies heavily on keyword patterns. While FastText captures semantic relationships, it may lose discriminative power when using simple averaging.

---

## 🚀 Future Improvements

* Use Transformer-based models (IndicBERT)
* Apply data augmentation (back translation)
* Hyperparameter tuning
* Ensemble learning methods
* Better handling of class imbalance

---

## 🛠️ Tech Stack

* Python
* Pandas, NumPy
* Scikit-learn
* Gensim (FastText)
* PyTorch (Autoencoder)
* Matplotlib (Visualization)

---

## 📈 Visualizations

* Model accuracy comparison
* Effect of preprocessing techniques
* Embedding dimension analysis

---

## 👨‍💻 Author

**Bharani Kumar**

---

## 💡 Key Takeaway

> “The choice of feature representation plays a more important role than model complexity in text classification.”
