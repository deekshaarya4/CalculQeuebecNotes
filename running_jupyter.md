### Running jupyter:

(After python install from running_python_scripts.md)
Ref: https://docs.computecanada.ca/wiki/Jupyter
1. `[cq_server]> module load python/3.6.3`
2. `[cq_server]> source env/bin/activate`
3. `[cq_server]> source env/bin/activate`
4. `(env)_[cq_server]> pip install jupyterlab`
5. `(env)_[cq_server]> echo -e '#!/bin/bash\nunset XDG_RUNTIME_DIR\njupyter lab --ip $(hostname -f) --no-browser' > $VIRTUAL_ENV/bin/jlab.sh`
6. `(env)_[cq_server]> chmod u+x $VIRTUAL_ENV/bin/jlab.sh`
To run on worker jobs:
7. `(env)_[cq_server]> salloc --time=1:0:0 --ntasks=1 --cpus-per-task=2 --mem-per-cpu=1024M --account=def-yourpi srun $VIRTUAL_ENV/bin/notebook.sh`
Then copy paste the URL provided by 7 in local machine browser to access jupyter lab.
