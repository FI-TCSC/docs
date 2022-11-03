
================
Misc slurm tips
================

Listing jobs running on particular node[s]
--------------------------------------
    squeue --sort=T,P,-S,-i --format="%i %P %j %u %C %D %m %f %t %M %l %e %R" --nodelist=nag\[02-09\]
List pending jobs on cluster
----------------------
    squeue --sort=S,Q --format="%8Q %.12i %.9P %.8j %.8u %.19S %.4D %12Y %R" --states=PENDING

