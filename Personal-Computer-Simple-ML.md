# 🚀✨ **Workshop 3: 🤖 Simple ML Model!** ✨🚀  

## 🎯 **Goal**  
🎉 Welcome, future AI builder! In this hands-on workshop, you'll learn how to **build, train, and use a simple Machine Learning (ML) model** using Python. No prior experience is needed—just curiosity and excitement! 🤖📊  

---

## 📌 **What You Will Learn** 🧠💡  
✅ What a Machine Learning (ML) model is 🏗️  
✅ What **Linear Regression** is and how it works 📈  
✅ How to prepare data for ML 📂  
✅ How to train a **simple ML model** 🤖  
✅ How to make predictions with the model 🔮  
✅ How to visualize ML predictions 🎨📊  

---

## 🤖 **1. What is a Machine Learning (ML) Model?**  

### **ML = Computers that Learn!** 💡  
A **Machine Learning (ML) model** is a program that **learns from data** to make predictions. Instead of being manually programmed with rules, ML models **find patterns** in data and use them to make future decisions.  

💡 **Where is ML used?**  
- 🛍️ **Amazon & Shopify** → Suggests products based on your shopping history  
- 📺 **Netflix & YouTube** → Recommends movies & videos you might like  
- 📸 **Face Unlock** → Recognizes your face using AI  

💡 **Think:** Can you think of other places you see ML in action? 🤔  

---

## 📈 **2. What is Linear Regression?**  
Linear Regression helps us **find patterns** in data and **make predictions** by drawing a straight line through the data points. 📊  

🔍 **Example:** Imagine tracking students’ ages and their test scores:  
- A **20-year-old** scores **75 points**  
- A **22-year-old** scores **78 points**  
- A **24-year-old** scores **80 points**  

📌 **Pattern:** As **age increases, scores increase**.  
📌 **Linear Regression** finds the best rule (line) to predict new scores.  

### 🎨 **Visual Example:**  
- 🔵 **Dots** = Real student scores from past data  
- 📍📍📍 **Red Line** = The best prediction rule  

📌 **Super Simple Math (No Formulas!):**  
- If each extra year **adds** about **2 points** to the score…  
- Then a **25-year-old** might score **82 points** (based on the pattern).  

💡 **That’s Linear Regression!** 🎉  

---

## 🔍 **3. Hands-on: Building a Simple ML Model**  

### 🚀 **Step 1: Open Google Colab**  
1️⃣ Open your browser and go to **[Google Colab](https://colab.research.google.com/)**.  
2️⃣ Click **+ New notebook**.  

### 💾 **Step 2: Load and Explore the Dataset**  
### **➕🐍 Add a New Code Cell**         
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67c84802-3138-8002-81a4-b7c3466bfeb8/)**
```python
# Import Pandas for data handling
import pandas as pd  

# Create a small dataset
data = pd.DataFrame({
    # Input: Age of students
    'Age': [18, 20, 22, 24, 26, 28, 30],
    # Output: Test scores
    'Score': [70, 75, 78, 80, 85, 87, 90]  
})

# Display the dataset
data
```

3️⃣ **Click Run** (▶) and check the dataset!  

✅ You should now see a table with student ages and scores! The dataset is now ready for exploration. 🎉

---

## 🤖 **4. Training a Simple ML Model**  

### **➕🐍 Add a New Code Cell**  
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67c8c1a6-ec0c-8002-9e5b-8833d632e572/)**
```python
# Import ML model
from sklearn.linear_model import LinearRegression  

# Feature (Input: Age) converted to array
X = data[['Age']].values  
# Target (Output: Score) converted to array
y = data['Score'].values  

# Create the model
model = LinearRegression()  
# Train the model
model.fit(X, y)  
```

3️⃣ Click **Run** (▶) to train the ML model!  

✅ Model trained successfully! Your ML model is now ready to make predictions. 🎉

---

## 🔮 **5. Making Predictions with ML**  

### **➕🐍 Add a New Code Cell**  
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67c8c20b-00c0-8002-accf-731a62f32f0e/)**
```python
# Predict score for age 25 
predicted_score = model.predict([[25]]) 
# Print prediction
print("Predicted Score for Age 25:", predicted_score[0])
```

3️⃣ Click **Run** (▶) to see the prediction!  

✅ You should now see the predicted score for age 25! 🎉

---

## 🎨 **6. Visualizing ML Predictions**  

### **➕🐍 Add a New Code Cell**  
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67c8c282-b3cc-8002-bc4d-f13e72845ad4/)**
```python
# Import plotting library 
import matplotlib.pyplot as plt 
# Import numpy for calculations 
import numpy as np 

# Generate a smooth range of age values from 18 to 30 (100 points in between)
age_range = np.linspace(18, 30, 100).reshape(-1, 1)  # Reshape to match model input format

# Predict scores for these age values using the trained model
predicted_scores = model.predict(age_range)   

# Create a scatter plot of the actual data (blue dots)
plt.scatter(data['Age'], data['Score'], color='blue', label='Actual Data')

# Draw the prediction line (red) showing how the model predicts scores
plt.plot(age_range, predicted_scores, color='red', label='Prediction Line')

# Label the x-axis as "Age"
plt.xlabel('Age')

# Label the y-axis as "Score"
plt.ylabel('Score')

# Set a title for the graph
plt.title('ML Model: Predicting Scores Based on Age')

# Add a legend to explain the blue dots and red line
plt.legend()

# Display the graph
plt.show()
```

3️⃣ Click **Run** (▶) and check the graph! 🎨📊  

✅ You should now see a graph with actual data points and a prediction line! 🎉

🎯 **Challenge**
* Go back to the first code cell and make changes to the dataset.
* **Rerun all the cells** (▶) and observe how the results evolve!
---

## 🎯 **7. Wrap-Up & Next Steps**

🎉 Great job! You just built, trained, and tested your first Machine Learning model! Here’s what we covered:

✅ Machine Learning helps computers learn from data 🤖📊  
✅ Linear Regression finds patterns and predicts outcomes 📈  
✅ We trained a simple ML model to predict test scores based on age 🏆  
✅ We visualized predictions with a graph 🎨📊  

🚀 **Next Workshop:** [🧠 Deep Neural Network (DNN)](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/personal-computer-dnn)  

### 🔗 **Additional AI Resources** 📚   

- [Google Colab Guide](https://colab.research.google.com/#scrollTo=GJBs_flRovLc)     
- [Python Introduction](https://www.w3schools.com/python/python_intro.asp)        
⚠ **Warning:** Please use only the two green buttons (“Previous” and “Next”) to navigate the tutorial. Avoid clicking on other links to prevent being redirected to ads.
- [Google Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course/)   
- [Microsoft Learn - Introduction to machine learning](https://learn.microsoft.com/en-us/training/modules/introduction-to-machine-learning/)

🎉 You did it! Keep exploring AI, and see you at the next workshop! 🚀