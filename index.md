---
layout: default
title:  JuliaBerry&#58; Julia on the Raspberry Pi
---

JuliaBerry is an organisation that brings together various resources for using the [Julia language](http://julialang.org/) for the [Raspberry Pi](https://www.raspberrypi.org/).

<div class="text-center"><iframe width="560" height="315" src="https://www.youtube.com/embed/EvJ-OvTC5eE" frameborder="0" allowfullscreen></iframe></div>

# Installation
Below, we go through three different methods of installing Julia on your Raspberry Pi.

### The recommended way - Download the prebuilt binary
To install the newest available version of Julia, download the 32-bit (ARMv7-a hard float) prebuilt binary from the [JuliaLang website](https://julialang.org/downloads/). Below is a sequence of commands that can be copy pasted into the command-line on the Raspberry Pi to:
1. Downloading julia 1.6.7 for the Raspberry Pi
2. Unpacking the downloaded `tar.gz` file
3. Deleting the compressed file
4. Making a folder `$HOME/.julia/my_installs`
5. Moving your Julia installation to `$HOME/.julia/my_installs`

```
curl https://julialang-s3.julialang.org/bin/linux/armv7l/1.6/julia-1.6.7-linux-armv7l.tar.gz --output $HOME/julia-1.6.7-linux-armv7l.tar.gz
tar -xzf $HOME/julia-1.6.7-linux-armv7l.tar.gz
rm $HOME/julia-1.6.7-linux-armv7l.tar.gz
mkdir -p $HOME/.julia/my_installs
mv $HOME/julia-1.6.7 $HOME/.julia/my_installs
```

If you want to install a different version, or to a different directory, adjust the commands as you see fit.  
Most users also want to add Julia to path. This is typically a manual step, and can be done in many ways. If you pasted exactly the lines above, you can add Julia to path by running the following commands:
```
echo '' >> $HOME/.profile
echo '#=== My own edits ===#' >> $HOME/.profile
echo 'PATH="$HOME/.julia/my_installs/julia-1.6.7/bin:$PATH"' >> $HOME/.profile
```

To load the version of `$HOME/.profile` with Julia on the path without restarting the shell, you can run
```
source $HOME/.profile
```
### The easy way - Via `apt`
Julia 1.5.3 is available via `apt` in Raspberry Pi OS. This adds `julia` to PATH automatically:

    sudo apt install julia

### The hard way - Compiling Julia from source
This is the most difficult method, and is not needed if one of the methods above worked for you. Building Julia from source on a Raspberry Pi takes a very long time, and takes up a lot of storage. But for those who are interested in compiling Julia, instructions can be found [over here](compile.md).

## Installing IJulia notebook 
This is **optional**, and is only for those who need [Jupyter Notebook](https://jupyter.org/).

Jupyter will need to be installed manually, as the automatic Conda installer does not work on the ARM architecture. Generally, running

    sudo apt install libzmq3-dev
    sudo pip3 install jupyter

at the shell should work. Then it should be sufficient to do

    Pkg.add("IJulia")

at the Julia REPL.


# Packages
The JuliaBerry org provides several Raspberry Pi-specific packages:

* [PiGPIO.jl](https://github.com/JuliaBerry/PiGPIO.jl): managing external hardware using GPIO pins.
* [PiCraft.jl](https://github.com/JuliaBerry/PiCraft.jl): manipulating Minecraft on the Raspberry Pi from Julia
* [SenseHat.jl](https://github.com/JuliaBerry/SenseHat.jl): interacting with the [Sense HAT](https://www.raspberrypi.org/products/sense-hat/).

# Getting Started with Julia
If you are new to Julia, welcome! We recommend heading over to [julialand.org/learning](https://julialang.org/learning/) to get started.

# Questions/issues
We do not have a dedicated mailing list, however questions can be posted to the [Julia Discourse](https://discourse.julialang.org).

Issues should be filed with the relevant packages on Github: if in doubt which package is appropriate, please ask on Discourse.

If you would like to contribute a new package to the JuliaBerry org, open an issue on the repository in question and ping [@aviks](https://github.com/aviks) or [@simonbyrne](https://github.com/simonbyrne).

If you have any comments or suggestions for the website, please open an issue [here](https://github.com/JuliaBerry/juliaberry.github.io/issues).
