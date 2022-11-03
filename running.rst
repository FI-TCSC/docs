
================
Running software
================

Running software with GUI (e.g. graphical matlab)
===============

Interactive usage with gui-software should be avoided if possible due to being slow and ineffective.

If you need still to do this, please use Narvi Shell propably with x2go or
xpra. You need to have X11-forward enabled on your SSH connection and working
X11 environment on your client machine (e.g. `VcXsrv` <https://sourceforge.net/projects/vcxsrv/>`_ , Xming or Cygwin/X for Windows).

Running software as a batch job
========
This is normal way to use cluster. Background jobs are managed by SLURM. So
you'll describe how much resources (CPUs, memory) your job needs and how to
actually run the job. Then slurm will locate best possible run time and place
and runs the job. Usually you'll want to have notification by email, if either
something goes wrong or when the job has finnished. There are some examples
about this on `separate page <slurm.html>`_. 


