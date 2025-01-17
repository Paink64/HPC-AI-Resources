# 🚀 Running a Python "Hello, World!" Docker Image as a Singularity Container on UCSD Expanse 🌟

Running Docker images on the Expanse supercomputer is achievable by converting them into Singularity containers. This guide will walk you through the process of pulling a Python "Hello, World!" Docker image from Docker Hub, converting it into a Singularity image, and running it on Expanse.

## 🎯 Objectives

By the end of this tutorial, you'll:

- **Access Expanse**: Log in to the Expanse system.
- **Load Singularity**: Ensure the Singularity environment is ready.
- **Pull Docker Image**: Retrieve the Python "Hello, World!" Docker image from Docker Hub.
- **Convert to Singularity**: Transform the Docker image into a Singularity image.
- **Run Singularity Container**: Execute the container on Expanse.
- **End Session**: Properly terminate your session.

## 🛠️ Prerequisites

Before proceeding, ensure you have:

- **An Expanse Account**: If not, request one through the ACCESS Allocation Request System or contact consult@sdsc.edu for a Trial Account.
- **Basic Unix Knowledge**: Familiarity with basic Unix commands.
- **Singularity Installed**: Singularity should be available on Expanse.

## 🔑 Step 1: Accessing Expanse

1. **Open Terminal**:
   - On your local machine, open the terminal application.

2. **Connect via SSH**:
   - Use the following command to connect to Expanse:

     ```bash
     ssh your_username@login.expanse.sdsc.edu
     ```

   - Replace `your_username` with your actual Expanse username. If prompted, enter your password.

## 🛠️ Step 2: Loading Singularity

1. **Load Singularity Module**:
   - Execute the following command to load the Singularity module:

     ```bash
     module load singularity
     ```

2. **Verify Singularity Availability**:
   - Confirm that Singularity is available by checking its version:

     ```bash
     singularity --version
     ```

   - This should display the Singularity version number.

## 🔄 Step 3: Pulling Docker Image

1. **Pull the Docker Image**:
   - Use Singularity to pull the Python "Hello, World!" Docker image directly from Docker Hub:

     ```bash
     singularity pull docker://python:3.8-slim-buster
     ```

   - This command retrieves the official Python 3.8 slim image from Docker Hub.

2. **Verify Image Download**:
   - List the files to ensure the `.sif` file is created:

     ```bash
     ls -lh
     ```

   - You should see a file with a `.sif` extension corresponding to the Python image.

## 🚀 Step 4: Running Singularity Container

1. **Run the Container**:
   - Execute the Singularity container interactively:

     ```bash
     singularity exec python-3.8-slim-buster.sif python -c "print('Hello, World!')"
     ```

   - This command runs the Python interpreter inside the container and prints "Hello, World!".

2. **Run a Script Inside the Container**:
   - If you have a Python script (e.g., `hello_world.py`), you can run it as follows:

     ```bash
     singularity exec python-3.8-slim-buster.sif python hello_world.py
     ```

   - Ensure that `hello_world.py` is in your current directory or provide the full path to the script.

## 🚪 Step 5: Ending the Session

1. **Exit the Container**:
   - If you are inside an interactive shell, type `exit` to leave the container.

2. **Terminate the Singularity Session**:
   - Ensure all processes are complete, and the container has stopped.

## 🎉 Congratulations!

You've successfully pulled a Python "Hello, World!" Docker image, converted it into a Singularity container, and run it on Expanse. For a visual walkthrough, you might find this webinar helpful:

[Singularity – Containers for Scientific and High-Performance Computing](https://www.youtube.com/watch?v=Cjbc7QO_PiY)
