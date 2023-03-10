# Spark on ACCRE

This repository provides updated code for spinning up a Spark cluster and running Spark jobs on ACCRE's traditional HPC cluster via SLURM.

## Description

This directory contains an example Spark job launched through SLURM. The job is launched through the SLURM batch script `spark_test.slurm`; this  script allocates resources to set up tasks consisting of 
- a client
- a master 
- an arbitrary number of workers

Due to how SLURM is structured, the allocation of each of these processes must be homogeneous, which is slightly wasteful but easy to understand. Each process is launched via `srun` where the exectuable for each process is specified in the `cluster.conf` file.

## Notes

To access the Spark Web UI:
- After submitting the SLURM job, and it's started...
- Run `grep 'To tunnel to MasterUI and JobUI' *task0.out` in the job's directory
- Run the command in the returned line on your local machine
- Navigate to localhost:8080/ in a browser

## Credits
Adapted from: https://bigdata-vandy.github.io/using-spark-with-gpfs/
