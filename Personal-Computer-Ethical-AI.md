# 🚀✨ Ethical AI & Future Trends Workshop 🌍🤖  

## 🎯 **Goal**  

Artificial Intelligence (AI) is everywhere—from **self-driving cars** to **job hiring**, **TikTok recommendations**, and even **medical diagnoses**. But **is AI always fair?**  

## 📌 **What You Will Learn** 🧠💡  

✅ **What is Ethical AI?** 
 
✅ **How does AI bias happen?**  

✅ **How can we fix unfair AI?** 
 
✅ **Will AI take over jobs, or will it help humans?**  

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

### 🚀 **Step 1: Open [Google Colab](https://colab.research.google.com/)** 
 
1️⃣ **Open your browser** and go to **[Google Colab](https://colab.research.google.com/)**.  

2️⃣ **Click** **+ New notebook** to create a new notebook.  

---

### 📌 **Step 2: Create a Biased AI Model**  

Now, let’s **train an AI model** and **see how bias affects its decisions**. 
 
[ChatGPT Code Conversation](https://chatgpt.com/share/67cfae07-0420-8008-a914-44279572f647)

```python
import pandas as pd

# Create a small dataset with gender and hiring outcome
data = {'Gender': ['Male', 'Male', 'Male', 'Male', 'Female', 'Female'],
        'Hired': [1, 1, 1, 1, 0, 0]}  # 1 = Hired, 0 = Rejected

df = pd.DataFrame(data)
print(df)
```
:one: Click Run :arrow_forward: and check the output!
 
Notice that **all males were hired**, and **all females were rejected**—the dataset is **biased**!  

---

### 📌 **Step 3: Train the Biased AI Model**  

[ChatGPT Code Conversation](https://chatgpt.com/share/67cfae6e-69e0-8008-8714-9dfb0317e581)

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

:one: Click Run :arrow_forward: and see the results! 
 
The AI **continues to reject females** because it learned from **biased data**.  

---

### 📌 **Step 4: Fix the AI Bias**  

Now, let’s **train AI with fair data** by **balancing the dataset**.  

[ChatGPT Code Conversation](https://chatgpt.com/share/67cfaeec-a898-8008-9844-43f62aa835bf)

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

:one: Click Run :arrow_forward: again

Now, AI should **treat males and females fairly!** 🎉  

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

You now understand:  

✅ AI **learns from past data**, so it can **inherit bias**. 
 
✅ **Bad data → Bad AI** ❌, **Good data → Fair AI** ✅.  

✅ AI will **not replace humans**, but **help us** do tasks better.  

📌 **Next Workshop**: 🎥 Watch a documentary on **AI Ethics**.  
 
🔗 **Additional AI Resources** 📚

- [Responsible AI by Microsoft](https://learn.microsoft.com/en-us/training/modules/embrace-responsible-ai-principles-practices/)
- [Secure AI services by Microsoft](https://learn.microsoft.com/en-us/training/modules/secure-ai-services/)

🚀 Keep exploring AI and **stay curious!**  

🎉 **That’s how we build Ethical AI for the Future!** 🚀