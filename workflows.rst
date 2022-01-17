=========================
Remote workflows at Tampere University
=========================

.. note::

   The more specific remote access instructions for narvi is at
   `TCSC Eduuni wikispace <https://wiki.eduuni.fi/display/tuttcsc/Connecting+to+cluster>`__. 
   This page explains the options, including other systems.


.. note::

   How can you work from home?  For that matter, how can you work on more than your desktop/laptop while at work?  There are many options which trade off between graphical interfaces and more power.  Read more for details.

You have most likely created your own workflow to analyse data at TAU and most likely you are using a dedicated desktop workstation in Tampere. However, with increased mobility of working conditions and recent global events that recommend tele-working, you might be asking yourself: "how do I stop using my workstation at the dept, and get analysis/figures/papers done from home?".

The data analysis workflows from remote might not be familiar to everyone. We list here few possible cases, this page will expand according to the needs and requests of the users.

What's your style?
------------------

If you need the most power or flexibility, use Narvi for your data storage and computation. For prototyping and testing you can use your own workstation or maybe `Linux desktops <https://intra.tuni.fi/handbook/2677/2724/3229?role=staff&university=uni>`. Then to scale up, you can use the Narvi options: 4, 5, 6 which have access to the same data. (`Narvi account required <https://wiki.eduuni.fi/display/tuttcsc/User+Account>`__ for 4-6).

If you need simple applications with a graphical interface, try 3 (Remote desktop).

If you use your own laptop/desktop (1, 2), then it's good for getting started but you have to copy your data and code back and forth once you need to scale up.

Summary table for remote data analysis workflows
------------------------------------------------

   * Good for data security: 3, 4, 5, 6
   * Good for prototyping, working on the go, doing tests, interactive work: 1, 2, 3
   * Shares Narvi data (e.g. scratch folders): 4, 5, 6
   * Easy to scale up, shares software, data, etc: 4, 5, 6
   * Largest resources available 6 (medium: 5)


.. list-table::
   :header-rows: 1

   * * Workflow
     * Pros
     * Cons
     * Recommendation
     * Data on cluster
   * * 1. Own laptop/desktop computer
     * Can work from anywhere. Does not require internet connection.  You are in control.
     * Not good for personal or confidential data. Computing resources might not be enough. Accessing large data remotely stored at anywhere else might be problematic - you will end up having to copy a lot.  You have to manage software yourself.
     * Excellent for prototyping, working on the go, doing tests, interactive work (e.g. making figures). Don’t use it with large data or confidential / personal data.
     * N
   * * 2. University workstation/laptop
     * Same as above, plus same tools available as TUNI employer.
     * Same as above.
     * Same as above.
     * N
   * * 3. Remote desktop ( linux-desktop.tuni.fi )
     * Computing happens on remote. Data access happens on remote, so it is more secure.
     * Computing resources and storage space are limited.
     * Excellent for prototyping, working on the go, doing tests, interactive work (e.g. making figures). More secure access to data.
     * N
   * * 4. Interactive graphical session on `narvi-shell <https://wiki.eduuni.fi/display/tuttcsc/Narvi+Shell>` (ssh -X narvi-shell.tut.fi)
     * Graphical programs.
     * Lost once your internet connection dies, needs fast internet connection.
     * If you need specific graphical applications which are only on Narvi.
     * Y
   * * 5. Interactive command line session on Narvi HPC (ssh + srun)
     * Works from anywhere.  Can get lots of resources for a short time.
     * Limited time limits, must be used manually.
     * A general workhorse once you get comfortable with shell - many people work here + #6.
     * Y
   * * 6. Non-interactive batch HPC computing on Narvi (ssh + sbatch)
     * Largest resources, bulk computing
     * Need to script your computation
     * When you have the largest computational needs.
     * Y
   * * 7. Non-interactive batch HPC computing on CSC (ssh + sbatch)
     * Similar to #6 but at CSC
     * Similar to #6
     * Similar to #6
     * N


1. Own laptop/desktop computer
------------------------------

**Description**: Here you are the administrator. You might be working from a
cafe with your own laptop, or from home with a desktop. You should be able to
install any tool you need. As an TUNI employer you get access to many nice
commercial tools for your private computers. Visit: `Intra
<https://intra.tuni.fi/handbook/2677/11307/3234?role=staff&university=uni>`__
and https://tuni.onthehub.com/  for some options. 

**Pros**: Computing freedom! You can work anywhere, you can work when there is
no internet connection, you do not share the computing resources with other
users so you can fully use the power of your computer.

**Cons**: If you work with personal or confidential data, the chances of a data
breach increase significantly, especially if you work from public spaces. Even
if you encrypt your hard disks and even if you are careful, you might be
forgetting to lock your computer or somebody behind you might see which
password you type. Furthermore, personal computers have limited resources when
it comes to RAM/CPUs/GPUs. When you need to scale up your analysis, you want to
move it to an HPC cluster, rather than leaving scripts running for days.
Finally, although you can connect your Tuni folders to your laptop, when the
data size is too big, it is very inefficient to analyse large datasets over the
internet.

**Recommendation**: Own computer is excellent for prototyping data analysis
scripts, working on the go, doing tests or new developments. You shouldn’t use
this option if you are working with personal data or with other confidential
data. You shouldn’t use this option if your computational needs are much
bigger.

2. Tuni workstation
---------------

**Description**: As an university employer, you are usually provided with a
desktop workstation or with an laptop. With an TUNI-laptop you can apply for
administrator rights so basically everything you have read for option 1 above is
valid also in this case.  See "{Linux|Mac|Windows}" on `Tuni-intra
<https://intra.tuni.fi/handbook/2677/2724?role=staff&university=uni>`__.

