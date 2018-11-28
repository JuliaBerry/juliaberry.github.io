---
layout: default
title:  JuliaBerry&#58; Julia on the Raspberry Pi
---

JuliaBerry is an organisation that brings together various resources for using the [Julia language](http://julialang.org/) for the [Raspberry Pi](https://www.raspberrypi.org/).

<div class="text-center"><iframe width="560" height="315" src="https://www.youtube.com/embed/EvJ-OvTC5eE" frameborder="0" allowfullscreen></iframe></div>

# Installing Julia

Julia is now available as part of Raspbian: the easiest way to install it is via
```
sudo apt update
sudo apt install julia
```

Alternatively, you can download the "ARMv7 32-bit hard float" binary (Pi 2 and 3 only) from the [JuliaLang downloads](http://julialang.org/downloads/). Note there are currently some known issues with these ([#17549](https://github.com/JuliaLang/julia/issues/17549), [#18816](https://github.com/JuliaLang/julia/issues/18816) and [#20936](https://github.com/JuliaLang/julia/issues/20936)), so installing via `apt` is recommended.

~~If you want to compile it from source, see the [Julia ARM readme](https://github.com/JuliaLang/julia/blob/master/README.arm.md).~~

# Compiling Julia

Instructions can be found [over here](compile.md)

# IJulia notebook

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

# Questions/issues

We do not have a dedicated mailing list, however questions can be posted to the [Julia discourse](https://discourse.julialang.org).

Issues should be filed with the relevant packages: if in doubt which package is appropriate, please ask on the above mailing list.

If you would like to contribute a new package to the JuliaBerry org, open an issue on the repository in question and ping [@aviks](https://github.com/aviks) or [@simonbyrne](https://github.com/simonbyrne).

If you have any comments or suggestions for the website, please open an issue [here](https://github.com/JuliaBerry/juliaberry.github.io/issues).
