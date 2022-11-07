
================
Lumerical FDTD
================

Current FDTD version is 8.18

This is the workflow using your local computer as a modelling and cluster as tool running simulations:

    Create model & transfer it to cluster propably some project related directory.
    Create/modify suitable batch-script  to run simulation.
    Transfer results to local computer for analyzing results.

Parallel example
----------------

First we'll allocate some CPU's from compute-nodes. ( e.g. using 4 nodes and one CPU per node)
lumerical slurm script
.. code-block::
    #!/bin/bash
    #SBATCH -J Lumerical-test
    #SBATCH --time=0:30:00
    #SBATCH --mem=2048
    #SBATCH --nodes=4
    #SBATCH --tasks-per-node=1
    #SBATCH --output=slurm-output.log
    #SBATCH --mail-user=my-email-address@tuni.fi
    #SBATCH --mail-type=END
    #SBATCH --partition=parallel
 
    module load lumerical
 
    JOBNAME=./my-lumerical-model.fsp
    $LUMERICAL_ROOT/mpich2/nemesis/bin/mpiexec -n $SLURM_NTASKS $LUMERICAL_ROOT/bin/fdtd-engine-mpich2nem $JOB


Using local GUI to submit jobs to cluster
-----------------------------------------

This is still work in progress.


This is something that should be doable according to https://support.lumerical.com/hc/en-us/articles/360026165714.


First you'll need to configure putty access to cluster like https://kb.lumerical.com/en/install_linux_running_simulations.html#4.



