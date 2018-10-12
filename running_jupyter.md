### Running jupyter:

Use only on Cedar, Graham or mp2 where SLURM is configured (so `salloc` is available)

(After python install from running_python_scripts.md)
Ref: https://docs.computecanada.ca/wiki/Jupyter
1. `[cq_server]> module load python/3.6.3`
2. `[cq_server]> source env/bin/activate`
3. `[cq_server]> source env/bin/activate`
4. `(env)_[cq_server]> pip install jupyterlab`
5. `(env)_[cq_server]> echo -e '#!/bin/bash\nunset XDG_RUNTIME_DIR\njupyter lab --ip $(hostname -f) --no-browser' > $VIRTUAL_ENV/bin/jlab.sh`
6. `(env)_[cq_server]> chmod u+x $VIRTUAL_ENV/bin/jlab.sh`
7. On your local box, in a new terminal tab/window, set up the ssh tunnel, first install sshuttle, then:
  
  `[local]> sshuttle --dns -Nr <username>@<cq_server>`
  
8. To run jupyter on worker jobs:
  
  `(env)_[cq_server]> salloc --time=1:0:0 --ntasks=1 --cpus-per-task=2 --mem-per-cpu=1024M --account=def-yourpi srun $VIRTUAL_ENV/bin/notebook.sh`

Then copy paste the URL provided in 8 in your local machine browser to access jupyter lab.
