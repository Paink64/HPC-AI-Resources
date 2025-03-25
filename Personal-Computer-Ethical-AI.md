# 🚀✨ PC: Ethical AI & Future Trends Workshop 🌍🤖  

## 🎯 **Goal**  

🤖Artificial Intelligence (AI) is everywhere—from **self-driving cars** to **job hiring**, **TikTok recommendations**, and even **medical diagnoses**. But **is AI always fair?**  

---

## 📌 **What You Will Learn** 🧠💡  

✅ **What is Ethical AI?**<br>
✅ **How does AI bias happen?** <br> 
✅ **How can we fix unfair AI?** <br>
✅ **Will AI take over jobs, or will it help humans?**  <br>

By the end of this session, you'll know how to **detect bias in AI**, **make AI more ethical**, and **understand the future of AI**! 🚀  

---
## 🖼️ 1. Understanding Ethical AI 

**Ethical AI** means AI that is **fair, transparent, and does not harm people**. It should treat everyone equally and not **make unfair decisions based on gender, race, or background**.  

### 🔍 **Example: AI in Hiring 👨‍💼👩‍💼**  
- A company uses **AI** to **screen job applications**. But the AI was trained on **past hiring data**, where the company mostly hired men.  
- Now, the AI **unfairly rejects female applicants** because it learned from biased data.  

❌ **Problem:** The AI is **unethical** because it reinforces discrimination.  
✅ **Solution:** 

- Train the AI with **diverse** data, including men and women applicants.  
- Make AI **explain** why it rejects someone.  
- Have **humans** double-check AI decisions.  

---

## 📚 2. Hands-on Experiment - Detecting AI Bias in Hiring

## 🚀 **Step 1: Open [Google Colab](https://colab.research.google.com/)** 
 
1️⃣ **Open your browser** and go to **[Google Colab](https://colab.research.google.com/)**.  

2️⃣ **Click** **+ New notebook** to create a new notebook.  


## 📌 **Step 2: Create a Biased AI Model**  

### **➕🐍 Add a New Code Cell**           
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
 
🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67d31f37-7644-8008-905c-8cd700608189)

```python
import pandas as pd

# Create a small dataset with gender and hiring outcome
data = {'Gender': ['Male', 'Male', 'Male', 'Male', 'Female', 'Female'],
        'Hired': [1, 1, 1, 1, 0, 0]}  # 1 = Hired, 0 = Rejected

df = pd.DataFrame(data)
print(df)
```

3️⃣ **Click Run (▶) and check the output!** 

✅ Notice that all males were hired, and all females were rejected—the dataset is biased!

🎯 Challenge: Make your own *intentionally biased* dataset. Try adding only one female and make her always rejected. Or create a world where AI only hires people named "Zorg." 🤖🚫

💡 Extra Tip: Edit the `data = {...}` section and see how badly AI can behave when trained on unfair data!


## 📌 **Step 3: Train the Biased AI Model**  

### **➕🐍 Add a New Code Cell**           
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67d31f5a-6238-8008-99db-10aa00f80011)

```python
from sklearn.tree import DecisionTreeClassifier

# Convert gender to numbers (Male = 0, Female = 1)
df['Gender'] = df['Gender'].map({'Male': 0, 'Female': 1})

# Split data into features (X) and target (y)
X = df[['Gender']]  # Gender is the only feature
y = df['Hired']

# Train a simple decision tree model
model = DecisionTreeClassifier()
model.fit(X, y)

# Test the model: Will a new male and female be hired?
test_data = pd.DataFrame({'Gender': [0, 1]})  # 0 = Male, 1 = Female
predictions = model.predict(test_data)

# Display results
for i, gender in enumerate(['Male', 'Female']):
    print(f"AI Prediction for {gender}: {'Hired' if predictions[i] == 1 else 'Rejected'}")

```

3️⃣ **Click Run (▶) and check the output!** 

✅ The AI continues to reject females because it learned from biased data.

