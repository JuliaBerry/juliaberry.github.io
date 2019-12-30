---
layout: default
title:  JuliaBerry&#58; Julia on the Raspberry Pi
---

JuliaBerry is an organisation that brings together various resources for using the [Julia language](http://julialang.org/) for the [Raspberry Pi](https://www.raspberrypi.org/).

<div class="text-center"><iframe width="560" height="315" src="https://www.youtube.com/embed/EvJ-OvTC5eE" frameborder="0" allowfullscreen></iframe></div>

# Installing Julia (Recommended)

The easiest way to install Julia is by downloading the 32-bit (ARMv7-a hard float) prebuilt binary from [the JuliaLang website](https://julialang.org/downloads/).

An older version of Julia (1.0.3) is also available via `apt` in Raspbian, we hope to update this to the latest version in the near future. (This is the easiest way to install Julia and it adds Julia to PATH automatically.)

    sudo apt install julia

Please read below if you would like to compile Julia instead of installing Julia using the methods above.

# Compiling Julia

If you have installed Julia following the instructions above, there is no need to compile Julia. This method takes a very long time and takes up a lot of storage.

For those who are interested in compiling Julia, instructions can be found [over here](compile.md)

# IJulia notebook 
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

# Getting Started

To get started with Julia, please follow the link [here](https://julialang.org/learning/) to start learning!

# Questions/issues

We do not have a dedicated mailing list, however questions can be posted to the [Julia discourse](https://discourse.julialang.org).

Issues should be filed with the relevant packages: if in doubt which package is appropriate, please ask on the above mailing list.

If you would like to contribute a new package to the JuliaBerry org, open an issue on the repository in question and ping [@aviks](https://github.com/aviks) or [@simonbyrne](https://github.com/simonbyrne).

If you have any comments or suggestions for the website, please open an issue [here](https://github.com/JuliaBerry/juliaberry.github.io/issues).
