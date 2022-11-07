
================
Compphys
================

Overview
--------
The compphys modules are a default set of slightly optimized builds of
compilers, libraries, and software useful for computational science. This
module package is available in TCSC's Narvi-cluster.

Loading CompPhys modules
------------------------

The modules should be accessible for every user by default. The compphys
software and libraries are set up under compphys/ -module names. You can load
the default set with the command::

    ml compphys/env/gnu

The modules can also be loaded separately, but there may be errors and/or
missing information on the prerequisite modules.


Compiler flags
--------------

The default set of compiler flags which is set when loading the module compphys/env/gnu is

-O3 -march=sandybridge -mtune=haswell -funroll-loops -mavx -msse4.2 -Wall -Wextra -Wconversion -pedantic -Wpointer-arith -Wcast-qual -Wmissing-declarations -pedantic -Winline -Wstrict-overflow=2 -Wfloat-equal -fopenmp -ftree-vectorize -fassociative-math -ffast-math -fPIC

If you wish to compile with some less optimization, try the module compphys/gccflags/safe which gives you

-O2 -funroll-loops -mavx -msse4.2 -Wall -Wextra -Wconversion -pedantic -Wpointer-arith -Wcast-qual -Wmissing-declarations -pedantic -Winline -Wstrict-overflow=2 -Wfloat-equal -fopenmp -ftree-vectorize -fPI


Software
--------

We've installed a bunch of different software used by the TUNI Computational Physics unit. This includes, e.g.,

| python | 3.6.7 | Python | compphys/sw/gcc/7.3.0/python | ✓ |
| perl   | 5.26.3.2603 | Perl | compphys/sw/prebuilt/perl/ | ✓ |
| git | 2.9.5 | Git | compphys/sw/gcc/7.3.0/git | ✓ |


Libraries
---------
| hdf5 | 1.10.4 | Hierachical Data Format. The best data format for scientific applications. | compphys/libs/gcc/7.3.0/hdf5/1.10.4-serial compphys/libs/gcc/7.3.0/hdf5/1.10.4-parallel  |
| eigen | 3.3.7 | C++ linear algebra library | compphys/libs/gcc/7.3.0/eigen |
| gsl | 2.5 | GNU Scientific Library | compphys/libs/gcc/7.3.0/gsl | 
| fftw | 3.3.8 | FFTW (The Fastest Fourier Transform in the West) | compphys/libs/gcc/7.3.0/fftw |
| libxc | 4.2.4 | A library full of different kinds of XC-functionals (for density functional theory calculations) | compphys/libs/gcc/7.3.0/libxc |
| tclap | 1.2.2 | C++ command line parser compphys/libs/gcc/7.3.0/tclap |    
| boost | 1.69.0 | Boost | compphys/libs/gcc/7.3.0/boost |

Boost.Python installed for Python 3.
Boost.MPI also installed.
Like
Janne Solanpää likes this
