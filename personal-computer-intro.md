# 📌 Intro to Command Terminal, AI, Docker & Jupyter 🖥️🤖🐳

Welcome to your **AI and High-Performance Computing (HPC)** journey! 🚀 In this workshop, you’ll learn how to use cool tools like the **command terminal**, **Docker**, and **Jupyter Notebooks** to explore the world of **Artificial Intelligence (AI)**. Let’s get started! 🌟

---

## 🖥️ **What You’ll Learn** 🎓
- **Command Terminal**: Talk to your computer like a pro. 💻
- **AI Basics**: What AI is and why it’s awesome. 🤖
- **Docker**: A magic box that makes software easy to use. 🐳
- **Jupyter Notebooks**: A fun way to write and run code. 📓✨

---

## 🚀 **Why These Tools?** 🌟
- **Command Terminal**: It’s like a secret code to control your computer. 🔐
- **AI**: From chatbots 💬 to self-driving cars 🚗, AI is everywhere—and you’ll learn how it works!
- **Docker**: No more “it works on my computer” problems! Docker makes everything run the same way for everyone. ✅
- **Jupyter Notebooks**: Write code, see results, and make cool visuals—all in one place. 🎨

---

## 🛠️ **What You’ll Need** 🧰
- A computer (Windows, macOS, or Linux). 💻
- A sense of curiosity and a willingness to learn! 🧠✨

---

## 📝 **Topics Covered** 📚

---

### 1. **Command Terminal Basics** ⌨️
   - **What is the Terminal?** 🤔
     - The terminal is like a **text-based remote control** for your computer. Instead of clicking icons, you type commands to make things happen.
     - Think of it as a **secret code** to unlock your computer’s powers! 🔓

   - **How to Open a Terminal** 🖱️
     - **Windows**:
       1. Open the **Ubuntu** app (or another Linux app) from the Start menu.
     - **macOS**:
       1. Open **Spotlight Search** (press `Cmd + Space`).
       2. Type `Terminal` and press `Enter`.
     - **Linux**:
       1. Press `Ctrl + Alt + T` to open the terminal.

---

### 2. **Introduction to AI** 🤖
   - **What is AI?** 🤔
     - AI (Artificial Intelligence) is when computers can do things that usually need human brains, like understanding language or recognizing faces.
     - **Examples**:
       - **Chatbots**: AI that talks to you (e.g., ChatGPT). 💬
       - **Image Recognition**: AI that knows what’s in a photo (e.g., facial recognition). 📸
       - **Recommendations**: AI that suggests movies or songs (e.g., Netflix). 🍿

   - **Why is AI Cool?** 🌟
     - It powers self-driving cars 🚗, helps doctors diagnose diseases 🏥, and even beats humans at video games 🎮!

---

### 3. **What is Docker?** 🐳
   - **Why Use Docker?** 🤔
     - Docker is like a **magic box** that holds everything your software needs to run. It makes sure your code works the same way on any computer.
     - No more “it works on my computer” problems! 🎉

   - **How Docker Works** ⚙️
     - Docker puts your software in a **container**—a lightweight, portable box that includes everything it needs to run.
     - It’s like packing your lunch in a lunchbox 🍱—everything you need is in one place!

---

### 4. **Getting Started with Jupyter** 📓✨
   - **What is Jupyter Notebook?** 🤔
     - Jupyter Notebook is like a **digital notebook** where you can write code, see results, and add notes—all in one place.
     - It’s perfect for experimenting with AI and making cool visuals! 🎨

   - **How to Use Jupyter** 🖥️
     - We’ve prepared a **pre-built Docker image** with everything you need. Just follow these steps:
       1. **Install Docker** (if not already installed):
          - [Download Docker Desktop](https://www.docker.com/products/docker-desktop)
       2. **Run the Docker Image**:
          - Open your terminal and run:
            ```bash
            docker run -p 8888:8888 jupyter/scipy-notebook:latest
            ```
       3. **Access Jupyter**:
          - Open your browser and go to `http://localhost:8888`.
          - Enter the token from the terminal to start coding!
       4. **Create a New Notebook and Run "Hello World"**:
          - Once you’re in Jupyter, you’ll see a file browser interface. Here’s how to create a new notebook:
            1. **Find the "File" Menu**:
               - Look at the top-left corner of the screen. You’ll see a menu labeled **File**. Click it.
            2. **Select "New" → "Notebook"**:
               - In the dropdown menu, hover over **New**, then click **Notebook**.
            3. **Choose "Python 3"**:
               - A pop-up will appear asking you to select a kernel. Choose **Python 3** and click **Select**.
            4. **Write Your First Code**:
               - You’ll see a blank cell in the notebook. Type the following code:
                 ```python
                 print("Hello, World!")
                 ```
            5. **Run the Code**:
               - Press `Shift + Enter` to run the code.
               - You should see `Hello, World!` printed below the cell. 🎉

---

## 🎯 **Quick Challenge** 🏆
- **Modify the Code**:
  - Change the code to print your name instead of "Hello, World!".
  - Example:
    ```python
    print("Hello, [Your Name]!")
    ```
  - Press `Shift + Enter` to run the updated code.

---

## 🛠️ **Troubleshooting Tips** 🔧
- **Docker Won’t Start?**
  - Make sure Docker Desktop is installed and running.
  - Restart your computer and try again.
- **Jupyter Token Not Working?**
  - Check the terminal for the correct token.
  - If you lose the token, stop the Docker container and restart it.

---

## 📚 **Additional Resources** 📖
- [Command Terminal Cheat Sheet](https://cheatography.com/davechild/cheat-sheets/linux-command-line/)
- [Docker Documentation](https://docs.docker.com/)
- [Jupyter Notebook Tutorial](https://jupyter.org/try)

---

## ➡️ **Next Steps** 🚀
Ready to dive deeper? Head over to the next section:  
[📊 Data Exploration & Management](personal-computer-data-exploration)

---

## ❓ **Questions?** 🤔
If you have any questions or run into issues, feel free to ask for help. Let’s get started on your AI journey! 🚀