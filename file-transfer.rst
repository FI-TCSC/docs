
================
Transfering files to and from cluster
================

There are few ways to transfer data in and out:

    * Directly with sftp/scp
    * mounting directory from cluster to your workstation with sshfs
    * accessing TUNI intra directory directly from cluster

From Linux-machine
===============

SCP/SFTP
-------------
You can copy your files to narvi-cluster with command scp that does not need any mounts.

For example copy one file from localhost to narvi 
.. code-block::
    scp yourfile narvi:/home/${USER}

Copy a directory from localhost to narvi
.. code-block::
    % scp -r yourdirectory narvi:/home/${USER}

You can use this also to other direction or between any other two hosts.

For more information
.. code-block::
    man scp

SSHFS
-------------
You can mount your homedirectory from narvi-cluster to your localhost
with command sshfs.

First create a directory where you mount your home from narvi
.. code-block::
    mkdir ${HOME}/narvi-home

Then use sshfs to mount your narvi-home to directory you just created 

This example asumes that your home in narvi is /home/$USER, if it is not that please change to correct one
.. code-block::
    sshfs ${USER}@narvi.tut.fi:/home/${USER} ${HOME}/narvi-home

When file transfers are ready and you don't need to have this mount, unmount narvi-home from your localmachine with command
.. code-block::
    fusermount -u ${HOME}/narvi-home

For more information

man sshfs
man fusermount

From Windows-machine
========

Moving files between your windows-machine and cluster might be easiest with WinSCP after you add you private-key to it.

Or then you should have your files on your INTRA -homedirectory so you access them directly on cluster frontend:

TUNI home&group -directories
-------------
You can access your TUNI-home and group directories directly on frontend nodes (narvi and narvi-shell):

.. code-block::
    # Let's acquire kerberos ticket for authentication:
    kinit username@AD.TUNI.FI
    Password for username@AD.TUNI.FI: (type your intra-password here)
    
    ls /tuni/home/username
    ...
    ls /tuni/groups/22702_Common
    ...

/tuni/groups directory contains all group directories which you have access, but you'll have to now the specific directory's name. So unless you have visited some directory /tuni/groups will be empty.

