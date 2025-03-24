# 🚀✨ HPC: Introduction of Large Language Models (LLMs) ✨🚀

## 🎯 Goal
🤖 Learn how to efficiently run Large Language Models (LLMs) on **High-Performance Computing (HPC) systems**, leveraging **JupyterLab** for scalable text generation and question-answering tasks. Whether you're new to LLMs or HPC, this hands-on workshop will guide you through the essentials! 🚀

---

## 📌 What You Will Learn 🧠💡
✅ Why use **HPC** for running LLMs? 🚀  
✅ How to access and navigate **CSUSB HPC & JupyterLab** 🖥️  
✅ Install essential Libraries and Kaggle dataset ✍️  
✅ How to run **pre-trained LLMs on HPC** for faster processing ⏩  
✅ Using **Hugging Face Transformers** for text generation and QA  
✅ Working with a **Kaggle dataset** for real-world applications 📊  

---

## 🏆 1. Why use **HPC** for running LLMs? 🚀
### 🚀 The Power of High-Performance Computing (HPC)
LLMs are computationally expensive! Running them on personal devices can be **slow**, **memory-intensive**, and sometimes **impossible**. HPC systems solve this by:
- **Parallelizing workloads** for faster execution ⚡
- **Providing GPU acceleration** to handle large-scale deep learning models 🎮
- **Handling large datasets** efficiently 📊

💡 *Think: What AI tasks can benefit from HPC? Jot down your ideas! 📝*

---

## 🔥 2. How to access and navigate **CSUSB HPC & JupyterLab** 🖥️

Once you sign in to the CSUSB HPC portal, follow these steps to configure and launch your server:

### Step 1: Access the HPC JupyterHub   
1️⃣ Log into [CSUSB HPC Portal](https://csusb-hpc.nrp-nautilus.io/) using your school credentials.   
2️⃣ Click CI Logon and authenticate.

### Step 2: Configure Your Server   
1️⃣ Click Start My Server or Launch Server if prompted.   
2️⃣ Under Advanced Options, adjust the following:   

- GPUs: 2
- GPU Type: Leave as Any
- Cores: 4 (default)
- RAM: 16 GB (default)
 
3️⃣ Under Image, select:   
✅ Stack Datascience   
### Step 3: Start Your Server   
1️⃣ Scroll down and click Start to launch the server.   
2️⃣ Wait for the server to initialize. Once it is ready, JupyterHub will open in a new tab.

✅ Now your server is ready for the workshop! 🚀

---

## 🔧 3. Install essential Libraries and Kaggle dataset ✍️  

### **➕🐍 Add a New Code Cell**  
  
1️⃣ Click **+ Code** in Jupyter Notebook to add a new code cell.  
2️⃣ Copy and paste the following code:  
    
🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67cb1712-6940-8004-9dd6-df6e5b2542c1)
```bash
# Install essential Python libraries for data manipulation and analysis
pip install --user pandas  

# Install seaborn for data visualization, useful for plotting and analyzing trends
pip install --user seaborn  

# Install matplotlib for creating static, animated, and interactive visualizations
pip install --user matplotlib  

# Install Kaggle API to download datasets directly from Kaggle into the HPC environment
pip install --user kaggle  

# Temporarily add Kaggle to system PATH
export PATH=~/.local/bin:$PATH  

# Permanently add Kaggle to system PATH
echo 'export PATH=~/.local/bin:$PATH' >> ~/.bashrc  

# Apply changes immediately
source ~/.bashrc  

# Create a new directory for dataset storage
mkdir -p ~/playstore_data  

# Navigate into the dataset directory
cd ~/playstore_data  

# Download the Google Playstore dataset from Kaggle
kaggle datasets download -d gauthamp10/google-playstore-apps  

# Unzip the downloaded dataset
unzip google-playstore-apps.zip  

# List extracted files to confirm successful download
ls -lh  
```

3️⃣ **Click Run (▶) and check the output!** 

✅ **Success!** Dataset downloaded and ready for analysis. 🎉

---

## 🤖 4. How to run **pre-trained LLMs on HPC** for faster processing ⏩ 

## 🏗️ Step 1: Load Dataset into Jupyter Notebook

1️⃣ In **JupyterLab**, open a **new notebook** (Python 3 Kernel).  
2️⃣ In the first code cell, run:  
  
🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67cb1794-47c4-8004-86e4-4231aa963ed4)

```python
# Import Pandas library
import pandas as pd  

# Define dataset file path
dataset_path = "~/playstore_data/Google-Playstore.csv"  

# Load dataset into a Pandas DataFrame
playstore_df = pd.read_csv(dataset_path)  

# Display the first few rows of the dataset
print("Dataset Preview:")  
print(playstore_df.head())  

# Extract column names for reference
column_names = playstore_df.columns.tolist()  

# Print column names
print("\nColumn Names:", column_names)  
```
3️⃣ **Click Run (▶) and check the output!** 
 
