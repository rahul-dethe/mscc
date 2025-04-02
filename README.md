Guide to run MSCC Applications on NSM Systems.


1) Log in to the NSM System
   (If you don't have one please drop a mail to mscc-support@cdac.in)

2) After successful login 

   I) Interactive Mode:
      salloc -N 1 -p (partition name) --exclusive
      squeue --me
      ssh (node name)
   ![image](https://github.com/user-attachments/assets/5bf3d212-4fad-421f-9b27-cf9ab48c6d9d)


Step 1: Load the application.
Command: module load MSCC/ann-ci

Step 2: Create input and bond order files (keep both files in same place)

Step 3: Create a slurm script.

#!/bin/bash
#SBATCH --job-name=sys14
#SBATCH --nodes=1
#SBATCH --exclusive
#SBATCH --partition=cpu
#SBATCH --time=48:00:00
#SBATCH --output=%j.out
#SBATCH --error=%j.err

module load MSCC/ann-ci
cd $SLURM_SUBMIT_DIR
exe.py <your_inputfile>  

Step 4: Execute the slurm script to start the job.
Command: sbatch script.sh



Important commands:
module avail | grep -i MSCC: To see all MSCC applications which are currently available on an NSM system. 
sinfo: To see partition names.
