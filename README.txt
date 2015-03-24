Pygr README
===========

Introduction
------------

Pygr is an open source software project used to develop graph database 
interfaces for the popular Python language, with a strong emphasis 
on bioinformatics applications ranging from genome-wide analysis of 
alternative splicing patterns, to comparative genomics queries of 
multi-genome alignment data.

For more information see

http://pygr.org

Latest Release
--------------

http://code.google.com/p/pygr/downloads/list

Documentation
-------------

This distribution includes the full Pygr documentation source,
but you will need the Sphinx documentation tool to build the
formatted docs.  You can get Sphinx via:

easy_install -U Sphinx

To build HTML versions of the docs using Sphinx:
cd doc
make html

The docs are also available online:

http://pygr.org/docs/latest-release/

Core Prerequisites
-----------------

1) Python >= 2.3 

To build Pygr from source code, you need Pyrex

Apps Prerequiites
-----------------
	
MySQL-python >= 1.2.0
MySQL >= 3.23.x  

Note: While pygr's core functionality is solely dependent on a sane python environment, the aformentioned apps requirements must be installed if one wishes to utilize the apps modules and test code. 

Supported Platforms
-------------------

In theory, pygr should work on any platform that adequately supports python.

Here are the OS's we've successfully tested on:

o Linux 2.2.x/2.4.x
o OS X 
o OpenBSD
o Windows XP

Installation
------------

Installing pygr is quite simple. 

1) tar -xzvf pygr-0.3.tar.gz 
2) cd pygr
3) python setup.py install 

Once the test framework has completed successfully, the setup script
will install pygr into python's respective site-packages directory. 
If you don't want to install pygr into your system-wide site-packages,
replace the "python setup.py install" command with
"python setup.py build".  This will build pygr but not install it
in site-packages.

IGB Installation -- CentOS 5 and 6, python 2.6
==============================================
Ensure that you have sourced the ${MOTIFMAP_ENV}/profile before
proceeding. This should point to the absolute path of the 
motifmap-devel checkout


To compile, issue the following command

	LDFLAGS="-L${MOTIFMAP_ENV}/lib64" python setup.py build

Pyrex warnings are normal and should compile to completion if you
are using gcc 4.1.2. If your system does not have this version, 
you will need to update your PATH and LD_LIBRARY_PATH to point
to the gcc/4.1.2 that's shipped with motifmap-devel

	export PATH=${MOTIFMAP_ENV}/deps/gcc/4.1.2/bin:$PATH
	export LD_LIBRARY_PATH=${MOTIFMAP_ENV}/deps/gcc/4.1.2/lib:$LD_LIBRARY_PATH

To install, issue the following command

	LDFLAGS="-L${MOTIFMAP_ENV}/lib64" python setup.py install

This should install the pygr module under

	${MOTIFMAP_ENV}/lib64/python2.6/site-packages


IGB Installation -- CentOS 6 and python 2.7
===========================================

Enter the src directory of motifmap-devel 

    cd codebase/motifmap-devel/src/

If the pygr checkout doesn't exist, make sure to run the pull-submodules.sh
script at the root of the checkout, ie, MOTIFMAP_ENV folder

Now go into the pygr folder and source the latest python 2.7 profile
    cd pygr
    source /auto/igb-libs/linux/centos/6.x/x86_64/profiles/python_2.7.6 

Remove (if necessary) the following files
    rm pygr/cdict.c pygr/cnestedlist.c pygr/seqfmt.c

Install correct version of pyrex:
    easy_install pyrex==0.9.8.6

Build and install pygr
	python setup.py build
    python setup.py install

Run the test code at the root of the checkout
    python src/pyrexes/pygr-testcode.py
    
The output should be like the following if the compilation and installation was correct
    /auto/igb-libs/linux/centos/6.x/x86_64/pkgs/python/2.7.6/lib/python2.7/site-packages/pygr-0.8.2-py2.7-linux-x86_64.egg/pygr/__init__.pyc
    Chrom:chr1, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x26515f0>
    Chrom:chr10, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x2651488>
    Chrom:chr11, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x7f673dd0f9e0>
    Chrom:chr12, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x2651488>
    Chrom:chr13, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x7f673dd0f9e0>
    Chrom:chr14, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x2651488>
    Chrom:chr15, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x7f673dd0f9e0>
    ... more ...
    Chrom:GL172637, msa: <pygr.nlmsa_utils.EmptySlice instance at 0x565b758>
    ... more ...


Using Pygr
----------
Check out the tutorials in the online docs!

Pygr contains several modules imported as follows:
from pygr import seqdb # IMPORT SEQUENCE DATABASE MODULE

If you did not install pygr in your system-wide site-packages, you 
must set your PYTHONPATH to the location of your pygr build.
For example, if your top-level pygr source directory is PYGRDIR then
you'd type something like:
setenv PYTHONPATH PYGRDIR/build/lib.linux-i686-2.3
where the last directory name depends on your specific architecture.


License
-------

New BSD license.

Author
------
Chris Lee <leec@chem.ucla.edu> and the rest of the Pygr developer team.
Please see http://code.google.com/p/pygr for a current list
of the participating developers.

Also see http://github.com/cjlee112/pygr/ for a list of other
developers who have created their own branches of the Pygr
git repository.


