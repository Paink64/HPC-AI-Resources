# 🚀✨ PC: Introduction to Large Language Models (LLMs) ✨🚀

## 🎯 Goal
🤖 Understand what a Large Language Model (LLM) is and how it can be used for text generation, question answering, and more, using Python. No prior experience needed—just bring your curiosity! 🚀

---

## 📌 What You Will Learn 🧠💡
✅ What is a Large Language Model (LLM)?  
✅ How do LLMs work?  
✅ How to use pre-trained LLMs for text generation  
✅ How to use LLMs for answering questions  
✅ Hands-on coding with Google Colab  
✅ Basics of Hugging Face library for LLMs  

---

## 🤖 1. What is a Large Language Model (LLM)?
### 🧠 Understanding LLMs in Simple Terms
A **Large Language Model (LLM)** is a type of AI model that can understand and generate human-like text. It learns by analyzing huge amounts of text data, recognizing patterns, and predicting words based on context.

### 📌 Real-World Examples:
- ✅ Chatbots like Siri, Google Assistant, ChatGPT 🗣️  
- ✅ AI-powered writing assistants (Grammarly, Jasper AI) ✍️  
- ✅ Search engines predicting your queries 🔍  
- ✅ AI-generated stories and essays 📖  

---

## 🔥 2. How do LLMs work?
### 🛠️ How Do LLMs Generate Text?
- #### 📚 Training on Large Datasets  
  - LLMs are trained on **billions of words** from books, articles, and websites.

- #### 🔍 Predicting the Next Word  
  - When given a sentence, the model predicts the most likely next word.

- #### ✍️ Generating Coherent Responses  
  - By repeating this process, it forms complete sentences that make sense.

📌 **Example: How AI predicts text**   
- Input: "The sky is"    
- Predicted Output: "blue because of the way light scatters."

💡 *Quick Thought: Where else do you see AI predicting text? Jot down your ideas! 📝*

---

## 🔧 3. How to use pre-trained LLMs for text generation

## 💻 Step 1: Open Google Colab
1️⃣ Open [Google Colab](https://colab.research.google.com/)  
2️⃣ Click **+ New Notebook**  

## 📚 Step 2: Import Required Libraries
### **➕🐍 Add a New Code Cell**         
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67caf38c-8f0c-8004-9dff-1b2441a14b83)

```python
# Import pipeline from Hugging Face for easy LLM use
from transformers import pipeline  
```
3️⃣ **Click Run (▶) and check the output!** 

✅ Libraries imported successfully! You’re now ready to use the Hugging Face pipeline. 🚀🎉


## 🧠 Step 3: Load a Pre-Trained LLM
💡 We will use GPT-2, a popular model that generates human-like text.  
### **➕🐍 Add a New Code Cell**           
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67caf3f2-c6ac-8004-a5d5-a34e8a75b783)

```python
# Define the task as text generation
task = 'text-generation'

# Specify the model to be used
model_name = 'gpt2'

# Load the pre-trained model for text generation
generator = pipeline(task, model=model_name)
```
3️⃣ **Click Run (▶) and check the output!** 

✅ Pre-trained LLM loaded successfully! You're now ready to generate text using GPT-2. 🧠🚀🎉

## 📝 Step 4: Generate Text Using the LLM    
### **➕🐍 Add a New Code Cell**         
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67caf460-e874-8004-a418-040789cda3cf)

```python
# Define the input text prompt
prompt_text = "Once upon a time, in a faraway land, there was a magical forest."

# Set the maximum length for generated text
max_length = 100

# Generate text based on the given prompt
output = generator(prompt_text, max_length=max_length)

# Extract and print the generated text
generated_text = output[0]['generated_text']
print(generated_text)
```
3️⃣ **Click Run (▶) and check the output!** 

✅ Text generated successfully! You should now see a creative continuation of your prompt. 📝✨🎉

🎯 Challenge: Try changing the prompt to something funny or mysterious!🔥<br>
💡 Extra Tip: Edit the prompt_text = "..." line and try your own creative ideas. For example, start with “In a haunted bakery…” or “The cat who ruled the internet…”

---
## 🤖 4. How to use LLMs for answering questions
💡 LLMs can also answer questions based on a given context!  
### **➕🐍 Add a New Code Cell**           
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell. 
 
🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67caf4c1-cfe4-8004-b55c-20ed9f92f25c)

```python
# Define the task as question answering
task_qa = 'question-answering'

# Specify the model to be used
qa_model_name = 'distilbert-base-uncased-distilled-squad'

# Load the pre-trained model for question answering
qa_pipeline = pipeline(task_qa, model=qa_model_name)

# Define the context for the question
context_text = """
Hugging Face is a company that provides tools and models for natural language processing.
Their library, Transformers, is widely used in AI.
"""

# Define the question
question_text = "What does Hugging Face do?"

# Use the model to answer the question based on the context
result = qa_pipeline(question=question_text, context=context_text)

# Extract and print the answer
answer_text = result['answer']
print("Answer:", answer_text)
```
3️⃣ **Click Run (▶) and check the output!** 

✅ Question answered successfully! You should now see the model's response based on the given context. 🤖🎉

---

## 🎯 5. Wrap-Up & Next Steps
🎉 Congratulations! Today you learned how to:

- ✅ Use LLMs for text generation ✍️
- ✅ Use LLMs for question answering 💬
- ✅ Work with Hugging Face models 🤖

🚀 **Next Workshop:** [📚 LLM + RAG (AI-Powered Search)](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/personal-computer-llm-rag)

### 🔗 Additional AI Resources 📚

- [Google Colab Guide](https://colab.research.google.com/)     
- [Python Introduction](https://www.w3schools.com/python/python_intro.asp) (Use only the two green buttons “Previous” and “Next” to navigate the tutorial and avoid ads.)<br> 
- [AI for Beginners (Microsoft)](https://microsoft.github.io/AI-For-Beginners/?id=other-curricula)
- [What is LLM (Large Language Model)?](https://aws.amazon.com/what-is/large-language-model/)


🎉 Keep learning AI, and see you at the next workshop! 🚀

---

### 📝 Workshop Feedback Survey 

Thanks for completing this workshop!🎆

We'd love to hear what you think so we can make future workshops even better. 💡

📌 **[Survey link]**

---
