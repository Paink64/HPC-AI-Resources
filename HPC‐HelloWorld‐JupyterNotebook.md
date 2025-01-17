# 🚀 Running a "Hello, World!" Program on UCSD Expanse with Jupyter Notebook Using Galyleo Shell 🌟

Embarking on your High-Performance Computing (HPC) journey with Jupyter Notebooks on UC San Diego's Expanse supercomputer is both exciting and rewarding. Let's dive into a step-by-step guide to creating and running a simple "Hello, World!" program using Jupyter Notebook via the Galyleo shell. Ready? Let's go! 🎉

## 🎯 Objectives

By the end of this tutorial, you'll:

- Log in to Expanse.
- Load the Galyleo environment.
- Launch JupyterLab.
- Create a new notebook.
- Run a simple Python "Hello, World!" program.
- End your session properly.

## 🛠️ Prerequisites

Before we begin, ensure you have:

- **An Expanse Account**: If not, request one through the ACCESS Allocation Request System or contact consult@sdsc.edu for a Trial Account.
- **Basic Unix Knowledge**: Familiarize yourself with basic Unix commands. A helpful resource is available here.

## 🔑 Step 1: Accessing Expanse

1. **Open Terminal**:
   - On your local machine, open the terminal application.

2. **Connect via SSH**:
   - Use the following command to connect to Expanse:

     ```bash
     ssh your_username@login.expanse.sdsc.edu
     ```

   - Replace `your_username` with your actual Expanse username. If prompted, enter your password.

## 🛠️ Step 2: Loading Galyleo

1. **Add Galyleo to Your PATH**:
   - Execute the following command to include Galyleo in your PATH:

     ```bash
     export PATH="/cm/shared/apps/sdsc/galyleo:${PATH}"
     ```

2. **Verify Galyleo Availability**:
   - Confirm that Galyleo is available in your PATH by echoing the PATH variable:

     ```bash
     echo $PATH
     ```

   - This will display the directories included in your PATH. Ensure that the path to Galyleo is listed among them.

## 🆔 Step 3: Identifying Your Project ID

1. **List Available Projects**:
   - To view your valid project IDs, run the following command:

     ```bash
     expanse-client user
     ```

   - This will display a list of projects associated with your account.

2. **Select the Appropriate Project ID**:
   - Identify the project ID you intend to use for your session.

## 🚀 Step 4: Launching JupyterLab

1. **Launch JupyterLab**:
   - Start JupyterLab with the specified resources:

     ```bash
     galyleo launch --account your_project_id --partition shared --cpus 1 --memory 2 --time-limit 00:30:00 --env-modules cpu/0.17.3b,anaconda3/2021.05 --interface lab
     ```

   - Replace `your_project_id` with the project ID identified in Step 3.

2. **Access JupyterLab**:
   - After launching, Galyleo will provide a URL. Open this URL in your web browser to access JupyterLab.

## 📝 Step 5: Creating a New Notebook

1. **Open JupyterLab**:
   - Navigate to the provided URL in your web browser to open JupyterLab.

2. **Create a New Notebook**:
   - In JupyterLab, select the Python kernel to create a new notebook.

## 🖥️ Step 6: Running the "Hello, World!" Program

1. **Enter the Code**:
   - In the first cell of the notebook, type the following code:

     ```python
     print("Hello, World!")
     ```

2. **Run the Cell**:
   - Execute the cell to run the code. You should see the output:

     ```
     Hello, World!
     ```

## 🚪 Step 7: Ending the Session

1. **Close the Notebook**:
   - Save your work and close the notebook tab in your browser.

2. **Terminate the JupyterLab Session**:
   - In the terminal, press `Ctrl + C` to stop the JupyterLab session and release the allocated resources.

## 🎉 Congratulations!

You've successfully run your first Python "Hello, World!" program on Expanse using Jupyter Notebook via the Galyleo shell. Keep exploring and happy computing! 🌟

For a visual walkthrough, you might find this webinar helpful:

[SDSC Webinar: Running Jupyter Notebooks on Expanse](https://www.youtube.com/watch?v=LTyV4eMMO7w)
