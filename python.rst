.. _Narvi python:
=====================
Using python on narvi
=====================



As cluster's basic operating system is quite old, therefore also its default
python installation is ancient. That's why when working with python you should
almost always start with loading suitable anaconda module and creating
environment for your current python project. Otherwise you'll end up with a mess
with broken python & libraries sooner or later. (You might still end up with it)

So start with either with:

.. code-block::
    module load Miniconda3
 
# or
 
.. code-block::
    module load local-anaconda

The first one is "mini-anaconda" specifically ment for creating your own
environments and second one is locally maintained quite often updated and
propably has some of useful modules already installed. But either way you'll start
with more recent python and pip and with local-anaconda already have several python modules e.g.
cuda and tensorflow already installed.

If/when you'll need to add some other python modules best way to proceed is to create your own anaconda environment "on top" of that:

.. code-block::
    conda create -n my-env python numpy cuda ...
    # Let's activate newly created environment
    source activate my-env
    # now you can add either conda packages or plain python packages with
    conda install keras=2.4.3
    pip install picos

You'll need to activate environment always before using it.

In case you want to deactivate it e.g. to create other one use
source deactivate myenv

Your own environments are installed by default to your home-directory ~/.local so in case you get problems that's where you have start cleaning ;-)

Listing all environments known to conda:
conda env list

And so on ...

