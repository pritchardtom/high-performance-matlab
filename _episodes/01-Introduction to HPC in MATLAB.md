---
title: "Introduction to HPC in MATLAB"
teaching: 30
exercises: 0
questions:
- "What is high-performance computing (HPC)?"
- "What are the different options for HPC in MATLAB?"
objectives:
- "Understand what high-performance computing is."
- "A brief overview different types of HPC techniques
   available to MATLAB users."
keypoints:
- "High-performance computing is all about expediting the computations."
- "MATLAB offers several in-built functions to exploit the various 
-  HPC architectures, for example, multi-threads, 
   multi-cores and GPUs, available today."
- "MATLAB Parallel Computing Toolbox requires significantly less effort
   when compared with parallelisation in C, C++ and Fortran. But it comes
   at the cost of lower computing speeds."
---

# MATLAB
MATLAB is a multi-paradigm numerical computing platform for 
scientific computing, and is also a high-level programming language.

MATLAB offers support for linear algebra (Matrices and Vectors), 
function evaluations, plotting and visualisation, and symbolic 
computations for mathematical expressions.

Unlike C, C++ and Fortran, MATLAB is an interpreted language similar 
to Python. This means that programs written in MATLAB can be executed 
directly without the need for compiling them. Therefore, MATLAB is 
relatively easy to learn and use compared to compiled languages 
C, C++ and Fortran. However, the price one has to pay for this 
functionality is the slowness of computations. MATLAB is atleast 
an order of magnitude is slower than the programs written in C, 
C++ and Fortran. Nevertheless, MATLAB supports linking of C/C++ 
and Fortran codes with MATLAB code, if one is interested in replacing 
computing-intensive routines with C++ or Fortran programs.

# Scope of this lesson
The main objective of this lession is to learn how we can harness 
the computing power in high-performance computers using MATLAB.
In this workshop we will focuss on the techniques that help run MATLAB 
programs efficiently and effectively using commandline interface and 
high-performance computing (HPC) resources. This material is aimed at 
problems that are computationally so demanding that each simulation 
runs for days on personal computers.

* While high-performance computing is considerably more involved in 
  languages such as C, C++, Fortran and Python, it is 
  relatively easier in MATLAB.
* MATLAB offers in-built support for high-performance computing 
  in the form of parallelised loops, parallelised functions and
  **spmd** construct within the MATLAB Parallel Computing Toolbox (PCT).
* In this course, we will focus on
    * Vectorization
    * Profiling
    * Parallel Computing Toolbox
      * parfor
      * spmd
      * mpiprofile
    * Running MATLAB from commandline
    * Running MATLAB on Sunbird


# What is High-Performance Computing (HPC)?
In layman words, High-Performance Computing can be described as 
the process of perfoming more calculations in a given amount of 
time by utilising more computer hardware.

According [InsideHPC](https://insidehpc.com/hpc-basic-training/what-is-hpc/),

"High Performance Computing most generally refers to 
the practice of aggregating computing power in a way 
that delivers much higher performance than one could get
out of a typical desktop computer or workstation in order to
solve large problems in science, engineering, or business.”

High Performance Computing is carried out on a supercomputer,
also called as a cluster. A cluster is simply a group of computers 
with the same components 
(RAM, disk, processors/cores, and networking cards) as those in 
your desktop or laptop, but more poweful, and are networked 
with high-speed interconnect that can be accessed (indirectly) 
through software, the scheduler, that manages simultaneous 
execution of jobs by single or multiple users.

The following figure depicts a typical supercomputing cluster 
along with some of its important componnets. The user accesses 
the supercomputer by logging into the ***login node*** and by 
submitting jobs (or tasks) using ***jobscripts*** which will be managed 
by job schedulers such as [Slurm Workload Manager](https://slurm.schedmd.com/documentation.html),
[PBS](https://www.pbspro.org/). The jobs are executed on the 
***compute nodes***. On Sunbird, we use Slurm workload manager.
![Parallel pool status indicator](../fig/cluster-generic.png)


## Nodes and Cores
Each individual computer in a cluster is commonly referred to
as a “node”. Inside each node will be several processor chips 
that do the actual computation. A typical node in a cluster 
will have anything from 8 to 40 cores in total often across 
several physical processor chips.

## Reasons for using high-performance computing
* Your code takes a lot of time, for example, a couple of days, 
  to run on your personal laptop or the desktop PC in your lab.
* Even though your code is fast enough you don't have enough memory on
  your local machine to fit all of your data.
* Your code runs fast enough but you want to run 100s or
  1000s of small jobs by varying some input parameters.
* You want to use a software library or a propriatory software that you
  cannot install on your local machine for some reason.


> ## MATLAB job scheduler
> MATLAB has its own job scheduler. However, we do not recommend it 
> on Supercomputing Wales clusters. We use SLURM.
{: .callout}

> ## MATLAB Computing speed
> It is important to keep in mind the slowness of MATLAB codes.
  MATLAB codes are 10-100 times slower than the optimized C, C++ and 
  Fortran codes. Since MATLAB is significantly slower than the code written 
  in C, C++ and Fortran, parallelisation in MATLAB will also be 
  considerably slower than what we can achieve in C, C++ and Fortran.
{: .callout}


{% include links.md %}

