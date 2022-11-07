
================
Matlab
================

Current default Matlab version is R2020a

We don't use Matlab Distributed Computing in cluster, so matlab jobs are in practice single compute-node jobs.

If you want to use several cores in one node you'll have to:

    Allocate required number of core via slurm (e.g. --cpus-per-task)
    Start allocated number of workers on compute-node (parpool (CPUs) in your matlab code)
    Parallelize your code&data (e.g. parfor loops and so on)

If you'd like to scale up further, you'll need to be able to split job into smaller independent parts, which can run on separate slurm jobs.

You might want to investigate Mathworks documentation on parallel computing.


Matlab parallel example
-----------------------

First we'll allocate some CPU's on some compute-node with slurm

.. code-block::

    #!/bin/bash
    #SBATCH -J Matlab-job-example
    #SBATCH --output=Slurm-output.txt
    #SBATCH --mail-user=user.name@tut.fi
    #SBATCH --mail-type=END
    #SBATCH --time=00:15:00
    #SBATCH --mem=64
    #SBATCH --ntasks=1
    #SBATCH --cpus-per-task=8
 
    module load matlab
    matlab -nodisplay -r "Matlab-parcluster"


We'll need to inform matlab about reserved CPU's
Matlab-parcluster.m:
.. code-block::
    myCluster = parcluster('local');
    % We'll read number of allocated CPUs from environment
    myCluster.Numworkers = str2num(getenv('SLURM_CPUS_ON_NODE'));
 
    % Then pool to local cluster
    parpool (myCluster.Numworkers);
 
    % Now we should be able to use parfor etc.
    ...
