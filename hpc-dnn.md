# 🚀✨ High-Performance Computing (HPC) Deep Neural Network (DNN) Workshop! 🌟✨

## 🎯 **Goal**
📊 Learn how to build, train, and visualize a **Deep Neural Network (DNN)** using **PyTorch and HPC**. We will use the **Places365 dataset** and leverage **multi-GPU distributed training** on **CSUSB's HPC cluster**. No prior experience is needed—just bring your curiosity and creativity! 🚀

---

## 📌 **What You Will Learn** 🧠💡  

✅ Understanding large datasets and their significance 📂 <br>
✅ Preparing and processing real-world data at scale 🔍 <br>
✅ Building a **Deep Neural Network** optimized for **HPC** 🏗️ <br>
✅ Training and evaluating a **DNN using multi-GPU acceleration** 🔄 <br> 
✅ Visualizing training results 📈  <br>
✅ Hands-on coding with **PyTorch, DistributedDataParallel (DDP), and HPC** 💻  <br>

---

## 🔑 **1. Key Terminologies in High-Performance Computing (HPC) Deep Neural Networks** 🧠  

🖥️ CPU vs. GPU

This image illustrates the difference between a CPU (Central Processing Unit) and a GPU (Graphics Processing Unit):

<img width="450" alt="Screenshot 2025-03-11 at 6 07 07 PM" src="https://github.com/user-attachments/assets/af1f80eb-a9e7-451a-bf22-22ad55372859" />


**CPU (left side)**: Contains only a few powerful cores optimized for sequential processing. It handles general-purpose computing tasks efficiently but struggles with massively parallel workloads.

**GPU (right side)**: Contains thousands of smaller cores designed for parallel processing. GPUs are highly efficient for matrix operations and deep learning computations, making them ideal for high-performance computing (HPC) tasks.

By leveraging GPUs over CPUs, deep learning models can process massive datasets faster and scale training workloads efficiently.

#### 🚀 **Parallel Computing**

- The technique of performing multiple computations simultaneously using multiple processors or cores.
- Essential for deep learning models, allowing faster training by distributing workloads across GPUs or nodes.

#### 🚀 **Distributed Computing**

- Splitting tasks across multiple nodes (computers) in an HPC cluster to enhance computational efficiency.
- Used in deep learning for training large models with massive datasets.

#### 🚀 **Tensor Cores**

- Hardware components within modern GPUs designed to accelerate matrix multiplications, crucial for AI workloads.
- Provide significant speedups in deep learning computations.

#### 🚀 **Why These Concepts Matter?**
- These HPC concepts **enable large-scale AI training**, reducing training times from weeks to hours.
- They allow deep learning models to **scale efficiently**, making cutting-edge AI research possible.

By leveraging **parallel processing, distributed computing, and GPU acceleration**, we can train deep learning models on massive datasets faster than ever before! 🚀  

---
## 🔍 **1: Access HPC Terminal via JupyterHub**