✅ **Success!** Dataset is now loaded into your notebook and ready for analysis.

## ✍️ Step 2: Using **Hugging Face Transformers** for text generation and QA  
This step demonstrates how an LLM can generate text based on a given prompt.

### **➕🐍 Add a New Code Cell**    
1️⃣ Click **+ Code** in Jupyter Notebook to add a new code cell.  
2️⃣ Copy and paste the following code:  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67cb17fa-9d94-8004-82cf-28100b37fbdb)

3️⃣ import the necessary library:
```python
# Import Hugging Face pipeline
from transformers import pipeline  
```
4️⃣ Load the GPT-2 model, which is a pre-trained language model:
```python
# Define text generation task
task = "text-generation"  

# Specify model name
model_name = "gpt2"  

# Load the pre-trained GPT-2 model
generator = pipeline(task, model=model_name)  
```
5️⃣ Generate text based on a given prompt:
```python
# Define input prompt
prompt = "Once upon a time, in a futuristic city,"  

# Set maximum number of new tokens
max_tokens = 50  

# Generate text based on prompt
output = generator(prompt, max_new_tokens=max_tokens)  

# Extract generated text
generated_story = output[0]['generated_text']  

# Print generated story
print("Generated Story:")  
print(generated_story)  
```
6️⃣ **Click Run (▶) and check the output!** 
  
✅ Text generation complete! You should now see a futuristic story generated by GPT-2. 📖🚀🎉

💡 **Challenge:** Modify the `prompt` variable to explore different stories.

## 🤔 Step 3: Analyze App Descriptions with GPT-2
Instead of manually writing descriptions, let’s use GPT-2 to generate app descriptions automatically.


### **➕🐍 Add a New Code Cell**    
1️⃣ Click **+ Code** in Jupyter Notebook to add a new code cell.  
2️⃣ Copy and paste the following code:  

🔗 [ChatGPT explanation for the code](https://chatgpt.com/share/67cb1863-4454-8004-844c-41cb9b1f197e)

3️⃣ Extract app names and format them into prompts:
```python
# Extract app names from dataset
app_names = playstore_df['App Name'].dropna()  

# Convert app names into prompts for description generation
app_descriptions = [f"{str(app)} is an app that " for app in app_names]  
```
4️⃣ Use GPT-2 to generate descriptions for each app:
```python
# Select first 10 app names to generate descriptions
selected_apps = app_descriptions[:10]  

# Set max tokens for generated descriptions
max_description_tokens = 50  

# Generate text for app descriptions
outputs = generator(selected_apps, max_new_tokens=max_description_tokens)  
```
5️⃣ Print generated app descriptions:
```python
# Print generated descriptions for each app
print("Generated App Descriptions:")  
for app, output in zip(playstore_df['App Name'][:10], outputs):  
    generated_text = output[0]['generated_text']  
    print(f"{app}: {generated_text}")  
```
6️⃣ **Click Run (▶) and check the output!** 

✅ App descriptions generated! You should now see AI-generated descriptions for the first 10 apps. 📱✨🎉

💡 **Challenge:** Try processing more than 10 apps to analyze the variety of AI-generated text.

---

## 🎯 4. Wrap-Up & Next Steps
🎉 Congratulations! You learned how to:
- ✅ Access **HPC & JupyterLab** 🖥️
- ✅ Install **LLM dependencies on HPC** 🔧
- ✅ Download and analyze **Kaggle datasets** 📊
- ✅ Use **GPT-2 for text generation** ✍️
- ✅ Apply AI to real-world app descriptions 🏗️

🚀 **Next Workshop:** [📚 LLM + RAG (AI-Powered Search)](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/hpc-llm-rag)


### 🔗 Additional Resources 📚
- [Project Jupyter Documentation](https://docs.jupyter.org/en/latest/)     
- [Python Introduction](https://www.w3schools.com/python/python_intro.asp)<br> 
⚠ **Warning:** Please use only the two green buttons (“Previous” and “Next”) to navigate the tutorial. Avoid clicking on other links to prevent being redirected to ads.     
- [CSUSB: High-Performance Computing (HPC) Resources](https://www.csusb.edu/faculty-center-for-excellence/idat/high-performance-computing)   
- [Microsoft Learn: Introduction to large language models](https://learn.microsoft.com/en-us/training/modules/introduction-large-language-models/)

🎉 **Keep exploring AI, and see you at the next workshop!** 🚀