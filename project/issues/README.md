issue 1
## Issue Summary
incorrect number of processors indicated in SIZE.h as compared to processors requested in slurm file
## MITgcm message
the difference of processors was indicated by the slurm out file showing STOP ABNORMAL END as well as the STDERR.000X files saying that that the processors were not equal to nPx x nPy despite my SIZE.h having nPx = 4 and nPy = 2
## Issue Remedy
I fixed this issue by updating my build directory as this turned out to be the root of the error. By recompiling with the update SIZE.h file, the build files were correct and it fixed the error.
