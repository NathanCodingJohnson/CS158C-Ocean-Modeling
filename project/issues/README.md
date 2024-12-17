issue 1
## Issue Summary
incorrect number of processors indicated in SIZE.h as compared to processors requested in slurm file
## MITgcm message
the difference of processors was indicated by the slurm out file showing STOP ABNORMAL END as well as the STDERR.000X files saying that that the processors were not equal to nPx x nPy despite my SIZE.h having nPx = 4 and nPy = 2
## Issue Remedy
I fixed this issue by updating my build directory as this turned out to be the root of the error. By recompiling with the update SIZE.h file, the build files were correct and it fixed the error.


build issue


## Issue Summary
Despite getting a (FC_CHECK 5/5), when running make depend in the build directory, I am getting the following warnings:
![unnamed](https://github.com/user-attachments/assets/abd7c7b7-030b-4e56-ba35-2351b37a9016)
If I then try to run make, I end up with a bunch of errors regarding being unable to find various mpi files and the mitgcmuv executable is not created.
![unnamed](https://github.com/user-attachments/assets/f78411a9-980a-4f7a-b0c3-9a3eb0aad73c)
