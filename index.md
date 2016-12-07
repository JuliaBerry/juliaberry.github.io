---
layout: default
title:  JuliaBerry&#58; Julia on the Raspberry Pi
---

JuliaBerry is an organisation that brings together various resources for using the [Julia language](http://julialang.org/) for the [Raspberry Pi](https://www.raspberrypi.org/).

<div class="text-center"><iframe width="560" height="315" src="https://www.youtube.com/embed/EvJ-OvTC5eE" frameborder="0" allowfullscreen></iframe></div>

# Installing Julia

Julia has started to provide support for the ARM architecture used by the Raspberry Pi since version 0.5.

## Prebuilt binary

For the Raspberry Pi 2 and 3, the easiest way to install Julia is to download the "ARMv7 32-bit hard float" binary from the [JuliaLang downloads](http://julialang.org/downloads/) page.

The current release (0.5.0) bundles a version of the libstdc++ library which is quite old, and can cause conflicts when using certain julia packages ([issue #18816](https://github.com/JuliaLang/julia/issues/18816)). This can be fixed by removing the file `lib/julia/libstdc++.so.6` from the extracted tree (it is not needed as a newer version is already installed on Raspbian).

This can all be accomplished by the following:

    wget https://julialang.s3.amazonaws.com/bin/linux/arm/0.5/julia-0.5-latest-linux-arm.tar.gz
    mkdir julia
    tar -xzf julia-0.5-latest-linux-arm.tar.gz -C julia --strip-components 1 --exclude libstdc++.so.6

Julia can then be run by

    julia/bin/julia

You may get a warning "WARNING: unable to determine host cpu name.": this can safely be ignored and should be fixed in the next release ([issue #17549](https://github.com/JuliaLang/julia/issues/17549)).

## Compiling from source

If you have a Raspberry Pi 1 or Zero, you will need to compile it from source. Instructions for this are available in the [Julia ARM readme](https://github.com/JuliaLang/julia/blob/master/README.arm.md).

# Packages

The JuliaBerry org provides several Raspberry Pi-specific packages:

* [PiGPIO.jl](https://github.com/JuliaBerry/PiGPIO.jl): managing external hardware using GPIO pins.
* [PiCraft.jl](https://github.com/JuliaBerry/PiCraft.jl): manipulating Minecraft on the Raspberry Pi from Julia
* [SenseHat.jl](https://github.com/JuliaBerry/SenseHat.jl): interacting with the [Sense HAT](https://www.raspberrypi.org/products/sense-hat/).

# Questions/issues

We do not have a dedicated mailing list, however questions can be posted to the [Julia discourse](https://discourse.julialang.org).

Issues should be filed with the relevant packages: if in doubt which package is appropriate, please ask on the above mailing list.

If you would like to contribute a new package to the JuliaBerry org, open an issue on the repository and ping [@aviks](https://github.com/aviks) or [@simonbyrne](https://github.com/simonbyrne).

If you have any comments or suggestions for the website, please open an issue [here](https://github.com/JuliaBerry/juliaberry.github.io/issues).