**Pros/Cons/Recommendation**: see option 1 above.  But, when on TUNI networks/VPN,
you have easier access to TUNI storage systems.

3. Linux desktop
----------------------------------

**Description**: You might be working with very large datasets or with
confidential/personal data, so that you cannot or do not want to copy the data
to your local computer. Sometimes you use many computers, but would like to
connect to “the same computer” from remote where a longer analysis script
might be crunching numbers. 

**Pros**: The computing processes are not going to run on your local computer,
computing happens on remote which means that you can close your internet
connection, have a break, and resume the work where you left it. There is no
need to copy the data locally as all data stays on remote and is accessed as if
it was a desktop computer from the campus.

**Cons**: Desktop machines have a limited computing power. So they are great
for small prototyping, but for a large scale computation you might want to
consider HPC cluster. The desktop session is not kept alive forever.

**Recommendation**: Desktop is excellent when you need a graphic interactive
session and access to personal/confidential data without the
risks of data breach. Use desktop for small analysis or interactive development, we
do not recommend it when the executing time of your scripts starts to be bigger
than a 7 hours working day.

4. Interactive graphical session via narvi-shell
----------------------------------------------

**Description**: Sometimes what you can achieve with your own laptop or with
linux desktop is not enough when it comes to computing resources. However, your workflow
does not yet allow you to go fully automatic as you still need to manually
interact with the analysis process (e.g. point-click analysis interfaces, doing
development work, making figures, etc). An option is to connect to
narvi-shell.tut.fi with a graphical interface. This is usually done with ssh -X
narvi-shell.tut.fi. For example you can do it from a terminal within a Linux Desktop
session. Once connected to the narvi-shell node, you can launch desired software from there.

**Pros**: This is similar to the Linux-desktop case above (#3) without the computing
limitation imposed by it. 

**Cons**: If you connect from narvi-shell.tut.fi from your own desktop/laptop,
your internet connection might be limiting the speed of the graphical session
making it very difficult to use graphical IDEs or other tools. Move to Linux-desktop,
which optimises how the images are transferred over the internet. Interactive
sessions cannot typically last for for several days, if you need to run scripts that
have high computational requirements AND long time of execution, the solution
for you is to go fully non-interactive using Triton HPC with slurm (case #6)

**Recommendation**: This might be one of the best scenarios for working from
remote with an interactive graphical session. Although you cannot keep the
session open for more than 24 hours, you can still work on your
scripts/code/figures interactively without any limitation and without any risks
of data breaches. Narvi account required
<https://wiki.eduuni.fi/display/tuttcsc/User+Account>`__.


5. Interactive command line only session on Narvi
-----------------------------------------------------------------------

**Description**: sometimes you do not really need a graphical interface because
you are running interactively scripts that do not produce or need a graphical
output. This is the same case as sinteractive above, but without the limitation
of the 24h session. The best workflow is to: 1) connect to triton ``ssh
narvi.tut.fi`` 2) start a screen/tmux session that can be detached /
reattached in case you lose the internet connection or in case you need to
leave the interactive script running for days 3) request a dedicated
interactive terminal with command ``srun -p normal --time=HH:MM:SS
--mem=nnG --pty bash`` (see other examples at
https://scicomp.aalto.fi/triton/tut/interactive.html or
https://scicomp.aalto.fi/triton/usage/gpu.html for interactive GPU) 4) get all
your numbers crunched and remember to close it once you are done. Please note
that, if you have a dedicated Linux workstation at a department at TUNI, you
can also connect to your workstation and use it as a remote computing node
fully dedicated to you. The resources are limited to your workstation, but here
you won’t have the time constraint or the need to queue for resources if
Narvi’s queue is overcrowded. Narvi account required
<https://wiki.eduuni.fi/display/tuttcsc/User+Account>`__.

**Pros**: when you do not need a graphical interface and when you need to run
something interactively for days, this is the best option: high computing
resources, secure access to data, persistent interactive session. 

**Cons**: when you request an interactive command line session you are
basically submitting a slurm job. As with all jobs, you might need to wait in
the queue according to the amount of resources you have requested. Furthermore,
jobs cannot last more than 7 days. In general, if you have an analysis script
that needs more than 7 days to operate, you might want to identify if it can be
parallelized or split into sub-parts with checkpoints.

**Recommendation**: this is the best option when you need long-lasting
computing power and large data/confidential data access with interactive input
from the user. This is useful once you have your analysis pipeline/code fully
developed so that you can just run the scripts in command line mode. Post
processing/figure making can then happen interactively once your analysis is
over.

6. Non-interactive batch computing on Narvi
------------------------------------------------

**Description**: this is the case when no interactive input is needed to
process your data. This is extremely useful when you are going to perform the
same analysis code for hundreds of time. Please check more detailed
descriptions at https://scicomp.aalto.fi/triton/index.html and if you havent,
go through the tutorials https://scicomp.aalto.fi/triton/index.html#tutorials.
Narvi account required
<https://wiki.eduuni.fi/display/tuttcsc/User+Account>`__.

**Pros**: when it comes to large scale data analysis, this is the most
efficient way to do it. Having a fully non-interactive workflow also makes your
analysis reproducible as it does not require any human input which can
sometimes be the source of errors or other irreproducible/undocumented steps.

**Cons**: as this is a non-interactive workflow, this is not recommended for
generating figures or with graphical tools that does not allow “batch” mode
operations.

**Recommendation**: this is the best option when you need long-lasting parallel
computing power and large data/confidential data access. This is also
recommended from reproducibility/replicability perspective since, by fully
removing human input, the workflow can be made fully replicable. 

7. Non-interactive batch HPC computing at CSC
---------------------------------------------

**Description**: this case is similar to #6. You can read/learn more about this
option at https://research.csc.fi/guides

**Pro/Cons/Recommendation**: see #6.
