# 🚀 Hello, Future HPC Enthusiast! Welcome to Expanse! 🌟

Embarking on your High-Performance Computing (HPC) journey is both exciting and rewarding. Let's dive into a simple "Hello, World!" tutorial using Python on UC San Diego's Expanse supercomputer. We'll guide you step-by-step, making it engaging and straightforward. Ready? Let's go! 🎉

---

## 🎯 Objectives

By the end of this tutorial, you'll:

- **Log in** to Expanse.
- **Write** a simple Python "Hello, World!" program.
- **Submit** and **run** your program on Expanse.

---

## 🛠️ Prerequisites

Before we begin, ensure you have:

- **An Expanse Account**:
  - If not, you can request one through the [ACCESS Allocation Request System](https://access-ci.org/about/get-started/#start) or request a Trial Account from SDSC by contacting consult@sdsc.edu.
- **Basic Unix Knowledge**:
  - Familiarize yourself with basic Unix commands. A helpful resource is available [here](https://github.com/sdsc-hpc-training-org/basic_skills/tree/master/basic_linux_skills_expanse).

---

## 🔑 Step 1: Accessing Expanse

1. **Open Terminal**:
   - On your local machine, open the terminal application.

2. **Connect via SSH**:
   - Use the following command to connect to Expanse:

     ```bash
     ssh your_username@login.expanse.sdsc.edu
     ```

     Replace `your_username` with your actual Expanse username. If prompted, enter your password.

---

## 📝 Step 2: Writing the "Hello, World!" Program

1. **Create a Directory**:
   - Organize your work by creating a new directory:

     ```bash
     mkdir hello_world
     cd hello_world
     ```

2. **Write the Program**:
   - Use a text editor like `nano` to create your Python script:

     ```bash
     nano hello.py
     ```

   - Then, type the following code:

     ```python
     print("Hello, World from Expanse!")
     ```

   - Save and exit by pressing `Ctrl + X`, then `Y`, and `Enter`.

---

## 🚀 Step 3: Running the Program

1. **Create a SLURM Batch Script**:
   - SLURM manages job submissions on Expanse. Create a script named `hello_job.slurm`:

     ```bash
     nano hello_job.slurm
     ```

   - Add the following content:

     ```bash
     #!/bin/bash
     #SBATCH --job-name=hello_exp
     #SBATCH --output=hello_output.txt
     #SBATCH --partition=debug
     #SBATCH --nodes=1
     #SBATCH --ntasks=1
     #SBATCH --time=00:05:00

     module load cpu
     module load python

     python hello.py
     ```

   - Save and exit the editor.

2. **Submit the Job**:
   - Submit your job to the queue:

     ```bash
     sbatch hello_job.slurm
     ```

3. **Check Job Status**:
   - Monitor your job's status:

     ```bash
     squeue -u your_username
     ```

     Replace `your_username` with your actual username.

4. **View Output**:
   - Once the job completes, view the output:

     ```bash
     cat hello_output.txt
     ```

   - You should see:

     ```
     Hello, World from Expanse!
     ```

---

## 🎉 Congratulations!

You've successfully run your first Python "Hello, World!" program on Expanse! Keep exploring and happy computing! 🌟

---

*For more detailed information, refer to the [Expanse User Guide](https://www.sdsc.edu/support/user_guides/expanse.html).*