1️⃣ Go to [CSUSB HPC](https://csusb-hpc.nrp-nautilus.io/).<br>
2️⃣ Click CI Logon to log in using your school account.<br>
3️⃣ Select GPU & Image.<br>

Once logged in:
- Under **GPU Type**, select **RTX A5000**.
- Choose **2 GPU cores**.
- In the **Image selection**, pick **Stack PyTorch 2**.

4️⃣ After logging in, Welcome to JupyterLab.

---

## 🔍 **2. Hands-on: Loading a Large Dataset on HPC**

We will use CSUSB’s High-Performance Computing (HPC) system to run our AI code. Follow these steps to access JupyterHub on HPC.

### 🚀 **Step 1**: Log In to HPC with CI Logon 🔐

Let’s get you authenticated! Here’s how:

1️⃣ Go to the CI Logon Portal

- Open [CI Logon](https://csusb-hpc.nrp-nautilus.io/) in your browser.
- Click Sign in with CILogon

2️⃣ Select Your Identity Provider & Log In

- Choose "California State University, San Bernardino" 🎓 from the dropdown.
- Check "Remember this selection" to save time next login. ✅
- Click Log On to proceed. 🚀

### 🖥️ **Step 2**: Launch Your JupyterHub Server

Your HPC Jupyter environment is ready—let’s start coding!

1️⃣ Check Out the Launcher Page

- You’ll see several options like:
- Notebook: Start a Jupyter Notebook (e.g., Python 3 🐍).
- Console: Open a Python console for quick commands 📟.
- Other: Access Terminal, Text File, Markdown File, or Help 📚.

2️⃣ Open a Notebook or File

- Click Notebook → Python 3 (ipykernel) to start coding! ✍️
- You can also browse and open existing files. 📂

3️⃣ Run Your Code & Save Your Work

- Type your Python code and press Shift + Enter to run.
- Save often to keep your work safe! 💾

❓ **Why Use 2 GPU Cores and RTX A5000?**

We are working with **huge datasets** that require powerful GPUs for efficient computation. 

### 📂 Step 3: Load the Places365 Dataset

🏞️ **Places365** (PyTorch)
- A large-scale dataset used for **scene classification**.
- Contains **~1.8 million** images spanning **365 categories**.
- Needs **significant GPU power** for training deep neural networks.

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  


[Chatgpt Code Conversation](https://chatgpt.com/share/67d0f4af-9c8c-8008-b2ae-4ca613a0ec40)

```python
import torch
import torchvision
import torchvision.transforms as transforms

# Check GPU availability
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

# Define dataset transformation
transform = transforms.Compose([
    transforms.Resize((256, 256)),
    transforms.ToTensor(),
    transforms.Normalize((0.5,), (0.5,))
])

# Load Places365 dataset
train_dataset = torchvision.datasets.Places365(root="/scratch/datasets", split='train-standard', download=True, transform=transform)
test_dataset = torchvision.datasets.Places365(root="/scratch/datasets", split='val', download=True, transform=transform)

# Create DataLoader for efficient processing
train_loader = torch.utils.data.DataLoader(train_dataset, batch_size=512, shuffle=True, num_workers=16, pin_memory=True)
test_loader = torch.utils.data.DataLoader(test_dataset, batch_size=512, shuffle=False, num_workers=16, pin_memory=True)

print(f"Dataset Loaded: Places365 with {len(train_dataset)} training images")
```

3️⃣ **Click Run (▶) and check the output!** 

---

## 🏗️ **3. Building and Training a Deep Neural Network on HPC**

### Define a CNN Model

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

[ChatGpt Code Conversation](https://chatgpt.com/share/67d0f4fb-3dc4-8008-8f9e-a42de947400a)

```python
import torch.nn as nn
import torch.optim as optim

class DeepCNN(nn.Module):
    def __init__(self):
        super(DeepCNN, self).__init__()
        self.conv1 = nn.Conv2d(3, 64, kernel_size=3, stride=1, padding=1)
        self.relu = nn.ReLU()
        self.conv2 = nn.Conv2d(64, 128, kernel_size=3, stride=1, padding=1)
        self.pool = nn.MaxPool2d(2, 2)
        self.fc1 = nn.Linear(128 * 128 * 128, 1024)
        self.fc2 = nn.Linear(1024, 365)
    
    def forward(self, x):
        x = self.pool(self.relu(self.conv1(x)))
        x = self.pool(self.relu(self.conv2(x)))
        x = x.view(-1, 128 * 128 * 128)
        x = self.relu(self.fc1(x))
        x = self.fc2(x)
        return x

model = DeepCNN().to(device)
print("Model created!")
```

3️⃣ **Click Run (▶) and check the output!** 

---

## 🏗️ **4. Evaluating the Model**

### Evaluate Model on Test Data

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

[ChatGpt Code Conversation](https://chatgpt.com/share/67d0f58d-e518-8008-b987-d1f14a7de503)

```python
correct = 0
total = 0
with torch.no_grad():
    for inputs, labels in test_loader:
        inputs, labels = inputs.to(device), labels.to(device)
        outputs = model(inputs)
        _, predicted = torch.max(outputs, 1)
        total += labels.size(0)
        correct += (predicted == labels).sum().item()

accuracy = 100 * correct / total
print(f"Test Accuracy: {accuracy:.2f}% 🎯")
```

3️⃣ **Click Run (▶) and check the output!** 

---

## 🔮 5. Making Predictions

### Making Predictions

1️⃣ Click **+ Code** in the top left to add a new code cell.  
2️⃣ Copy and paste the following code into the new code cell.  

[ChatGpt Code Conversation](https://chatgpt.com/share/67d0f617-6f1c-8008-8acb-11e241fd52f9)

```python
import numpy as np

new_sample = torch.randn(1, 3, 256, 256).to(device)  # Generate a random test image
prediction = model(new_sample)
predicted_class = torch.argmax(prediction, 1).item()
print(f"Predicted Class: {predicted_class} 🎯")
```

3️⃣ **Click Run (▶) and check the output!** 

---

## 🎉 6. Wrap-Up & Next Steps

🎯 Congratulations! You’ve just built and trained your first Deep Neural Network on HPC! 🚀

✅ Loaded and prepared the dataset 📂<br>
✅ Built a deep learning model optimized for multi-GPU HPC training 🏗️<br>
✅ Trained the model using distributed computing 🔄<br>
✅ Evaluated its accuracy on Places365 📊<br>
✅ Made predictions using the trained model 🎯<br>

📌 **Next Workshop** : [🚀 Intro to HPC, AI & Jupyter](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/hpc-intro-llms)

### **🔗 Additional AI Resources** 📚

- [Project Jupyter Documentation](https://docs.jupyter.org/en/latest/)     
- [Python Introduction](https://www.w3schools.com/python/python_intro.asp)      
- [CSUSB: High-Performance Computing (HPC) Resources](https://www.csusb.edu/faculty-center-for-excellence/idat/high-performance-computing)   
- [Fundamentals of Facial Recognition](https://learn.microsoft.com/en-us/training/modules/detect-analyze-faces/)

🚀 Keep learning and see you at the next workshop! 🎉
