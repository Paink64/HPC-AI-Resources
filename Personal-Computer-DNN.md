# 🤖 Deep Neural Networks (DNN) Workshop with the Iris Dataset 🌸

Welcome to this exciting workshop where you’ll build your first **Deep Neural Network (DNN)** using the **Iris dataset**! 🚀 AI is all about learning from data, and today, you’ll train a model to recognize different types of flowers. Let’s get started! 🌟

---

## 🖥️ **What You’ll Learn** 🎓
- How to **load and explore data** in Jupyter Notebooks.
- How to **prepare data** for training an AI model.
- How to **build, train, and test a Deep Neural Network** using TensorFlow and Keras.
- How to **evaluate model performance** and improve results.

---

## 🌟 **Why is AI Important?**
- AI helps computers **learn from data** and make predictions.
- Neural networks are the building blocks of **smart AI systems**.
- By training a model, we can **recognize patterns** in real-world data.

---

## 🛠️ **What You’ll Need** 🧰
- A running **Jupyter Notebook** (see previous workshops if you need help setting it up).
- The **Iris dataset** (which we’ll load using Python).
- Python libraries: `tensorflow`, `keras`, `numpy`, `pandas`, and `matplotlib`.

---

## 📚 **Step-by-Step Guide**

### 1. **What is a Neural Network?** 🤔
   - A **Neural Network** is a type of AI model that mimics how the human brain learns.
   - It consists of **layers of neurons** that process information and find patterns in data.
   - Deep Neural Networks (DNNs) have multiple layers, allowing them to learn **complex relationships**.

---

### 2. **Load and Explore the Dataset** 📂
   1. **Import Libraries**:
      ```python
      import pandas as pd
      import numpy as np
      import tensorflow as tf
      from tensorflow import keras
      from sklearn.model_selection import train_test_split
      from sklearn.preprocessing import LabelEncoder
      import matplotlib.pyplot as plt
      from sklearn.datasets import load_iris
      print("Libraries imported successfully! 🎉")
      ```
   
   2. **Load the Iris Dataset**:
      ```python
      iris = load_iris()
      data = pd.DataFrame(iris.data, columns=iris.feature_names)
      data['species'] = iris.target
      print("Dataset loaded successfully! 🎉")
      ```

   3. **Explore the Data**:
      ```python
      print("First 5 rows of the dataset:")
      print(data.head())
      print("Dataset Info:")
      print(data.info())
      print("Summary Statistics:")
      print(data.describe())
      ```
      
---

### 3. **Prepare the Data for Training** 🏋️‍♂️
   1. **Encode Labels**:
      ```python
      label_encoder = LabelEncoder()
      data['species'] = label_encoder.fit_transform(data['species'])
      print("Labels encoded successfully! 🎉")
      ```
   
   2. **Split the Data** (80% for training, 20% for testing):
      ```python
      X = data.drop(columns=['species'])
      y = data['species']
      X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
      print("Data split successfully! 🎉")
      ```

---

### 4. **Build a Deep Neural Network (DNN)** 🏗️
   - Our model will have **three layers**: an input layer, a hidden layer, and an output layer.
   
   ```python
   model = keras.Sequential([
       keras.layers.Dense(10, activation='relu', input_shape=(X_train.shape[1],)),
       keras.layers.Dense(10, activation='relu'),
       keras.layers.Dense(3, activation='softmax')  # 3 output classes
   ])
   
   model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
   print("Model built successfully! 🎉")
5. Train the Model 🚀
Now, we train the model using our training data!
python
Copy
Edit
history = model.fit(X_train, y_train, epochs=50, validation_data=(X_test, y_test))
print("Model training completed! 🎉")
6. Evaluate the Model 📊
Check Accuracy:

python
Copy
Edit
test_loss, test_acc = model.evaluate(X_test, y_test)
print(f"Test accuracy: {test_acc:.4f}")
Plot Training History:

python
Copy
Edit
plt.plot(history.history['accuracy'], label='Train Accuracy')
plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
plt.xlabel('Epochs')
plt.ylabel('Accuracy')
plt.legend()
plt.show()
🎯 Quick Challenge 🏆
Try changing the number of neurons in the hidden layers. Does it improve accuracy? 🤔
What happens if you increase or decrease the number of training epochs? 🔄
🎉 Congratulations! 🎊
You’ve built and trained your first Deep Neural Network using the Iris dataset! Keep experimenting and learning. The world of AI is just getting started! 🚀