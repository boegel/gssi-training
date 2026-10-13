# European Environment for Scientific Software Installations (EESSI)

This exercise aims to give you hands-on experience with the European Environment of Scientific 
Software Installations (EESSI). EESSI can be used as a central software stack on HPC but also
as a software stack on your laptop or in the cloud. The exercises indicated with **recomended**
should approximately take 30 minutes to complete. For people interested in other scenarios they
can follow the links to other trainings and the EESSI documentation.

relevant links:
- [EESSI documentation](https://www.eessi.io/docs/)
- [EESSI demos](https://github.com/EESSI/eessi-demo)

## Using EESSI
### EESSI available (recommended exercise)
In the following excercise we will show how to check whether EESSI is available on the system.
And how to start using it.
```
# Check if EESSI is available
ls /cvmfs/software.eessi.io
```
This will return the following on all systems at VSC sites.
```
README.eessi  host_injections  init  versions
```
If EESSI is on the system you can initialize the EESSI environment.
```
source /cvmfs/software.eessi.io/versions/2025.06/init/lmod/bash
```

If you are on another system and you get the following return. EESSI is not available and
you should follow the instructions (here)[# EESSI not available].
```
ls: /cvmfs/software.eessi.io: No such file or directory
```

### EESSI not available
If EESSI is not available on the system you want to use it on their are a number of options.
If you have root permissions on the system you can do a native installation of
[cvmfs](https://cvmfs.docs.cern.ch/mkdocs/). Which is the delivery machanism for software in
EESSI. If you do not have root permissions you can also use cvmfsexec or containers.

Check out the EESSI documentation for the different instructions on making EESSI available:
- [Containers](https://www.eessi.io/docs/getting_access/eessi_container/)
- [Native (requires root)](https://www.eessi.io/docs/getting_access/native_installation/)
- [cernvmexec](https://www.eessi.io/docs/training-events/2025/tutorial-best-practices-cvmfs-hpc/access/alternatives/#cvmfsexec)

## Excercise
### Software already available in EESSI (recommended exercise)
EESSI already has a wide range of software available over its 3 supported versions 
(2023.06, 2025.06 and 2026.06). You can look at the EESSI 
[software overview page](https://www.eessi.io/docs/available_software/) to see if 
the software and specific version you require is already available. You can also use the
`module` command once EESSI is inatialized.

To get access to different EESSI versions you can run:
```
module purge
module load EESSI/2023.06
```

EESSI provides a number of demo's for software that is already available in the stack. Feel free
to run any of the scripts in the [demo repository](https://github.com/EESSI/eessi-demo). Below
we will go through the steps of running the tblite example.

```
git clone https://github.com/EESSI/eessi-demo.git
module purge
module load EESSI/2025.06
cd eessi-demo
cd tblite
./run.sh
   --------------------------------------------------------------
   Cycle       total energy       energy error     density error 
   --------------------------------------------------------------
       1    -31.30086746450     -3.1478794E+01     3.3527172E-01
   ...
      18   -31.716155889120     -1.8267450E-09     1.5041592E-05
   --------------------------------------------------------------
   Total:                        0.074 sec
   -31.71658891203904

```

### Building on top of EESSI
If the software you require is not yet in EESSI you can relly on the already existing software
stack and build on top of it with EasyBuild, Python venv, spack, ... 
For instructions:
- [EESSI-extend (building ontop with EasyBuild)](https://www.eessi.io/docs/available_software/detail/EESSI-extend/)
- [Python venv](https://vscentrum.github.io/gssi-training/exercises/python/)
- [with spack](https://www.eessi.io/docs/blog/2026/01/09/Spack-on-top-of-EESSI-PoC/)

### Contributing to EESSI
If you want your software to be available on wide range of systems and it is not yet in EESSI.
You can contribute it yourself, see 
[Overview of adding software to EESSI](https://www.eessi.io/docs/adding_software/overview/#overview-of-adding-software-to-eessi).
