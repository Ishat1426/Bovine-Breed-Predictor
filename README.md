# 🐄 Bovine Breed Predictor

An AI-powered deep learning application that classifies **Indian bovine breeds** using images captured from a **camera** or uploaded manually.  
The system predicts the breed among **5 predefined classes** using a trained CNN model.

---

## 📌 Project Overview

The **Bovine Breed Predictor** is a computer vision–based project developed to identify cattle breeds from images.  
It allows users to either:

- Capture an image using a camera  
- Upload an image manually  

The model then predicts the bovine breed with high accuracy.

This project is useful for:
- Farmers and dairy industries  
- Livestock management  
- Veterinary research  
- Smart agriculture systems  

---

## 🐄 Supported Breeds (5 Classes)

1. Gir  
2. Holstein Friesian (HF)  
3. Jersey  
4. Murrah  
5. Nili Ravi  

---

## 🚀 Features

- ✅ Camera-based image capture  
- ✅ Upload image for prediction  
- ✅ Deep learning CNN model  
- ✅ High accuracy classification  
- ✅ Fast and simple interface  
- ✅ Works locally  
- ✅ Easy to extend  

---

## 🧠 Technologies Used

| Category | Technology |
|--------|------------|
| Language | Python |
| Deep Learning | TensorFlow / Keras |
| Image Processing | OpenCV |
| Data Handling | NumPy, Pandas |
| Model | CNN |
| Web Framework | Flask |
| Visualization | Matplotlib |

---

## 📂 Project Structure

Bovine-Breed-Predictor/
│
├── dataset/
│   └── train/
│       ├── Gir/
│       ├── HF/
│       ├── Jersey/
│       ├── Murrah/
│       └── Nili_Ravi/
│
├── model/
│   └── bovine_model.h5
│
├── static/
│   └── uploads/
│
├── templates/
│   └── index.html
│
├── app.py
├── train_model.py
├── requirements.txt
└── README.md

---

## ⚙️ Installation & Setup

### Step 1: Clone Repository
```bash
git clone https://github.com/Ishat1426/Bovine-Breed-Predictor.git
cd Bovine-Breed-Predictor
```
### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Run Application
```bash
python app.py
```
📊 Working Flow
1. Data Collection
2. Data Preprocessing
3. Feature Extraction
4. Model Training
5. Model Evaluation
6. Breed Prediction

### 🧪 Sample Input
```bash
Image of cow or buffalo
Real-time camera input
Weight: 450 kg (optional)
Age: 4 years (optional)
Color: Brown (optional)
Milk Yield: 15 L/day (optional)
```
### Output
```bash
Predicted Breed: Gir
```

📈 Model Performance
Accuracy: ~90–95%
Evaluation Metrics:
Accuracy Score
Confusion Matrix
Classification Report

🚀 Future Enhancements
Mobile app integration
Cloud deployment
Breed health prediction

👨‍💻 Author
Ishu Vadwani
B.Tech CSE – Bennett University
AI & Machine Learning Enthusiast



