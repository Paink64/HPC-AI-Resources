# Welcome to the HPC-AI Resources for STEM and Non-STEM Researchers 🚀

## Repository Overview 📖  
This repository offers accessible resources and workshops on **AI** 🤖 and **supercomputing** (high-performance computing, HPC) 💻, designed for both **STEM** (Science, Technology, Engineering, and Mathematics) and **non-STEM** majors. The materials are presented in simple language, requiring no prior technical background, making them suitable for a wide range of learners.  

The focus is on bridging the **AI digital gap** 🌐 and enabling participants to harness the power of AI and HPC for **research**, **innovation**, and **discovery** 🌟. By simplifying complex concepts, these workshops aim to empower researchers and students alike to confidently integrate AI and HPC into their academic and professional pursuits. 💡
# Data Exploration & Management Workshop

Welcome to the **Data Exploration & Management** workshop!  
This workshop is designed to help you understand the fundamentals of **data exploration and management** using **Jupyter Notebook** in a **Docker-based environment**.  

By the end of this workshop, you will be able to:  
✅ Upload, download, and manage datasets  
✅ Move data between **local machines, HPC, and cloud storage**  
✅ Use **data visualization techniques** such as histograms, scatter plots, and box plots  

---

## 📌 Prerequisites  

Before starting, make sure you have the following installed:  

