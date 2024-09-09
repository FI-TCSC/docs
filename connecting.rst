
====================
Connecting to Narvi
====================


All access to Narvi is via Secure Shell (ssh).

You can connect to ``narvi.tut.fi`` from the following kinds of computers: 
- Computers with centralized management by the IT Services, see Computer environment. When working outside of campuses, TUNI VPN must be used
- TUNI classroom and lab computers
- Students' own computers using eduVPN

.. note::

   Are you here for a `SciComp KickStart course <https://scicomp.aalto.fi/training/scip/winter-kickstart/>`_?  You just need to `make
   sure you have an account <accounts.html>`_ and then be able to connect
   via ssh (first section here), and you don't need to worry about the
   graphical application parts.  Everything else, will be discussed during course.

.. note::

   Narvi uses Tuni accounts, but since we don't use passwords, account needs to
   activated first and you need to provide your public ssh-key as instructed at
   `accounts <accounts.html>`_

.. seealso::

      The `shell crash course <https://scicomp.aalto.fi/scicomp/shell>`_ is a kind of prerequisite
      to this material.


Connecting via ssh
==================

Linux
-----

All Linux distributions come with an ``ssh`` client, so you don't need to do
anything.  To use graphical applications, use the standard ``-X`` option,
nothing extra is needed.::

  ssh narvi.tut.fi
  # OR, if your username is different from local machine:
  ssh username@narvi.tut.fi

Mac
---

``ssh`` is installed by default, same as Linux.  Run it from a terminal,
same command as Linux.  To run graphical applications, you need to
install an X server (XQuartz).

Windows
-------

You need to install a ssh client yourself:  `PuTTY <https://www.chiark.greenend.org.uk/~sgtatham/putty/>`__ is
the standard one.  If you want to run graphical programs, you need an X server on
Windows: see this
`link <http://www.geo.mtu.edu/geoschem/docs/putty_install.html>`_ for
some hints.  (Side note: putty dot org is an advertisement site trying to
get you to install something else.)

You should configure this with the hostname, username, and save the
settings so that you can connect quickly.

Nowadays with new Windows 10 builds you can also use its native openssh, so most of linux example's 
commands work out of box e.g. ssh-keygen and ssh. If you want still better linux compatibility, you could install 
WSL (=Windows Subsystem for Linux), which has about anything normal linux shell apart from kernel-services.

Advanced options
----------------

See the  `advanced ssh information <https://scicomp.aalto.fi/scicomp/ssh>`_ to learn how
to log in without a password, automatically save your username 
and more. It really will save you time.

``ssh`` is one of the most fundamental Linux programs: by using it
well, you can really do almost anything from anywhere.  The
``.ssh/config`` file is valuable to set up.  If ssh is annoying to
use, ask for some help in getting it working well.  



Exercise
--------

1. Connect to Narvi.  List your home directory and work directory
   ``$WRKDIR``.

2. Check the uptime and load of the login node: ``uptime`` and
   ``htop`` (``q`` to quit).  What else can you learn about the node?

3. Check what your default shell is: ``echo $SHELL``.  Go ahead and
   change your shell to bash if it's not yet (see below).


What's next?
============

The next tutorial is about `software and modules <https://scicomp.aalto.fi/modules>`__.
