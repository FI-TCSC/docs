
================
Slurm
================
So FGCI-cluster is using slurm as batch-queue system.

While there is a lot of magnificient documentation e.g. Slurm's own

For more detailed info about our configuration please refer to configuration.


    Simple serial job
    Parallel job
    Interactive session
    Notes about resource reservations

Below are some basic examples of usage:

First you'll have to create some job-script which describes resources that job needs and does the actual execution.

Simple serial job
===============
.. code-block::
	#!/bin/bash
	#
	# At first let's give job some descriptive name to distinct from other jobs running on cluster
	#SBATCH -J My-test
	#
	# Let's redirect job's out some other file than default slurm-%jobid-out
	#SBATCH --output=slurm.out
	#SBATCH --error=slurm.err
	#
	# We'll want mail notifications from job errors and ending
	#SBATCH --mail-user=firstname.lastname@tut.fi
	#SBATCH --mail-type=END
	#
	# We'll want to allocate just one cpu from some node for this job
	#SBATCH --ntasks=1
	#SBATCH --cpus-per-task=1
	#
	# We'll want to reserve 2GB memory for job (per node), and
	# we estimate that job should finish in maximum of 8 hours and 15 minutes.
	#SBATCH --time=8:15:00
	#SBATCH --mem=2048
	 
	# Then actual program, commands e.g.
	 
	echo "Starting job on `uname -n` at `date --rfc-3339=seconds`
	./my_own_code --with-parameters=1,4,55

Then you'll submit that code with command:
	sbatch serial-job.sh

Parallel job
========
For parallel job we'll just need to change resource allocations of the job:

.. code-block::
	...
	# We'll want to allocate four cpu's from two separate nodes (totaling eight CPU's) for this job
	#SBATCH --ntasks=2
	#SBATCH --cpus-per-task=4
	#SBATCH --tasks-per-node=1
	 
	# We'll want to reserve 16GB memory for job (per node, so 4G per thread), and
	# we estimate that job should finish in maximum of 3 days.
	#SBATCH --time=03-0:0:0
	#SBATCH --mem=16384
	 
	# If we'll use OpenMP in nodes internal communication then, we'll need to tell number of threads with
	export OMP_NUM_THREADS=$SLURM_CPUS_PER_TASK
	 
	module load openmpi
	mpirun myexecutable
	
Interactive session
==================
Interactive shell session in compute-node can be requested with:
.. code-block::
	srun --pty -J " Bash session" --partition=test --mem=10000 --time=4:0:0 /bin/bash -i

Notes about resource reservations
================================
As compute-nodes operating system also needs some memory to run, some of the
memory isn't allocatable by slurm.  This means that if you request e.g. 128G
memory, in practice you'll need to wait for node with 256G to be available. So
if it might be better to only request 126G if don't absolutely need 128G
To show memory available for slurm jobs on nodes.
.. code-block::
	scontrol show node |grep RealMemory

