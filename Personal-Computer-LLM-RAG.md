# 🚀✨ **Workshop: Introduction to Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG)** ✨🚀  

---

## 🎯 **Goal**  
🤖 **Understand the basics of Large Language Models (LLMs)** and how **Retrieval-Augmented Generation (RAG)** enhances LLMs for tasks like text generation and answering complex queries. You will learn to use LLMs in combination with a retrieval system to improve performance. No prior experience needed—just bring your curiosity! 🚀  

---

## 📌 **What You Will Learn** 🧠💡  
✅ What are **Large Language Models (LLMs)**?  
✅ What is **Retrieval-Augmented Generation (RAG)**?  
✅ Setting Up LLM and RAG for Text Generation  
✅ Running LLM and RAG for Text Generation   
✅ How to use **RAG** with **Hugging Face** to enhance text generation  
✅ Hands-on coding with **Google Colab** and **Hugging Face**  

---

## 🤖 **1. What is a Large Language Model (LLM)?**  
### 🧠 Understanding LLMs in Simple Terms  
A **Large Language Model (LLM)** is a type of AI model that can understand and generate human-like text. It learns by analyzing massive amounts of text data, recognizing patterns, and predicting words based on context.

### 📌 Real-World Examples:  
- ✅ Chatbots like Siri, Google Assistant, ChatGPT 🗣️  
- ✅ AI-powered writing assistants (Grammarly, Jasper AI) ✍️  
- ✅ Search engines predicting your queries 🔍  
- ✅ AI-generated stories and essays 📖  

---

## 🔧 **2. What is Retrieval-Augmented Generation (RAG)?**  
### 🛠️ How Does RAG Work?  
RAG enhances LLMs by integrating **retrieval** and **generation** to provide more accurate responses. Instead of relying solely on pre-trained knowledge, it fetches relevant information from external databases before generating a response.

#### 📚 Steps in RAG:  
1️⃣ **Retrieval:** The model searches for relevant documents from a knowledge base.  
2️⃣ **Augmentation:** The retrieved data is passed as context to the LLM.  
3️⃣ **Generation:** The LLM generates a response based on the retrieved information. 

📌 **Example:**  
- If you ask about a recent scientific breakthrough, RAG can retrieve research papers or trusted sources before forming an answer.  

---

## 🔧 **3. Setting Up LLM and RAG for Text Generation**

### 🚀 **Step 1: Open [Google Colab](https://colab.research.google.com/)**

