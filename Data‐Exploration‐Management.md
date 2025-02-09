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
