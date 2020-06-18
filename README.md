# Great Lakes Cheat Sheet

cmd|description
---|---
`my_accounts`|show accounts
`module load python3.7-anaconda`|load a module
`module list`|list all loaded modules
`pip install --user "torch==1.4"`|install package into user directory
`history`|list of past commands
`sbatch myExJob.sh`|submit Slurm job
`srun --pty --account=cscar --partition=gpu --gres=gpu:1 --nodes=1 --ntasks-per-node=1 --mem-per-cpu=7g /bin/bash`|submit interactive Slurm job for gpu
`scancel <jobid>`|delete job (interactive too)
`squeue -u caoa`|show job queue
`sstat <jobid>`|job status info
`scp localfile caoa@greatlakes-xfer.arc-ts.umich.edu:~/remotefile`|copy file from local to great lakes
`scp -r localdir caoa@greatlakes-xfer.arc-ts.umich.edu:~/remotedir`|copy directory from local to great lakes
`scp -r caoa@greatlakes-xfer.arc-ts.umich.edu:~/remotedir localdir`|copy directory from great lakes to local

[Great Lakes User Guide by Arc-TS](https://arc-ts.umich.edu/greatlakes/user-guide/)

[Great Lakes Cheat Sheet by Arc-TS](
https://arc-ts.umich.edu/wp-content/uploads/sites/4/2019/11/Great-Lakes-Cheat-Sheet-11-19.pdf)


# rclone Cheat Sheet

Great Lakes
```
module load rclone
rclone config
```
Cavium  
`/sw/dsi/aarch64/centos7/bin/rclone config`

Here is an example config setting for accessing AWS S3 bucket. IAM user READ-ONLY role has been defined.

field|value
:---:|:---:
name|S3bucket
type|s3
provider|AWS
env_auth|false
access_key_id|<access_key>
secret_access_key|<secret_access_key>
region|<region>
acl|private
endpoint|<endpoint if exists else "">
  
Everything else is default setting.

cmd|description
---|---
`rclone lsd S3bucket:`|list buckets in account
`rclone ls S3bucket:s3select-example`|list files in bucket
`rclone copy S3bucket:s3select-example/summary.txt ~ --dry-run`|dry run of copying file from AWS to local
`rclone copy S3bucket:s3select-example/summary.txt ~`|copy file from AWS to local