## 📌 **Step 4: Fix the AI Bias**  

Now, let’s **train AI with fair data** by **balancing the dataset**. 

### **➕🐍 Add a New Code Cell**  

1️⃣ Click **+ Code** in the top left to add a new code cell.        
2️⃣ Copy and paste the following into the new code cell.             

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67d31f71-a3b0-8008-90d9-ec15fae52e3a)

```python
# Create a fair dataset (equal male & female hiring)
fair_data = {'Gender': ['Male', 'Male', 'Male', 'Female', 'Female', 'Female'],
             'Hired': [1, 1, 0, 1, 1, 0]}  

df_fair = pd.DataFrame(fair_data)
df_fair['Gender'] = df_fair['Gender'].map({'Male': 0, 'Female': 1})

# Train AI on fair data
X_fair = df_fair[['Gender']]
y_fair = df_fair['Hired']
model.fit(X_fair, y_fair)

# Test again
fair_predictions = model.predict(test_data)

for i, gender in enumerate(['Male', 'Female']):
    print(f"AI Prediction for {gender} (Fair AI): {'Hired' if fair_predictions[i] == 1 else 'Rejected'}")
```

3️⃣ **Click Run (▶) and check the output!** 

✅ Now, AI should **treat males and females fairly!** 🎉  

---

## 🔍 3. How Does AI Become Unfair? 

AI **learns from data**, and if the data is **biased**, AI will also be **biased**!  

### 🔍 **Example: AI in Facial Recognition 😃📸**  
- AI **recognizes faces** based on thousands of photos.  
- If it is **only trained on photos of white people**, it may **struggle** to recognize **Black or Asian faces**.  
- This can **cause problems**—for example, **wrongfully identifying** someone in a crime case!  

✅ **Solution:** Train AI with **diverse** photos of people **from different backgrounds**.  

---

## 🚀 4: Future of AI - Good or Bad?

AI is **getting better every day**, but will it **replace humans**?  

### **Thought Experiment: Will AI Take Our Jobs?**  
🤔 **Ask students:**  
- What jobs can AI **help** with?  
- What jobs need **human creativity and emotions**?  

### **Mini Activity:**  
- Divide students into two groups:  
  - **Team AI:** List jobs AI **can do better** (e.g., data entry, self-driving cars).  
  - **Team Humans:** List jobs that need **human skills** (e.g., art, teaching, therapy).  

🚀 **Conclusion:**  
AI **won't replace humans**, but **it will change jobs**. We must **train AI fairly** and **learn to work with AI!**  

---

## 🎯 5. Wrap-Up & Next Steps

🎉You now understand:  

✅ AI **learns from past data**, so it can **inherit bias**.<br>
✅ **Bad data → Bad AI** ❌, **Good data → Fair AI** ✅.<br>
✅ AI will **not replace humans**, but **help us** do tasks better.<br>

📌 **Next Workshop**: [🚀 Intro to HPC, AI & Jupyter](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/hpc-intro)
 
### 🔗 **Additional AI Resources** 📚   

- [Google Colab: Getting Started](https://colab.research.google.com/#scrollTo=GJBs_flRovLc)     
- [Python Introduction](https://www.w3schools.com/python/python_intro.asp) (Use only the two green buttons “Previous” and “Next” to navigate the tutorial and avoid ads.)<br>   
- [AI for Beginners (Microsoft)](https://microsoft.github.io/AI-For-Beginners/?id=other-curricula)
- [Responsible AI by Microsoft](https://learn.microsoft.com/en-us/training/modules/embrace-responsible-ai-principles-practices/)

🚀 Keep exploring AI and **stay curious!**  

🎉 **That’s how we build Ethical AI for the Future!** 🚀

---

### 📝 Workshop Feedback Survey 

Thanks for completing this workshop!🎆

We'd love to hear what you think so we can make future workshops even better. 💡

📌 **[Survey link]**

---
