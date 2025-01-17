# 🚀 Welcome to Your First Python Program on Expanse! 🌟

Embarking on your High-Performance Computing (HPC) journey is both exciting and rewarding. Let's dive into a simple "Hello, World!" tutorial using Python on UC San Diego's Expanse supercomputer. We'll guide you step-by-step, making it engaging and straightforward. Ready? Let's go! 🎉

---

## 🎯 Objectives

By the end of this tutorial, you'll:

- **Log in** to Expanse.
- **Identify** your project ID.
- **Write** a simple Python "Hello, World!" program.
- **Submit** and **run** your program on Expanse.

---

## 🛠️ Prerequisites

Before we begin, ensure you have:

- **An Expanse Account**:
  - If not, you can request one through the [ACCESS Allocation Request System](https://access-ci.org/about/get-started/#start) or request a Trial Account from SDSC by contacting consult@sdsc.edu.
- **Basic Unix Knowledge**:
  - Familiarize yourself with basic Unix commands. A helpful resource is available [here](https://github.com/sdsc-hpc-training-org/basic_skills).

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

## 🆔 Step 2: Identifying Your Project ID

1. **Use the `expanse-client` Utility**:
   - After logging into Expanse, use the following command to list your available projects:

     ```bash
     expanse-client user
     ```

   - This command will display information about your user account, including the projects you're associated with. Look for the `Project` or `Account` field to find your project ID.

   - For example, the output might look like:

     ```
     Resource  expanse

     ╭───┬────────────┬───────┬─────────┬──────────────┬──────┬───────────┬─────────────────╮
     │   │ NAME       │ STATE │ PROJECT │ TG PROJECT   │ USED │ AVAILABLE │ USED BY PROJECT │
     ├───┼────────────┼───────┼─────────┼──────────────┼──────┼───────────┼─────────────────┤
     │ 1 │ username   │ allow │ csd123  │ TG-TRA123456 │    5 │     50000 │               5 │
     │ 2 │ username   │ allow │ sds456  │ TG-TRA789012 │    0 │     40000 │           10182 │
     ╰───┴────────────┴───────┴─────────┴──────────────┴──────┴───────────┴─────────────────╯
     ```

   - In this example, `csd123` and `sds456` are your project IDs.

---

## 📝 Step 3: Writing the "Hello, World!" Program

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

## 📝 Step 4: Running the "Hello, World!" Program

1. **Create a SLURM Batch Script: SLURM manages job submissions on Expanse. Create the Batch Script**:
   - Create a new file named `hello_job.slurm`:

     ```bash
     nano hello_job.slurm
     ```

2. **Add the Following Content**:
   - Replace `your_project_id` with the project ID identified earlier:

     ```bash
     #!/bin/bash
     #SBATCH --job-name=hello_exp
     #SBATCH --output=hello_output.txt
     #SBATCH --partition=debug
     #SBATCH --account=your_project_id
     #SBATCH --nodes=1
     #SBATCH --ntasks=1
     #SBATCH --time=00:05:00

     module load cpu
     module load python

     python hello.py
     ```

   - Save and exit the editor.

---

## 🚀 Step 5: Running the Program

1. **Submit the Job**:
   - Submit your job to the queue:

     ```bash
     sbatch hello_job.slurm
     ```

2. **Check Job Status**:
   - Monitor your job's status:

     ```bash
     squeue -u your_username
     ```

     Replace `your_username` with your actual username.

3. **View Output**:
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
