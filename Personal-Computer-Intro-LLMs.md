# 🤖 Deep Neural Network (DNN): Classifying the Iris Dataset 🌸

Welcome to the next workshop in your AI journey! 🚀 In this workshop, you'll learn how to use a **Deep Neural Network (DNN)** to classify the famous **Iris dataset**. This is a more advanced method that builds on what you learned in the Logistic Regression workshop.

---

## 🖥️ **What You’ll Learn** 🎓
- What a **Deep Neural Network (DNN)** is and how it works.
- How to build and train a DNN using **TensorFlow/Keras**.
- How to evaluate the model’s performance on the Iris dataset.

---

## 🚀 **Why Use a Deep Neural Network?** 🌟
- DNNs are powerful models that can learn complex patterns in data.
- They are great for tasks like image recognition, natural language processing, and more.
- Even though the Iris dataset is simple, using a DNN will help you understand the basics of deep learning.

---

## 🛠️ **What You’ll Need** 🧰
- A running **Jupyter Notebook**.
- The **Iris dataset** (we'll use the one from the `sklearn` library).
- **TensorFlow/Keras** installed (we’ll install it in the workshop).

---

## 📝 **Step-by-Step Guide** 📚

---

### 1. **What is a Deep Neural Network (DNN)?** 🤔
   - A **DNN** is a type of machine learning model inspired by the human brain. It consists of layers of **neurons** that process data.
   - Each layer learns to extract features from the input data, and the final layer makes predictions.
   - DNNs are especially good at handling complex, non-linear relationships in data.

---

### 2. **Install TensorFlow/Keras** 📦
   - First, we’ll install TensorFlow/Keras, a popular library for building neural networks:
     1. **Install TensorFlow**:
        - In a new cell, type:
          ```bash
          !pip install tensorflow
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve installed TensorFlow, which includes Keras for building neural networks.

---

### 3. **Load the Dataset** 📂
   - Next, we’ll load the Iris dataset and prepare it for training:
     1. **Import Libraries**:
        - In a new cell, type:
          ```python
          # Import the required libraries
          import pandas as pd
          from sklearn.datasets import load_iris
          from sklearn.model_selection import train_test_split
          from sklearn.preprocessing import OneHotEncoder
          import tensorflow as tf
          from tensorflow.keras.models import Sequential
          from tensorflow.keras.layers import Dense

          print("Libraries imported successfully! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve imported libraries needed for loading the dataset, preprocessing, and building the DNN.

     2. **Load the Dataset**:
        - In the next cell, type:
          ```python
          # Load the Iris dataset
          iris = load_iris()

          # Turn the dataset into a DataFrame
          data = pd.DataFrame(iris.data, columns=iris.feature_names)
          
          # Add the target (species) column to the dataset
          data['species'] = iris.target

          print("Dataset loaded successfully! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve loaded the Iris dataset and added a new column for the species.

     3. **View the Data**:
        - To see the first few rows of the dataset, type:
          ```python
          # Display the first 5 rows of the dataset
          display(data.head())

          print("First 5 rows displayed! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ll see the first few rows of the Iris dataset, including **sepal length**, **sepal width**, **petal length**, **petal width**, and **species**.

---

### 4. **Prepare the Data** 🛠️
   - We’ll split the data into **training** and **testing** sets and encode the target labels:
     1. **Split the Data**:
        - Type:
          ```python
          # Split the dataset into features (X) and target (y)
          X = data.drop('species', axis=1)  # Features: everything except the species column
          y = data['species']  # Target: the species column

          # Split the data into training and testing sets (80% for training, 20% for testing)
          X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

          print("Data split into training and testing sets! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You've split the dataset into features (`X`) and target (`y`), and divided it into training and testing sets.

     2. **Encode the Target Labels**:
        - Type:
          ```python
          # One-hot encode the target labels
          encoder = OneHotEncoder(sparse=False)
          y_train_encoded = encoder.fit_transform(y_train.values.reshape(-1, 1))
          y_test_encoded = encoder.transform(y_test.values.reshape(-1, 1))

          print("Target labels encoded successfully! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve converted the species labels into a one-hot encoded format, which is required for training the DNN.

---

### 5. **Build the DNN Model** 🏗️
   - Now we’ll build a simple DNN using TensorFlow/Keras:
     1. **Create the Model**:
        - Type:
          ```python
          # Create the DNN model
          model = Sequential([
              Dense(10, activation='relu', input_shape=(4,)),  # Input layer with 4 features
              Dense(10, activation='relu'),  # Hidden layer
              Dense(3, activation='softmax')  # Output layer with 3 classes
          ])

          print("DNN model created successfully! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve created a DNN with one input layer, one hidden layer, and one output layer.

     2. **Compile the Model**:
        - Type:
          ```python
          # Compile the model
          model.compile(optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])

          print("Model compiled successfully! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve configured the model to use the Adam optimizer and categorical cross-entropy loss.

---

### 6. **Train the DNN Model** 🏋️‍♀️
   - Let’s train the model using the training data:
     1. **Train the Model**:
        - Type:
          ```python
          # Train the model
          history = model.fit(X_train, y_train_encoded, epochs=50, batch_size=8, validation_split=0.2)

          print("Model trained successfully! 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve trained the DNN for 50 epochs using the training data.

---

### 7. **Evaluate the Model** 📈
   - Let’s check how well our model performs on the test data:
     1. **Evaluate the Model**:
        - Type:
          ```python
          # Evaluate the model on the test data
          loss, accuracy = model.evaluate(X_test, y_test_encoded)

          print(f"Test accuracy: {accuracy * 100:.2f}% 🎉")
          ```
        - Press `Shift + Enter` to run the code.
        - **What Happened?** 🎉
          - You’ve evaluated the model’s performance on the test data and printed the accuracy.

---

### 8. **Interpret the Results** 🧐
   - If the accuracy is high, that means the model is doing a great job of classifying the species! 🎉
   - A lower accuracy might mean that the model needs more training, or that the data has features that aren’t helpful for classification.

---

## 🎯 **Quick Challenge** 🏆
- **Change the Model Architecture**:
  - Try adding more layers or changing the number of neurons in each layer.
  - Example:
    ```python
    model = Sequential([
        Dense(20, activation='relu', input_shape=(4,)),  # Input layer with 20 neurons
        Dense(10, activation='relu'),  # Hidden layer with 10 neurons
        Dense(3, activation='softmax')  # Output layer with 3 classes
    ])
    ```

---

## 🛠️ **Troubleshooting Tips** 🔧
- **Model Not Training?**
  - Make sure you've split the data properly and check for any errors in the code.
- **Accuracy is Low?**
  - Try adjusting the number of epochs, batch size, or model architecture.

---

## 📚 **Additional Resources** 📖
- [TensorFlow/Keras Documentation](https://www.tensorflow.org/api_docs/python/tf/keras)
- [Deep Learning with Python by François Chollet](https://www.manning.com/books/deep-learning-with-python)

---

## ➡️ **Next Steps** 🚀
Now that you’ve learned how to build a DNN, you can explore more advanced topics like **Convolutional Neural Networks (CNNs)** for image classification or **Recurrent Neural Networks (RNNs)** for sequence data.

---

## ❓ **Questions?** 🤔
If you have any questions or run into issues, feel free to ask for help. Let’s continue your journey into the world of AI! 🚀