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


new run error

## Issue Summary
Upon sbatch cs185c00.slm, I am no longer getting the same errors complaining about number of processors not being correct, but I am now getting a series of Fortran runtime errors: Repeat count too large for namelist object delx At line 4332 of file ini_parms.f (unit = 11, file = 'scratch1.00000000x') with x ranging from 0 to 7


unlike previous errors, 8 full STDERR files and 8 STDOUT files are created along with 8 scratch1.00000000x files

the STDERR files all are empty so they provide no helpful information

The STDOUT files shows the execution of SIZE.h that includes the proper sizing and processors being used but then stopps in the middle of the data file once INI_PARAMS starts to read PARM04. It should also be noted that when ran in the run-tsunami folder, the STDOUT file does not show the change to the data file that specifies the pSurfaceInitFile to be ETAN_with_tsunami_IC.bin and just shows the ETAN_IC.bin that is used in the pain run folder

the scratch.00000000x files just show the data file, also with the incorrect ETAN file in the run-tsunami folder
