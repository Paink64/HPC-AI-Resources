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
            1. **Find the "New" Button**:
               - Look at the top-right corner of the screen. You’ll see a button labeled **New**. Click it.
            2. **Select "Python 3"**:
               - A dropdown menu will appear. Click **Python 3** to create a new notebook.
            3. **Write Your First Code**:
               - You’ll see a blank cell in the notebook. Type the following code:
                 ```python
                 print("Hello, World!")
                 ```
            4. **Run the Code**:
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
[⚙️ Accessing the Pre-Built Docker Environment](personal-computer-docker-access)

---

## ❓ **Questions?** 🤔
If you have any questions or run into issues, feel free to ask for help. Let’s get started on your AI journey! 🚀