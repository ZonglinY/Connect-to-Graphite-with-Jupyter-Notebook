# Use-Jupyter-Notebook-on-Graphite

## Overview


Instructions for setting up Jupyter Notebook on Graphite.

## Steps

Pre-step: 

install Anaconda and set up your environment ``<env_name>``


Step 1:  On graphite:     

    
    source activate <env_name>
    
Step 2: On graphite,	   
   
    which python
    
Step 3,

   Get print: 	``/home/<your_netid>/.conda/envs/<env_name>/bin/python``, 
   
   We will use the file path for bin in next step: ``/home/<your_netid>/.conda/envs/<env_name>/bin/``
    
Step 4: On graphite,
    
    export PATH=/home/<your_netid>/.conda/envs/<env_name>/bin/:$PATH
    
Step 5: On local machine,
    

    ssh <your_netid>@graphite-login.coecis.cornell.edu -L 127.0.0.1:1234:NODE_NAME:8888 
   (For Claire's student, an example here for ``NODE_NAME`` is nikola-compute05)

    ssh your_netid@graphite-login.coecis.cornell.edu -L 127.0.0.1:1234:NODE_NAME:8888 
   (For Prof. Cardie's student, an example here for NODE_NAME is nikola-compute05)
   
   (If 8888 is used, change it with any number between 8000 and 10000, but note that you should also change the port number in step 7 with the number you use in this step)


Step 6: On grahite,
   
    srun -p interactive --pty --nodelist=NODE_NAME /bin/bash

Step 7: On grahite,     
   
    XDG_RUNTIME_DIR=/tmp/<your_netid> jupyter-notebook --ip=0.0.0.0 --port=8888
    
Step 8:

   On local browser, ``http://127.0.0.1:1234/?token=LONG_ALPHANUMERIC_STRING_FROM_JUPYTER-NOTEBOOK_OUTPUT``

## Acknowledgment

These were adapted from official suggestions by Cornell IT (https://it.coecis.cornell.edu/researchit/graphitegpu/).
