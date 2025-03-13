# 🚀✨ Deep Neural Network (DNN) Workshop for Beginners! ✨

## 🎯 Goal

📊 Learn how to **build, train, and visualize** a Deep Neural Network (DNN) using TensorFlow and Keras. No prior experience needed—just bring your curiosity and creativity! 🚀

---
## 📌 What You Will Learn 🧠💡

✅ What datasets are and why they matter 📂<br>
✅ How to **prepare and process** real-world data 🔍<br>
✅ How to **build** a Deep Neural Network 🏗️<br>
✅ How to **train and evaluate** the DNN 🔄<br>
✅ How to **visualize** training results 📈<br>
✅ Hands-on coding with **Google Colab** for easy Python use 💻<br>

---

## 📚 1. Key Terminologies in Deep Neural Networks 🧠

### 🧠 What is a Neuron?

A neuron (also called a node or unit) is the basic building block of a neural network, similar to how a neuron in the human brain processes information. It takes in inputs, performs a mathematical operation, and then produces an output.

### 🖼️ Deep Neural Network Visual Representation

<img width="600" alt="Screenshot 2025-03-11 at 3 33 33 PM" src="https://github.com/user-attachments/assets/4bdbeb87-510b-40b2-b3ff-5c4d446146eb" />

Source: [Google Images](https://medium.com/data-science-365/overview-of-a-neural-networks-learning-process-61690a502fa)

### 🧠 How a Neural Network Learns 🔗 
 
💡 Think: How do these concepts work together to train an AI model? 🤔

Neural networks are a fundamental part of artificial intelligence (AI). They learn by adjusting their internal settings based on data. This process involves two main steps: **forward propagation** (making predictions) and **backward propagation** (learning from mistakes). 

- Neurons – The building blocks of neural networks that receive inputs, process them, and produce outputs. 🧠
- Layers – Different levels in a neural network, including input, hidden, and output layers. 🏗️
- Activation Function – Determines whether a neuron should activate or not (e.g., ReLU, Sigmoid, Softmax). ⚡
- Weights & Biases – Parameters that are adjusted during training to improve predictions. ⚖️
- Forward Propagation – The process of passing input data through the network to generate an output. ➡️
- Loss Function – Measures how well the network's predictions match the actual values (e.g., Mean Squared Error, Cross-Entropy Loss). ❌
- Optimizer – A method for adjusting weights and biases to minimize loss (e.g., Adam, SGD). 🔄
- Backpropagation – The technique used to update network parameters by propagating errors backward. 🔙
- Epochs & Batch Size – Defines how many times the network trains on the entire dataset and how much data is processed at a time. 🔁

### 🚀 Step 1: Forward Propagation (Making Predictions)

Forward propagation is the process of passing inputs through the network to generate predictions.

### **How It Works**
- **Input Layer**: The network receives raw data (e.g., temperature, humidity).
- **Hidden Layers**:
   - Each neuron applies a **weighted sum** to the inputs.
   - The result passes through an **activation function** that helps decide which information is important.
- **Output Layer**: The final result (prediction) is generated.

### **Example**

If we are predicting whether it will rain:

- **Input**: Humidity = 80%, Temperature = 25°C
- **Hidden Layer Processing**: Mathematical operations adjust these numbers.
- **Output**: "Yes, it will rain" (Prediction).

### 🚀 Step 2: Loss Function (Measuring Mistakes)

The prediction is compared to the actual answer. The **loss function** calculates how far off the prediction was:
- A **low loss** means the prediction was close.
- A **high loss** means the network needs improvement.

### 🚀 Step 3: Backward Propagation (Learning from Mistakes)

Backward propagation adjusts the network to reduce mistakes.

### **How It Works**

- **Error Calculation**: The loss function determines how wrong the prediction was.
- **Weight Adjustment**:
   - The **optimizer** updates the weights using **gradient descent** (a technique to find the best values).
- **Repeat Until Accurate**: The process repeats multiple times, gradually improving accuracy.

### 🚀 Step 4: Why This Matters

Neural networks power many AI applications, including:

✅ **Self-driving cars** (object detection)  
✅ **Facial recognition** (unlocking phones)  
✅ **Medical diagnosis** (detecting diseases)  
✅ **Chatbots & AI assistants** (Siri, ChatGPT)  

By using forward and backward propagation, AI **learns and improves over time**, just like humans learning from experience.

---
## 🔍 2. Hands-on: Exploring a Real Dataset

### Open Google Colab

1️⃣ Open your browser and go to **[Google Colab](https://colab.research.google.com/)**.<br>
2️⃣ Click **+ New notebook**.<br>

---

## 💾 3. Loading the Iris Dataset

### Add a New Code Cell

1️⃣ Click **+ Code** in the top left to add a new code cell.<br>
2️⃣ Copy and paste the following code into the new code cell.<br>

[ChatGPT Code Conversation](https://chatgpt.com/share/67c906e3-6300-8008-8dc1-d5aa700b0dce)

```python
import pandas as pd
from sklearn.datasets import load_iris

# Load the dataset
dataset = load_iris()
data = pd.DataFrame(dataset.data, columns=dataset.feature_names)
data['species'] = dataset.target
print("Dataset loaded successfully! 🎉")
```
3️⃣ **Click Run (▶) and check the output!** 

---
## 🏗️ 4. Building the DNN Model

### Add a New Code Cell

1️⃣ Click **+ Code** in the top left to add a new code cell.<br>
2️⃣ Copy and paste the following code into the new code cell.<br>

[ChatGPT Code Conversation](https://chatgpt.com/share/67c90811-dfa8-8008-bd94-c63b3bbc4670)

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Define the DNN model
model = Sequential([
    Dense(10, activation='relu', input_shape=(4,)),
    Dense(10, activation='relu'),
    Dense(3, activation='softmax')
])

print("DNN model created successfully! 🎉")
```

3️⃣ **Click Run (▶) and check the output!** 

---
## 🎯 5. Training the DNN Model

### Add a New Code Cell

1️⃣ Click **+ Code** in the top left to add a new code cell.<br>
2️⃣ Copy and paste the following code into the new code cell.<br>

[ChatGPT Code Conversation](https://chatgpt.com/share/67cb97b0-cc34-8008-a86f-c8bb76ad6758)

```python
from sklearn.model_selection import train_test_split
from tensorflow.keras.utils import to_categorical

# Prepare the data
X_train, X_test, y_train, y_test = train_test_split(dataset.data, dataset.target, test_size=0.2)
y_train_encoded = to_categorical(y_train, num_classes=3)
y_test_encoded = to_categorical(y_test, num_classes=3)

# Compile and train the model
model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
history = model.fit(X_train, y_train_encoded, epochs=50, batch_size=8, validation_split=0.2)
```

3️⃣ **Click Run (▶) and check the output!** 

---

## 📈 6. Visualizing Training Progress

### Add a New Code Cell

1️⃣ Click **+ Code** in the top left to add a new code cell.<br>
2️⃣ Copy and paste the following code into the new code cell.<br>

[ChatGPT Code Conversation](https://chatgpt.com/share/67cfa74e-b278-8008-8861-7c27a38e8f5f)

```python
import matplotlib.pyplot as plt
plt.plot(history.history['loss'])
plt.xlabel('Epochs')
plt.ylabel('Loss')
plt.title('Training Progress')
plt.show()
```
3️⃣ **Click Run (▶) and check the output!** 

The following graph shows the **loss (error) reduction** during training. The loss function helps us understand how well the Deep Neural Network (DNN) is learning over time.

<img src="https://github.com/user-attachments/assets/cb39433e-788d-44e3-bfa7-a5b6af02a496" alt="Training Progress - Loss Reduction" width="450">

- The **X-axis (Epochs)** represents the number of training iterations, and the **Y-axis (Loss)** represents the remaining error in the model’s predictions. 

- The decreasing trend indicates that the model is learning and improving!

---

## 🏆 7. Evaluating the Model

### Add a New Code Cell
1️⃣ Click **+ Code** in the top left to add a new code cell.<br>
2️⃣ Copy and paste the following code into the new code cell.<br>

[ChatGPT Code Conversation](https://chatgpt.com/share/67cfa6c0-43d8-8008-9a03-b6bd05ffbebb)

```python
loss, accuracy = model.evaluate(X_test, y_test_encoded)
print(f"Test Accuracy: {accuracy * 100:.2f}% 🎉")
```

3️⃣ **Click Run (▶) and check the output!** 

---

## 🔮 8. Making Predictions

### Add a New Code Cell

1️⃣ Click **+ Code** in the top left to add a new code cell.<br>
2️⃣ Copy and paste the following code into the new code cell.<br>

[ChatGPT Code Conversation](https://chatgpt.com/share/67cfa5c0-d644-8008-9a02-9c1180e2f9c6)

```python
import numpy as np

new_sample = np.array([[5.0, 3.2, 1.3, 0.2]])
prediction = model.predict(new_sample)
predicted_class = np.argmax(prediction)
print(f"Predicted class: {predicted_class} 🎯")
```

3️⃣ **Click Run (▶) and check the output!** 

---
## 🎉 9. Wrap-Up & Next Steps

🎯 Congratulations! You’ve just built and trained your first Deep Neural Network! 🚀<br>
✅ Loaded and prepared the dataset 📂<br>
✅ Built a deep learning model 🏗️<br>
✅ Trained the model 🔄<br>
✅ Evaluated its accuracy 📊<br>
✅ Made predictions 🎯<br>

📌 **Next Steps**: [d](https://github.com/DrAlzahrani/HPC-AI-Resources/wiki/personal-computer-intro-llms)

📚 **Additional AI Resources**

- [Google Colab: Getting Started](https://colab.research.google.com/#scrollTo=GJBs_flRovLc)     
- [Python Introduction](https://www.w3schools.com/python/python_intro.asp)      
- [Google TensorFlow Documentation](https://www.tensorflow.org/)
- [Train and Evaluate Models by Microsoft](https://learn.microsoft.com/en-us/training/modules/train-evaluate-deep-learn-models/)

🚀 Keep learning and see you at the next workshop! 🎉