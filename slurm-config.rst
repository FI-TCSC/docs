
================
Slurm configuration
================

Current configuration:
================

Compute nodes are shared to a few different partitions, which are for slightly different use and have different limits for jobs:
test    everybody   1   8   4h  For short "testing" jobs. This should have shortest queueing times.

normal
    everybody -Students 8   Unlimited   7 days  For "normal" jobs not requiring anything too special e.g. huge parallelization, GPU'
parallel    parallel-group members  Unlimited   Unlimited   7 days  For large parallel jobs requiring more than four nodes per task.
gpu gpu-group members   Unlimited   Unlimited   7 days  For jobs, which require GPGPU's. Currently we have limitation of 12 simultaneous GPU allocations per user.
grid    grid-users  Unlimited   Unlimited   7 days  This is only for jobs coming through FGCI-grid, we are part of consortium.

Access to Parallel- and GPU-partitions needs to be requested from TCSC-support



CPU-pinning
=============

Please note that slurm is forcing CPU-pinning, which means that if you have reserved only one CPU-core, that's what you get!

e.g. Matlab still sees that node has 24 cores and might spawn 24 threads, but kernel will put those all on that one poor core →

very little work gets done because of all we have time to do is change thread running on core!


Only Normal-, Test- and grid-partitions exists currently.

Some specifics which have popped up:
===================================
Job TimeLimit

Currently Timelimit for normal- and grid-partition is 7 days max. Default Timelimit for jobs without specifications is two hours.

For test-partition maximum is two hours and default is 15 minutes. Also there is OverTimeLimit: time to wait after jobs reservation has expired before actually killing it. This is currently 15 minutes.

