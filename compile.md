---
layout: default
title:  JuliaBerry&#58; Compiling Julia
---

Compiling Julia on the Raspberry Pi is quite the journey.

# Prerequisites
### Packages
There a few packages that you must install prior to starting the compile.

```
sudo apt-get -y update 
sudo apt-get install build-essential libatomic1 python gfortran perl wget m4 cmake pkg-config libopenblas-dev git ccache
```

### Swap File
The standard, out of the box swap file configuration is not sufficient.  The swap file is configured for only 100MB, which
the compiler will go through very fast.

You can increase the size of the swap file by editing */etc/dphys-swapfile* as sudo/root.  Below are the recommended values:

```
CONF_SWAPSIZE=8192
CONF_MAXSWAP=8192
```

After editing the */etc/dphys-swapfile*, you can either reboot or execute the following:

```
sudo /etc/init.d/dphys-swapfile stop && sudo /etc/init.d/dphys-swapfile start
```

### Use the Source!

Change into the directory that you would like to keep your projects.  Execute:

```
git clone https://github.com/JuliaLang/julia.git
```

You can change into the *julia* directory and either work from master or checkout one of the existing releases/tags ( i.e. _v1.0.2_).

If you are going to keep up to date with master, or compile on a more frequest basis, then creating a *Make.user* file will save you some pain
with the extended compile times that Julia will have on the Raspberry Pi.

```
echo "USECCACHE=1" > Make.user
```

# Compiling
## Executing Make

This is perhaps the easiest step.  You will just need to execute *make* from the directory you checked out your code as follows:

```
make
```

Due to the memory limits, running multiple jobs (i.e. `make -j...`) is not recommended.

## The hard part
The hardest part is waiting.  The initial compile will take 12+ hours to compile.  Subsequent compiles after creating the _Make.user_ file as described above should only take around two hours.

# Distributing
### Binary Distributions
Additional details can be found [here](https://github.com/JuliaLang/julia/blob/master/DISTRIBUTING.md).

```
make binary-dist
```
