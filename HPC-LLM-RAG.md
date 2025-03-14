# 🚀✨ **Workshop: Scalable Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG) on CSUSB HPC** ✨🚀  


## 🎯 **Goal**  
🤖 **Learn how to implement Large Language Models (LLMs) with Retrieval-Augmented Generation (RAG) efficiently using CSUSB HPC.**
Traditional LLMs struggle with retrieving up-to-date information. **RAG enhances LLMs** by integrating external knowledge retrieval, improving accuracy for tasks like answering complex queries.  

---

## 📌 **What You Will Learn** 🧠💡  
✅ **Why Use HPC Instead of a Local Computer?**  
✅ **Access HPC Terminal via CSUSB HPC Portal**  
✅ **Install Dependencies, Setup Kaggle, and Download Dataset**   
✅ **Load and Preprocess the Dataset in Jupyter Notebook**  
✅ **Implementing Retrieval-Augmented Generation (RAG)**  
✅ **Analyzing Retrieval Efficiency**  

---

## 🖥️ **1. Why Use HPC Instead of a Local Computer?**

**Limitations of Local Machines:**
- 🚫 Limited memory (RAM) can slow down LLM inference and retrieval.
- 🚫 CPUs struggle with large datasets, making retrieval inefficient.
- 🚫 Local machines require heavy GPU resources for fine-tuning.

**Advantages of HPC:**
- ✅ **Faster processing**: Leverages powerful CPUs and GPUs.
- ✅ **Handles large-scale datasets**: Works seamlessly with **vector search** (FAISS).
- ✅ **Parallel processing**: Multiple cores process data in parallel, accelerating RAG models.
- ✅ **Remote execution**: No need to burden local machines with heavy computation.

---

## 🔍 **2: Access HPC Terminal via CSUSB HPC Portal**

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

## 💻 **3. Install Dependencies, Setup Kaggle, and Download Dataset**

1️⃣ Click **Terminal** in JupyterLab.    
2️⃣ Run the following commands:    
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1712-6940-8004-9dd6-df6e5b2542c1)

```bash
# Install Pandas, a powerful library for data manipulation and analysis, 
# providing data structures like DataFrames for handling structured data.
pip install --user pandas  

# Install Seaborn, a statistical data visualization library built on top of Matplotlib, 
# useful for creating informative and attractive graphs.
pip install --user seaborn  

# Install Matplotlib, a fundamental plotting library for Python, 
# enabling the creation of static, animated, and interactive visualizations.
pip install --user matplotlib  

# Install the Kaggle API library, which allows users to download datasets, 
# submit solutions, and interact with Kaggle’s platform programmatically.
pip install --user kaggle  

# Install FAISS (Facebook AI Similarity Search), an efficient library for 
# similarity search and clustering of dense vectors, optimized for fast retrieval.
pip install --user faiss-cpu  

# Install Hugging Face's Transformers library, which provides pre-trained models 
# for various NLP tasks such as text classification, translation, and generation.
pip install --user transformers   

# Temporarily add Kaggle to your system PATH
export PATH=~/.local/bin:$PATH  

# Permanently add Kaggle to your system PATH
echo 'export PATH=~/.local/bin:$PATH' >> ~/.bashrc  

# Apply the changes immediately
source ~/.bashrc  

# Create a new directory for dataset storage
mkdir -p ~/playstore_data  

# Navigate to dataset directory
cd ~/playstore_data  

# Download the Google Playstore dataset from Kaggle
kaggle datasets download -d gauthamp10/google-playstore-apps  

# Unzip the downloaded dataset
unzip google-playstore-apps.zip  

# List extracted files to confirm successful download
ls -lh  
```
3️⃣ **Click Run (▶) and check the output!** 

✅ **Now you have installed dependencies and downloaded the dataset! 🎉**

---

## 📚 **4: Load and Preprocess the Dataset in Jupyter Notebook**

### Step 1: Load the Dataset into a Pandas DataFrame    
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1d6c-9c98-8004-8d4e-71cacaa3d24d)    

```python
# Import Pandas for data handling
import pandas as pd  

# Define dataset path
dataset_path = "~/playstore_data/Google-Playstore.csv"  

# Load dataset into Pandas DataFrame
playstore_df = pd.read_csv(dataset_path)  

# Display first few rows
print(playstore_df.head())  
```
3️⃣ Click **Run** (▶) and check the output.

✅ **You should now see your dataset displayed!** 🎉

### Step 2: Clean and Prepare Data for RAG    
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1dbe-8580-8004-8d58-e95625a51e73)    

