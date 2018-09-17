### Running python script:
Ref: https://www.hpc.mcgill.ca/downloads/user_meetings/McGillHPC-UsersMeeting-PythonPackages-20171214.pdf
1. To get all latest version of python, etc: `[cq_server]> source /software/soft.computecanada.ca.sh`
2. `[cq_server]> module avail`
3. `[cq_server]> module add python/3.6.3`
4. `[cq_server]> module load python/3.6.3`
5. To create a virtualenv for python:
	1. `[cq_server]> virtualenv env`
	2. `[cq_server]> source env/bin/activate`
	3. `(env)_[cq_server]> pip install numpy`
	4. `(env)_[cq_server]> deactivate (to exit virtualenv)`

Example job script:

```
#!/bin/bash
#PBS -l walltime=00:08:00 ## The max amount of time needed to execute the file
echo 'Hello, world!'
source /software/soft.computecanada.ca.sh
module load python/3.6.3
echo $PATH
echo $(which python)
source ~/test_folder/env/bin/activate
cd ~/test_folder/test_repo
python test_file.py
sleep 30
```
