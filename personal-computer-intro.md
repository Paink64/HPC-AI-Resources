# 📌 Intro to Command Terminal, AI, Docker & Jupyter 🖥️🤖🐳

Welcome to the first step of your **AI and High-Performance Computing (HPC)** journey! 🚀 In this section, we’ll introduce you to the essential tools and concepts you’ll need to get started. By the end of this workshop, you’ll have a solid foundation in using the **command terminal**, understanding **AI basics**, working with **Docker**, and running code in **Jupyter Notebooks**. Let’s dive in! 🌊

---

## 🖥️ **What You’ll Learn** 🎓
- **Command Terminal**: The gateway to interacting with your computer like a pro. 💻
- **Artificial Intelligence (AI)**: What it is, why it matters, and how it’s changing the world. 🤖🌍
- **Docker**: A tool that simplifies software setup so you can focus on learning. 🐳
- **Jupyter Notebooks**: An interactive environment for writing and running code. 📓✨

---

## 🚀 **Why These Tools?** 🌟
- **Command Terminal**: It’s the backbone of working with computers, especially for AI and HPC. 💪
- **AI**: From self-driving cars 🚗 to chatbots 💬, AI is everywhere—and you’ll learn how it works!
- **Docker**: No more “it works on my machine” problems! Docker ensures everyone has the same setup. ✅
- **Jupyter Notebooks**: Perfect for experimenting with code and visualizing results. 🎨

---

## 🛠️ **What You’ll Need** 🧰
- A computer (Windows, macOS, or Linux). 💻
- A sense of curiosity and willingness to learn! 🧠✨

---

## 📝 **Topics Covered** 📚

### 1. **Command Terminal Basics** ⌨️
   - **What is the Terminal?** 🤔
     - The terminal is a text-based interface for interacting with your computer. Instead of using a graphical user interface (GUI), you type commands to perform tasks like navigating folders, running programs, and managing files.
     - Think of it as a **direct line to your computer’s brain**! 🧠💻

   - **How to Open a Terminal** 🖱️
     - **Windows**:
       1. Install **Windows Subsystem for Linux (WSL)** if you don’t already have it:
          - Open PowerShell as Administrator and run:
            ```bash
            wsl --install
            ```
       2. Open the **Ubuntu** app (or another Linux distribution) from the Start menu.
     - **macOS**:
       1. Open **Spotlight Search** (press `Cmd + Space`).
       2. Type `Terminal` and press `Enter`.
     - **Linux**:
       1. Press `Ctrl + Alt + T` to open the terminal.

   - **Basic Commands** 🛠️
     - `cd`: Change directory (navigate to a folder).
       ```bash
       cd Documents  # Moves to the "Documents" folder
       ```
     - `ls`: List files and folders in the current directory.
       ```bash
       ls  # Shows all files and folders in the current directory
       ```
     - `mkdir`: Create a new folder.
       ```bash
       mkdir my_folder  # Creates a folder named "my_folder"
       ```
     - `pwd`: Print working directory (show the current folder path).
       ```bash
       pwd  # Displays the current folder path
       ```

   - **Navigating the File System** 🗂️
     - Use `cd` to move between folders.
     - Use `ls` to see what’s inside a folder.
     - Use `pwd` to check your current location.

---

### 2. **Introduction to AI** 🤖
   - **What is AI?** 🤔
     - AI (Artificial Intelligence) refers to machines that can perform tasks that typically require human intelligence, such as understanding language, recognizing images, or making decisions.
     - **Examples**:
       - **Chatbots**: AI that can have conversations with humans (e.g., ChatGPT). 💬
       - **Image Recognition**: AI that can identify objects in photos (e.g., facial recognition). 📸
       - **Recommendation Systems**: AI that suggests products or content (e.g., Netflix recommendations). 🍿

   - **Real-World Applications** 🌍
     - **Self-Driving Cars**: AI analyzes sensor data to drive safely. 🚗
     - **Healthcare**: AI helps diagnose diseases from medical images. 🏥
     - **Gaming**: AI powers non-player characters (NPCs) in video games. 🎮

---

### 3. **What is Docker?** 🐳
   - **Why Use Docker?** 🤔
     - Docker is a tool that packages software into **containers**, which include everything needed to run the software (e.g., code, libraries, dependencies).
     - Benefits:
       - **Consistency**: Works the same way on any computer. ✅
       - **Ease of Setup**: No need to install software manually. 🛠️
       - **Isolation**: Keeps your system clean by running software in isolated environments. 🧼

   - **How Docker Works** ⚙️
     - **Containers vs. Virtual Machines**:
       - **Containers**: Lightweight, share the host system’s OS, and start quickly. ⚡
       - **Virtual Machines (VMs)**: Heavier, include a full OS, and take longer to start. 🐢
     - Docker uses containers to ensure software runs the same way everywhere. 🌍

---

### 4. **Getting Started with Jupyter** 📓✨
   - **What is Jupyter Notebook?** 🤔
     - Jupyter Notebook is an interactive environment for writing and running code. It’s especially popular for data science and AI because it allows you to mix code, visualizations, and explanations in one place.
     - Think of it as a **digital notebook** for your code! 📓✨

   - **How to Access Jupyter** 🖥️
     - We’ve prepared a **pre-built Docker image** with Python and ML libraries pre-installed. Follow these steps:
       1. **Install Docker** (if not already installed):
          - [Download Docker Desktop](https://www.docker.com/products/docker-desktop)
       2. **Run the Pre-Built Docker Image**:
          - Open your terminal and run the following command:
            ```bash
            docker run -p 8888:8888 jupyter/scipy-notebook:latest
            ```
          - This will start a Jupyter Notebook server.
       3. **Access Jupyter**:
          - Open your browser and go to `http://localhost:8888`.
          - Enter the token provided in the terminal to access Jupyter.

   - **Writing and Running Your First Python Script** 🐍
     1. Create a new notebook in Jupyter.
     2. Write your first Python script:
        ```python
        print("Hello, AI World!")
        ```
     3. Run the script by pressing `Shift + Enter`.

---

## 🎯 **Hands-On Activity** 🛠️
Let’s get started with a quick exercise:
1. Open your terminal (see instructions above).
2. Run the following command to launch the pre-built Docker environment:
   ```bash
   docker run -p 8888:8888 jupyter/scipy-notebook:latest