```python
# Check for missing values in the dataset
missing_values = playstore_df.isnull().sum()  
print("Missing Values:\n", missing_values)  

# Remove missing values
playstore_df.dropna(inplace=True)  

# Remove duplicate entries
playstore_df.drop_duplicates(inplace=True)  

# Display cleaned dataset
print(playstore_df.head())  
```
3️⃣ Click **Run** (▶) and check the output.

✅ **Now your dataset is clean and ready for retrieval-augmented generation.**

---

## 🤖 **5. Implementing Retrieval-Augmented Generation (RAG)**

### Step 1: Install and Import Required Libraries    
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1e19-a334-8004-b603-1f7d4a2034a2)    

```python
# Import required Hugging Face and FAISS libraries
from transformers import pipeline, RagTokenizer, RagRetriever, RagSequenceForGeneration  
import faiss  
```
3️⃣ Click **Run** (▶) to import the libraries.

### Step 2: Load a Pre-Trained RAG Model    
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1e75-6a94-8004-b865-f43171fe3604)    

```python
# Define tokenizer model name
tokenizer_model = "facebook/rag-sequence-nq"  

# Load tokenizer
tokenizer = RagTokenizer.from_pretrained(tokenizer_model)  

# Define generation model
generation_model = "gpt2"  

# Load text generation model
model = pipeline("text-generation", model=generation_model)  
```
3️⃣ Click **Run** (▶) to load the pre-trained model.

### Step 3: Define Query and Retrieve Information    
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1ebe-2cf4-8004-98f1-4f71c9d6d1ab)    

```python
# Define a user query
query = "What are the top categories in Google Playstore?"  

# Tokenize query
input_dict = tokenizer.prepare_seq2seq_batch(query, return_tensors="pt")  

# Retrieval disabled since retriever is removed
retrieved_docs = None  
```
3️⃣ Click **Run** (▶) to retrieve information.

### Step 4: Generate a Response    
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1f35-4c38-8004-b5dd-9f91a69c3fa2)    

```python
# Generate response based on retrieved documents
output = model(query, max_length=100, truncation=True)  

# Extract generated response
generated_response = output[0]['generated_text']  

# Print generated answer
print("Generated Answer:", generated_response)  
```
3️⃣ Click **Run** (▶) to generate a response.

📌 **Expected Output:**
- The model generates an answer using retrieval-based augmentation.

---

## 📊 **6: Analyzing Retrieval Efficiency**
    
1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  
[ChatGPT explanation for the code](https://chatgpt.com/share/67cb1f85-ef38-8004-88b3-972f1e37ca9f)    

```python
# Import visualization libraries
import matplotlib.pyplot as plt  
import seaborn as sns  

# Set figure size for better visualization
plt.figure(figsize=(12, 5))  

# Create bar plot for app categories
sns.countplot(x=playstore_df["Category"])  

# Rotate x-axis labels for readability
plt.xticks(rotation=90)  

# Set title
plt.title("Distribution of App Categories in Google Playstore")  

# Display the plot
plt.show()  
```
3️⃣ Click **Run** (▶) and check the output.

✅ **You should see a distribution of app categories.**

<img src="https://github.com/user-attachments/assets/b1d73377-5b32-46de-9a8d-a38376673770" alt="Self-Service System" width="650">


---

## 🎯 **7. Wrap-Up & Next Steps**  
🎉 Congratulations! You learned how to:

✅ **Use HPC for Large-Scale Retrieval-Augmented Generation (RAG)**   
✅ **Download and process large datasets efficiently**   
✅ **Generate responses using an AI model**   
✅ **Analyze and visualize retrieval success**

🚀 **Next Workshop:** [🔍 Ethical AI & Future Trends](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/hpc-ethical-ai)  

### 🔗 Additional AI & HPC Resources 📚  

- [Project Jupyter Documentation](https://docs.jupyter.org/en/latest/)     
- [Python Introduction](https://www.w3schools.com/python/python_intro.asp)<br>
⚠ **Warning:** Please use only the two green buttons (“Previous” and “Next”) to navigate the tutorial. Avoid clicking on other links to prevent being redirected to ads.      
- [CSUSB: High-Performance Computing (HPC) Resources](https://www.csusb.edu/faculty-center-for-excellence/idat/high-performance-computing)   
- [AWS: What is Retrieval-Augmented Generation (RAG)?](https://aws.amazon.com/what-is/retrieval-augmented-generation/)

🎉 Keep learning AI, and see you at the next workshop! 🚀