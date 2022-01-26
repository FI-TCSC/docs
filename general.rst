
================
Cluster overview
================

Shared resource
===============

Narvi is a joint installation of TCSC member faculties.
It is now available to all Tuni researchers.

As of 2016, Narvi is part of `FGCI - Finnish Grid and Cloud
Infrastructure <https://www.csc.fi/-/fgci>`_ (predecessor of `Finnish
Grid Infrastructure <http://www.csc.fi/tutkimus/Laskentapalvelut/gridymparisto/fgi>`_).
Through the national grid and cloud infrastructure, Narvi also becomes
part of the European Grid Infrastructure.

Hardware
========

Frontends: narvi.cc.tut.fi and narvi-shell.cc.tut.fi

    * 24 cores E5-2620
    * 128GB memory

Compute nodes:

    25 HP SL230 nodes with 16 cores E5-2670 and 128GB memory (me55-me102)
    80 Dell M630 nodes with 24 cores E5-2680 v3 and 64GB memory (me151-280)
    40 Dell C6320 nodes with 24 cores E5-2680 v3 and 256GB memory (na01-na40)
    20 Dell C6420 nodes with 40 cores Xeon Gold 6148 with at least 400GB memory (na41-na60)
    8  Dell C6420 nodes with 40 cores Xeon Gold 6248 with at least 400GB memory (na61-na68)
    3  Dell C6525 nodes with 64 cores AMD EPYC 7502 with 512GB memory (na69-na72)
    18 Dell C4130 ja C4140 GPU-nodes with 4 NVIDIA Tesla P100 or V100 GPUs with 12-32GB per GPU (nag02-nag19)
    1  Dell R740 with 3 Quadro RTX 8000 with 45GB per GPU (nag20)

Storage:

    ~90TB /home -partition
    500TB /lustre partition for computation data.

All computing nodes are identical in respect to software and
access to common file system, although cuda drivers are only on gpu-nodes. Each
node has its own unique host name and ip-address.

Networking
==========

The cluster has two internal networks: Infiniband for MPI and file-IO
and Gigabit Ethernet for everything else like batch-system communication and ssh.

The internal networks are unaccessible from outside. Only the login nodes
have an extra Ethernet connection to outside.

Software
========

The cluster is running open source software infrastructure: CentOS 7,
with SLURM as the scheduler and batch system.