1️⃣ Open your browser and go to **[Google Colab](https://colab.research.google.com/)**.\
2️⃣ Click **+ New notebook** to begin.

### 🛠️ **Step 2: Set Up Hugging Face Account and Access Token**

1️⃣ **Sign up on Hugging Face**: Go to [Hugging Face Sign-Up](https://huggingface.co/join) and create a free account.\
2️⃣ **Generate an Access Token**:

- Click on your profile icon and go to **[Your Account Settings](https://huggingface.co/settings/tokens)**.
- Scroll down to **Access Tokens** and click **New Token**.
- Give it a name (e.g., "Colab Access") and select **Read** access.
- Click **Generate Token** and copy the token.

### 📚 **Step 3: Login in Colab with the Token**

1️⃣ Open a new cell in Google Colab and run the following code:

<a href="https://chatgpt.com/share/67cafa63-35d0-8004-bfdc-f36ffb25ae57" target="_blank">ChatGPT explanation for the code</a>

```python
# Import Hugging Face login module
from huggingface_hub import notebook_login  

# Trigger login prompt
notebook_login()  
```

2️⃣ When prompted, paste the token you copied earlier.\
3️⃣ **Verify Authentication**:\
Run the following code to check if authentication is successful:   
<a href="https://chatgpt.com/share/67caface-5ed8-8004-a60c-5132ec7113bd" target="_blank">ChatGPT explanation for the code</a>

```python
# Check if authentication is successful
!huggingface-cli whoami  
```

4️⃣ If it prints your Hugging Face username, the setup is complete!

---

## 🔧 **4. Running LLM and RAG for Text Generation**
### 📚 **Step 1: Install and Import Required Libraries**

Before importing the libraries, install the necessary dependencies by running the following command:

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
<a href="https://chatgpt.com/share/67cafb46-9940-8004-8618-4f0cb0dfd5aa" target="_blank">ChatGPT explanation for the code</a>

```python
# Install Hugging Face Transformers, FAISS, and datasets
!pip install transformers faiss-cpu datasets  
```

3️⃣ Click **Run** (▶) to install the required packages.

These dependencies are not pre-loaded in google colab and need to be explicitly installed. 

Then, import the necessary libraries:

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
<a href="https://chatgpt.com/share/67cafbb3-4074-8004-8fd6-58b28b1cdd4d" target="_blank">ChatGPT explanation for the code</a>

```python
# Import required libraries
from transformers import pipeline, RagTokenizer, RagRetriever, RagSequenceForGeneration  
import faiss  
```

3️⃣ Click **Run** (▶) to import the libraries.

### 🧠 **Step 2: Load a Pre-Trained RAG Model**

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
<a href="https://chatgpt.com/share/67cafc54-f3c0-8004-a121-af4a0faa0f5c" target="_blank">ChatGPT explanation for the code</a>

```python
# Define tokenizer model name
tokenizer_model = "facebook/rag-sequence-nq"  

# Load the tokenizer
tokenizer = RagTokenizer.from_pretrained(tokenizer_model)  

# Define the text-generation model name
generation_model = "gpt2"  

# Load the text-generation model
model = pipeline("text-generation", model=generation_model)  
```

3️⃣ Click **Run** (▶) to load the pre-trained RAG model.

📌 **Note:** When running this step, you may see a prompt asking:

```
Do you wish to run the custom code? [y/N]
```

Type **'y'** and press **Enter** to allow the model to load properly. This is required for some Hugging Face models.



### 📚 **Step 3: Prepare a Query and Retrieve Information**

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
<a href="https://chatgpt.com/share/67cafcc4-b258-8004-9f15-5b1e7d1d9419" target="_blank">ChatGPT explanation for the code</a>

```python
# Define user query
query = "What is the process of photosynthesis?"  

# Tokenize query
input_dict = tokenizer.prepare_seq2seq_batch(query, return_tensors="pt")  

# Retrieval is disabled as retriever is removed
retrieved_docs = None  
```

3️⃣ Click **Run** (▶) to retrieve documents related to the query.

### ✨ **Step 4: Generate a Response Using the Retrieved Documents**

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
<a href="https://chatgpt.com/share/67cafd2e-39b4-8004-9c52-ba1ac77e845f" target="_blank">ChatGPT explanation for the code</a>

```python
# Generate response based on retrieved documents
output = model(query, max_length=100, truncation=True)  

# Extract generated text
generated_text = output[0]['generated_text']  

# Print generated response
print("Generated Answer:", generated_text)  
```

3️⃣ Click **Run** (▶) to generate a response based on the retrieved documents.

📌 **Expected Output:**

- The model should generate a relevant and coherent answer about the process of photosynthesis based on the retrieved information.

---


🏆 Exercise: Try It Yourself! 🎯

Now that you have learned how to retrieve and generate responses using RAG, try this challenge on your own!

1️⃣ Modify the query to ask about a different topic, such as climate change, machine learning, or the history of AI.    
2️⃣ Run the code and analyze how the retrieved documents influence the generated response.    
3️⃣ Experiment by changing the model parameters (e.g., max_length) to see how the output changes.

📌 Bonus Challenge: Try integrating a different retrieval dataset from Hugging Face and see how it impacts the performance! 🚀

---

## 🎯 **5. Wrap-Up & Next Steps**  
🎉 Congratulations! You learned how to:  
✅ Use a **Large Language Model (LLM)** for text generation.  
✅ Implement **Retrieval-Augmented Generation (RAG)** to improve text generation.  
✅ Use **Hugging Face** for easy access to pre-trained models and retrieval systems.  

🚀 **Next Workshop:** [🔍 Ethical AI & Future Trends](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/personal-computer-ethical-ai)  

🔗 Additional AI Resources 📚

- [Google Colab Guide](https://colab.research.google.com/)
- [What is retrieval-augmented generation (RAG)?](https://azure.microsoft.com/en-us/resources/cloud-computing-dictionary/what-is-retrieval-augmented-generation-rag)
- [AWS: What is Retrieval-Augmented Generation (RAG)?](https://aws.amazon.com/what-is/retrieval-augmented-generation/)


🎉 Keep learning AI, and see you at the next workshop! 🚀