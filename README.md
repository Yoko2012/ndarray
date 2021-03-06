ndarray: NumPy-friendly multidimensional arrays in C++
======================================================
[![Build Status](https://travis-ci.org/ndarray/ndarray.svg?branch=master)](https://travis-ci.org/ndarray/ndarray)

ndarray is a template library that provides multidimensional array
objects in C++, with an interface and features designed to mimic the
Python 'numpy' package as much as possible.

More information can be found in the [documentation at
ndarray.github.io/ndarray](http://ndarray.github.io/ndarray/).


Building from Git
-----------------

ndarray includes the Boost.NumPy library using git's "submodules"
feature.  When you clone the ndarray repository with git, you'll get
an empty Boost.NumPy directory.  Even if you don't plan to use
Boost.NumPy (which is required only if you want to build the
Boost.Python bindings for ndarray), it *is* necessary to checkout the
Boost.NumPy source (as parts of the build system is shared).  So,
immediately after cloning ndarray, you'll need to run:

git submodule update --init --recursive

From there, you'll be able to build ndarray and (optionally)
Boost.NumPy together just by running "scons" from the root of the
ndarray clone.

A partial cmake build has also recently been added, and we expect it to
eventually replace SCons as the recommended approach, but it does not yet
support building against Boost.NumPy to provide bindings for Boost.Python. 

To build with cmake, do:

    mkdir build
    cd build
    cmake ..
    make
    make test

Inclusion and testing of optional dependencies is controlled by NDARRAY_* cmake
options. Dependency resolution can be controlled by the PYBIND11_DIR,
EIGEN_DIR, and FFTW_DIR environment variables. For example, to build with an
alternate Eigen3 install location and disable FFTW testing replace `cmake ..`
with `EIGEN_DIR=/opt/local cmake -DNDARRY_FFTW=OFF ..`.

Building from Compressed Source
-------------------------------

GitHub's automatically generated tarballs and zip files don't include
the Boost.NumPy submodule or the git metadata needed to run "git
submodule", so these features can't be used to download ndarray.

When we post release downloads, however, we'll include the Boost.NumPy
source so they can be built directly.
