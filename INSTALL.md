# Installation of Piramid

Updates by: Dave W. Wright
Date: 10 NOvember 2021

## Installation on Ubuntu 20.04

### Preparation

I used clean conda environment to give me somewhere safe to make new OpenBabel library files and a PATH isolated from my working environment.

In the instructions below I will use the `$CONDA_PREFIX` environment varieable to refer to the conda directoty storing used for this install environment (e.g. `/home/dave/miniconda3/envs/environment_name/`).
This is set when you activate the relevant environment in conda.

I also created a source directory to store the code versions as downloaded, this will be refered to as `$src_dir`.

### Install instructions

Move into a suitable directory for code download - `cd $src_dir`.

Download version 2.4.x of OpenBabel:
```
git clone git@github.com:openbabel/openbabel.git
cd openbabel
git fetch --all --tags
git checkout origin/openbabel-2-4-x
```

Build OpenBabel and install in a suitable location:
```
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=$CONDA_PREFIX
make
make install
```
Note: For speed you can use the `-j N` flag to make where `N` is the number of cores to use in compilation.

Move back to source directory and download Piramid:

```
cd $src_dir
git clone git@github.com:kuano-ai/piramid.git
cd piramid
```

Compile:
```
cmake CMakeLists.txt
make
```

Note: `make install` does not make a viable version it cannot find the OpenBabel library.

"Install" - in this case make a symlink in the PATH:

```
ln -s $src_dir/piramid/piramid $CONDA_PREFIX/bin
```

## Original installation instructions

INTRODUCTION AND REQUIREMENTS

The following tools are required to compile PIRAMID:

	- The latest version of the OpenBabel source code (at least version 2.3)
	- A C++ compiler (like g++) 
	- A makefile system (like GNU make) 
	- CMake system (www.cmake.org)

If you want to install globally on your system, you will need root access, and should follow these instructions.


INSTALL GLOBALLY (YOU NEED ROOT ACCESS)

(1) Open a command window, and decompress the downloaded file with following command:

> tar -xvf piramid-1.0.2.tar.gz

This will create a folder called 'piramid-1.0.2'. 

(2) You now need to configure and compile PIRAMID. Run the following commands, one after the other:

> cd piramid-1.0.2
> cmake CMakeLists.txt
> make

(3) If you have root permissions, you can install openbabel globally. As root, run the following command:

> make install
> make clean


