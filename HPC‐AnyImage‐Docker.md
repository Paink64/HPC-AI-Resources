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
