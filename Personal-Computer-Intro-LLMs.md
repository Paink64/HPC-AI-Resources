# 🧑‍💻 Introduction to Large Language Models (LLMs) 🤖

Welcome to the workshop! In this session, we’ll learn about **Large Language Models (LLMs)**, which help computers understand and create human-like text. We’ll also set up a simple computer environment using Docker to run our code.

---

## 🛠️ **What You Need** 
- **Docker** installed on your computer.
- Basic knowledge of Python (don’t worry if you don’t, we’ll guide you through it).

---

## 🚀 **What We’ll Do** 
- Learn what **LLMs** are.
- Set up a Docker container with all the tools we need.
- Run some simple Python code to generate text with an LLM.

---

## 📝 **Step-by-Step Guide**

### 1. **What Are Large Language Models (LLMs)?**
   - **LLMs** are models that help computers understand and create human language, like how Siri or Google Assistant work.
   - They can do tasks like answering questions, writing stories, or even translating text!

---

### 2. **Setting Up Docker** 
   - **Docker** is a tool that makes it easy to run programs without installing them on your computer. We’ll use it to load everything we need for this workshop.
   
   **Steps to set up:**
   1. **Pull the Docker Image**:
      - Run this in your terminal to download the Docker image:
        ```bash
        docker pull huggingface/transformers
        ```
   2. **Run the Docker Container**:
      - After the image is downloaded, run this command to open the container:
        ```bash
        docker run -it huggingface/transformers bash
        ```

---

### 3. **Running Your First Python Code** 
   - Now that the Docker container is running, let’s load a model and generate some text!

   **Steps:**
   1. **Import the Libraries**:
      - Inside the Docker container, type this in Python:
        ```python
        from transformers import GPT2LMHeadModel, GPT2Tokenizer
        ```
   2. **Load the Model**:
      - Next, load the GPT-2 model and tokenizer:
        ```python
        model = GPT2LMHeadModel.from_pretrained("gpt2")
        tokenizer = GPT2Tokenizer.from_pretrained("gpt2")
        ```
   3. **Generate Text**:
      - Now, let’s give it a sentence, and the model will finish it for us:
        ```python
        input_text = "Once upon a time, in a faraway land, there was a dragon."
        input_ids = tokenizer.encode(input_text, return_tensors="pt")
        output = model.generate(input_ids, max_length=100)
        generated_text = tokenizer.decode(output[0], skip_special_tokens=True)
        print(generated_text)
        ```

---

### 4. **What Happened?**
   - The model will finish the story for you! This is how LLMs can generate human-like text.

---

## 📚 **Next Steps**
Now that you've set up your environment and tried generating text, you can try other models and explore how LLMs work with different tasks like answering questions or translating languages.

---

## 🤔 **Questions?**
Feel free to ask if you need help! Let’s have fun learning with AI! 🎉