- **Git** – A version control system. [Download Git](https://git-scm.com/downloads)  
- **Docker** – A platform to run applications in isolated environments. [Download Docker](https://www.docker.com/products/docker-desktop)  

⚠️ **Windows Users:** Install and use **Windows Subsystem for Linux (WSL)** to run Linux-based commands.  
[Learn more about WSL](https://learn.microsoft.com/en-us/windows/wsl/install)  

---

## 🚀 Part 1: Using a Local Computer  

This section will guide you through setting up a **Docker image** containing all the necessary tools for data exploration and management.  

---

### 🛠 Step 1: Clone the Repository  

First, clone the workshop repository to your local machine. This will allow you to access all necessary files for the workshop.  

Run the following command in your terminal:  

```bash
git clone https://github.com/decalyu/Data-Exploration-Management.git
cd Data-Exploration-Management
```
Before building the Docker image, ensure you are inside the **correct folder** where the `Dockerfile` is located.  

Run the following command to move into the correct directory:  

```bash
cd ~/Data-Exploration-Management/Using_a_Local_Computer
```
---

### 🏗 Step 2: Build the Docker Image  

Once you have cloned the repository, the next step is to **build the Docker image**. This image contains all the necessary tools and dependencies required for the workshop.  

Run the following command to build the Docker image:  

```bash
docker build -t data_exploration_management .
```

---



### 🔄 Step 3: Pull the Latest Version  

If you have already cloned the repository but want to ensure you have the latest updates, run the following command:  

```bash
git pull origin main
```
---

### ✅Step 4: Modify Script Permissions
Enable execute permissions for the setup script:  
```bash
chmod u+x docker_image_setup.sh
```
---

### 📦 Step 5: Run the Docker Container  
> **⚠️ Warning**: Ensure port `8888` is free. The script will automatically clean up this port if it's in use by stopping and removing any Docker container using it.
Once the Docker image has been built, you need to **run a container** from it. This will start a Jupyter Notebook environment that you can access from your web browser.  

Run the following command in your terminal:  

```bash
docker run -p 8888:8888 -v $(pwd):/home/jovyan/work data_exploration_management

```
---



### 🌐 Step 6: Access Jupyter Notebook  

Now that your container is running, you can access Jupyter Notebook by opening a web browser and navigating to:  

📌 **[http://localhost:8888](http://localhost:8888)**  

When prompted, enter the **token** displayed in your terminal output after running the container.  
If you need to retrieve the token again, run the following command inside the container:  

```bash
docker logs $(docker ps -q --filter "ancestor=data_exploration_management")
```
---

### 📊 Step 7: Explore the Notebooks  

In the Jupyter interface, open the **`data_exploration.ipynb`** notebook to begin the workshop activities.

#### 🏃‍♂️ Run the Provided Scripts  
You can also explore and execute the following files for additional functionality:  
- **`dataset.ipynb`** – Additional dataset exploration and manipulation.
- **`download_from_hpc.py`** – Script for downloading datasets from HPC.
- **`upload_to_hpc.py`** – Script for uploading data to HPC.
- **`titanic.csv`** – Example dataset for visualization and exploration.

 #### 📊 **About the Titanic Dataset**  
The **Titanic dataset** used in this notebook contains data about passengers aboard the RMS Titanic. This dataset includes several columns such as:
- **`Age`** – The age of the passenger.
- **`Fare`** – The amount the passenger paid for the ticket.
- **`Survived`** – Whether the passenger survived (1) or not (0).
- **`Pclass`** – The class of the ticket (1st, 2nd, or 3rd class).
- **`Sex`** – Gender of the passenger.
- **`Embarked`** – Port of embarkation.

The dataset is used to explore patterns such as:
- The **age distribution** of passengers.
- The relationship between **fare** and **age**.
- The survival rates across different **passenger classes**.

#### 📌 **Data Source**  
The dataset used in this workshop is based on the Titanic passenger data, which was originally made available as part of the **Kaggle Titanic: Machine Learning from Disaster** competition.  
You can access the original dataset here:  
- [Kaggle Titanic Dataset](https://www.kaggle.com/c/titanic/data)

#### 📊 Observe Data Visualizations  
Once you run the notebooks, you will be able to:  
✅ Visualize dataset distributions using **histograms**.  
✅ Explore relationships between variables using **scatter plots**.  
✅ Use **box plots** to analyze data trends and outliers.  
✅ Generate **interactive visualizations** within Jupyter Notebook.  

---


## 🔜 Next Steps  

After completing **Part 1**, you’ll be ready to move on to **Part 2**, where we explore using **High-Performance Computing (HPC)** for data exploration and management. 🚀  

In **Part 2**, you will:  
✅ Learn how to **access and use an HPC system** for large-scale data processing.  
✅ Transfer data between **your local machine and HPC clusters**.  
✅ Run **Jupyter Notebook on HPC** to handle **larger datasets and computations**.  
✅ Optimize workflows for **efficient data exploration and model training**.  

Stay tuned for the next section!  

---

### 🎯 Happy Coding! 😊

💡 **Note:**  
If you are new to coding, data visualization, data analysis, or data manipulation, please check out the [Lab Guide](https://github.com/decalyu/Data-Exploration-Management/wiki/Lab) before you start!
# 🚀 Running Docker Images as Singularity Containers on UCSD Expanse 🌟

Harnessing the power of Docker images within the Expanse supercomputer environment is achievable through Singularity containers. This guide will walk you through the process of converting a Docker image from a Docker registry into a Singularity image and running it on Expanse.

## 🎯 Objectives

By the end of this tutorial, you'll:

- **Access Expanse**: Log in to the Expanse system.
- **Load Singularity**: Ensure the Singularity environment is ready.
- **Convert Docker Image**: Transform a Docker image into a Singularity image.
- **Run Singularity Container**: Execute the container on Expanse.
- **End Session**: Properly terminate your session.

## 🛠️ Prerequisites

Before proceeding, ensure you have:

- **An Expanse Account**: If not, request one through the ACCESS Allocation Request System or contact consult@sdsc.edu for a Trial Account.
- **Basic Unix Knowledge**: Familiarity with basic Unix commands.
- **Docker Image**: The Docker image you wish to convert and run.

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

## 🔄 Step 3: Converting Docker Image to Singularity

1. **Pull Docker Image**:
   - Use Singularity to pull the Docker image directly from the Docker registry:

     ```bash
     singularity pull docker://your_docker_image
     ```

   - Replace `your_docker_image` with the name of the Docker image you wish to convert.

   - Singularity will download the Docker image and convert it into a Singularity Image File (SIF).

2. **Verify Conversion**:
   - List the files to ensure the `.sif` file is created:

     ```bash
     ls -lh
     ```

   - You should see a file with a `.sif` extension corresponding to your Docker image.

## 🚀 Step 4: Running Singularity Container

1. **Run the Container**:
   - Execute the Singularity container interactively:

     ```bash
     singularity shell your_image.sif
     ```

   - Replace `your_image.sif` with the name of your Singularity image file.

2. **Run a Command Inside the Container**:
   - To run a specific command within the container:

     ```bash
     singularity exec your_image.sif your_command
     ```

   - Replace `your_command` with the command you wish to execute inside the container.

## 🚪 Step 5: Ending the Session

1. **Exit the Container**:
   - If you are inside an interactive shell, type `exit` to leave the container.

2. **Terminate the Singularity Session**:
   - Ensure all processes are complete, and the container has stopped.

## 🎉 Congratulations!

You've successfully converted a Docker image to a Singularity container and run it on Expanse. For a visual walkthrough, you might find this webinar helpful:

[Singularity – Containers for Scientific and High-Performance Computing](https://www.youtube.com/watch?v=Cjbc7QO_PiY)
