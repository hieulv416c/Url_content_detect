# Url_content_detect

🚀 1. Overview

WebGuard is a machine learning system designed to detect phishing and fraudulent websites based on full HTML content, not just URLs.

Traditional blacklist or URL-only approaches struggle against new phishing sites. WebGuard solves this by analyzing every website’s visible text content, then applying multiple embedding techniques and machine learning models to determine whether the site is legitimate or malicious.

📌 This project is based on the academic research:
“WebGuard: Hệ thống phát hiện trang web lừa đảo dựa trên nội dung sử dụng học máy đa mô hình” – UEL, 2025.

📚 2. Dataset

Source: Mendeley Data (Ariyadasa et al., 2023)

Size: 80,000 HTML files

Label distribution:

~50,000 legitimate websites

~30,000 phishing websites

After cleaning and preprocessing → 68,859 samples used.

Each sample includes:

Raw HTML

Extracted textual content

Label (0 = legitimate, 1 = phishing)

🧼 3. Preprocessing Pipeline

The following steps were applied to every HTML file:

Extract visible text from HTML using BeautifulSoup

Remove scripts, styles, tags

Convert to lowercase

Remove punctuation

Remove stopwords

Lemmatization

Tokenization

Handle missing values & duplicates

This results in clean text ready for embedding.

🧠 4. Embedding Techniques Used

WebGuard compares four text-representation approaches:

1️⃣ TF-IDF (Term Frequency – Inverse Document Frequency)

Top 5,000 most important features

Sparse vector representation

Strong baseline for classification

2️⃣ Word2Vec

Trained using 68k cleaned samples

Vector size = 100

Uses mean-pooling to obtain document-level vectors

3️⃣ Doc2Vec

Distributed Memory (DM) + Distributed Bag of Words (DBOW)

Vector size = 100

Captures semantic meaning better than Word2Vec

4️⃣ BERT Embedding

Pretrained model: bert-base-uncased

Uses CLS token (768-dim vector)

Highest semantic accuracy but slowest computation

🤖 5. Machine Learning Models Evaluated

10 classification models were used:

Category	Models
Linear	Logistic Regression
Probabilistic	Naive Bayes
Distance-based	KNN
Neural	MLP Classifier
SVM	Linear SVC
Tree-based	Decision Tree
Ensemble	Random Forest
Boosting	Gradient Boosting
Advanced Boosting	XGBoost, CatBoost
📊 6. Experimental Setup

Platform: Google Colab Pro

Hardware: GPU T4 / CPU

Evaluation Metrics:

Accuracy

Precision

Recall

F1-score

Confusion Matrix

Training Time

🏆 7. Results Summary
🥇 Best Overall Performance: TF-IDF + XGBoost / CatBoost

Highest accuracy

Fastest inference

Best stability

BERT + ML models

Very high recall (good for catching phishing)

Slow and heavy → not optimal for deployment

Doc2Vec / Word2Vec

Good semantic representation

But lower classification accuracy than TF-IDF for this dataset


📈 8. Example Output

From the experiments:

Embedding	Best Model	Accuracy	Notes
TF-IDF	CatBoost	~95%	Best balance
BERT	SVM / LR	High recall	Slow
Doc2Vec	Random Forest	Medium	Semantic
Word2Vec	XGBoost	Medium	Fast
👨‍💻 9. Authors

Lê Văn Hiếu

Trương Thị Thanh Hà

Phan Thị Minh Huyền

Đoàn Gia Bảo Ngọc

Nguyễn Chí Khánh Trình

Supervisor: TS. Trần Duy Thanh

📄 12. License

This project is for academic research and educational purposes.

🎯 13. Contact

If you have questions or want to extend this work, feel free to contact:
📧 Hieulv22416c@st.uel.edu.vn
