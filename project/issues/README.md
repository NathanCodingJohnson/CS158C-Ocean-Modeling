issue 1
## Issue Summary
incorrect number of processors indicated in SIZE.h_no_mpi as compared to processors requested in slurm file
## MITgcm message
the difference of processors was indicated by the slurm out file showing STOP ABNORMAL END as well as the STDERR.000X files saying that that the processors were not equal to nPx x nPy
## Issue Remedy
I fixed this issue by updating my SIZE.h_no_mpi file to properly match the 8 processors requested
