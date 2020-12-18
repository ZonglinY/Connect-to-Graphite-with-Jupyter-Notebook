# Connect-to-Graphite-with-Jupyter-Notebook

This tips follows official suggestions by IT department (https://it.coecis.cornell.edu/researchit/graphitegpu/)

Pre-step: install Anaconda and set environment (my environment name is 'pt', you should substitute 'pt' with your own environment name in following steps)

Step 1： 

    On graphite: 	source activate pt
    
Step 2:

    On graphite:	which python
    
Step 3:

    Get print: 	/home/zy223/.conda/envs/pt/bin/python; We will use the file path for bin: /home/zy223/.conda/envs/pt/bin/
    
Step 4:

    On graphite:	export PATH=/home/zy223/.conda/envs/pt/bin/:$PATH
    
Step 5:

    On local machine:   ssh your_netid@graphite-login.coecis.cornell.edu -L 127.0.0.1:1234:NODE_NAME:8888 
    (For Prof. Cardie's student, an example here for NODE_NAME is nikola-compute05)

Step 6:

    On grahite:     srun -p interactive --pty --nodelist=NODE_NAME /bin/bash

Step 7:

    On grahite:     XDG_RUNTIME_DIR=/tmp/zy223 jupyter-notebook --ip=0.0.0.0 --port=8888
    
Step 8:

    On local browser:    http://127.0.0.1:1234/?token=LONG_ALPHANUMERIC_STRING_FROM_JUPYTER-NOTEBOOK_OUTPUT
