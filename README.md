# Gojek App Review Sentiment Analysis

## 📌 Project Summary
This project aims to build a *machine learning* model capable of classifying sentiment (positive, negative, neutral) from Gojek app user reviews on the Google Play Store. Using the **Multinomial Naive Bayes** algorithm and comprehensive text preprocessing techniques, this model was developed to understand public perception of Gojek's services.

Although the model achieved an overall accuracy of **79.7%**, a deeper analysis reveals that its performance is highly imbalanced. The most crucial finding of this project is that the model is very reliable at detecting negative reviews but almost completely fails to identify neutral and positive reviews.

🔗 **[View Complete Code on GitHub](https://github.com/YusepFathul/Analisis-Sentimen-Gojek)**

---

## 🎯 Project Objectives
- **Text Data Preprocessing:** To clean, normalize, and transform raw user review data into an analysis-ready format.
- **Model Development:** To build a sentiment classification model using Multinomial Naive Bayes, including handling of imbalanced data.
- **Critical Evaluation:** To thoroughly analyze the model's performance using metrics like *Precision, Recall, F1-score,* and the *Confusion Matrix*, not just relying on accuracy.
- **Challenge Identification:** To identify the model's weaknesses and the challenges arising from the dataset's characteristics.

---

## 🧰 Technologies & Libraries Used
- **Workspace:** Google Colaboratory
- **Core Libraries:**
  - **`Python`**
  - **`Pandas`** & **`NumPy`**: For data manipulation and cleaning.
  - **`Scikit-learn`**: For TF-IDF Vectorizer, Naive Bayes model, and evaluation metrics.
  - **`Imbalanced-learn`**: For the SMOTE over-sampling technique.
  - **`Stanza`**: For tokenization of Indonesian text.
  - **`Matplotlib`** & **`Seaborn`**: For data visualization.

---

## 🛠️ Project Methodology

1.  **Data Collection & Cleaning:**
    - **Source:** Gojek app review dataset from Kaggle.
    - **Cleaning:** Removed irrelevant columns and all rows with empty (NaN) values, which reduced the dataset from 445,500 to 90,559 rows.
    - **Sampling:** Took a random sample of 10,000 data points for computational efficiency.

2.  **Text Preprocessing:**
    - **Normalization:** Converted text to lowercase and removed non-alphabetic characters.
    - **Tokenization:** Split sentences into words (tokens) using the **Stanza** library, which is designed for Indonesian linguistics.

3.  **Sentiment Labeling:**
    Sentiment was automatically determined based on the star rating (`score`):
    - **Negative**: Score < 3 (⭐ & ⭐⭐)
    - **Neutral**: Score = 3 (⭐⭐⭐)
    - **Positive**: Score > 3 (⭐⭐⭐⭐ & ⭐⭐⭐⭐⭐)

4.  **Machine Learning Modeling:**
    - **Feature Extraction:** Converted text into numerical vectors using **TF-IDF Vectorizer**, considering both single words and two-word phrases (*bigrams*).
    - **Handling Imbalance:** Applied **SMOTE** (*Synthetic Minority Over-sampling Technique*) on the training data to balance the number of samples in each sentiment class.
    - **Algorithm:** Used the **Multinomial Naive Bayes** model for classification.

---

## 📈 Results and Analysis

### Sentiment Distribution
Data visualization shows the sample dataset is highly imbalanced and dominated by negative sentiment.
- **Negative**: 83.5%
- **Neutral**: 13.4%
- **Positive**: 3.1%

*Insight: The majority of users in this sample provided reviews with a negative tone, indicating significant issues that need attention.*

### Model Performance
Although the overall accuracy is **79.7%**, this figure is misleading. A deeper analysis through the *Classification Report* and *Confusion Matrix* shows:

- **Excellent for Negative Sentiment:** The model is very good at detecting negative reviews (**F1-score of 0.90**).
- **Very Poor for Neutral & Positive Sentiment:** The model has almost no ability to identify neutral reviews (**F1-score of 0.11**) or positive reviews (**F1-score of 0.17**).
- **Conclusion from Confusion Matrix:** The model tends to "play it safe" by predicting the majority class (negative). Most neutral and positive reviews were incorrectly classified as negative.

---

## 💡 Conclusion and Key Insights

1.  **Dominance of Negative Sentiment:** Reviews for the Gojek app in this dataset are significantly dominated by complaints and criticism.
2.  **Biased Model:** The developed Naive Bayes model is heavily biased towards the majority class (negative). The high accuracy is merely an illusion that masks its inability to recognize other classes.
3.  **Ineffective for Positive Feedback:** This model cannot be relied upon to filter for positive or neutral reviews, limiting its usefulness for understanding product strengths or specific areas for improvement.
4.  **Imbalanced Data Challenge:** The SMOTE technique proved insufficient to overcome the extreme data imbalance in this case.

---

## Challenges and Potential Improvements
- **Key Challenges:** Extreme class imbalance and potential bias introduced during data cleaning (removing thousands of NaN rows).
- **Potential Improvements:**
  - Using more advanced sampling techniques (e.g., a combination of SMOTE and Edited Nearest Neighbours).
  - Trying other algorithms that are more robust to imbalanced data, such as **SVM** or **XGBoost**.
  - Collecting additional data, especially for positive and neutral reviews, to create a more representative dataset.

---

## 👤 Contact
- **Name:** Yusep Fathul Anwar
- **LinkedIn:** [https://www.linkedin.com/in/yusepfathulanwar/](https://www.linkedin.com/in/yusepfathulanwar/)
- **Github:** [https://github.com/YusepFathul](https://github.com/YusepFathul)
