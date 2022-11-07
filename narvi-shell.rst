
================
Narvi-shell
================

The narvi-shell computing environment is intended for interactive use of
scientific applications, usage of graphical application interfaces, and for
submitting jobs in Slurm job scheduling system. The narvi-shell environment is
a dedicated computing server and part of the Narvi cluster.

The narvi-shell system is a shared service for all Narvi users. For this
reason, there are specific rules and regulations for using the system, such as:

 * Current system load should be paid attention to when launching new applications.
 * The limit of maximum four computing cores/threads per user should not be exceeded when running applications locally.
 * Long computing jobs and jobs requiring more than four computing cores should be executing on the cluster using Slurm job scheduling system.

Logging on to narvi-shell
-------------------------

The narvi-shell system is connected with the Narvi cluster. You should use
your Narvi credentials (ssh keys) to access the system. Once you have set up
your own environment, you can logon to the narvi-shell system with your
preferred ssh tool, for example ::

    ssh -i .ssh/id_narvi narvi-shell.cc.tut.fi

Matlab
---------

Matlab can be started In single-thread mode with the singleCompThread
parameter, which is strongly recommended on narvi-shell.

How to start Matlab (in single-thread mode)::
    module load matlab

    matlab -singleCompThread

.. note::
    On narvi-shell, Matlab has been pre-configured to execute in single-thread
    mode by setting the default value of the global maxNumCompThreads variable to
    1. However, the maxNumCompThreads variable has been (deprecated) in recent
    Matlab versions, and it is not guaranteed to work in all cases.

Only very short Matlab test runs may be executed in multi-thread mode on
narvi-shell. This option is not recommended on narvi-shell, and close attention
should always be paid in order not to affect other users and/or their
applications.

How to start Matlab (in multi-thread mode)::

    module load matlab

    matlab

..Matlab starts..::

    >> maxNumCompThreads = 16

>> % Now ready to run on all cores


