# Use-Jupyter-Notebook-on-Graphite

This tips follows official suggestions by IT department (https://it.coecis.cornell.edu/researchit/graphitegpu/)

Pre-step: install Anaconda and set up an environment (my environment name is 'pt', you should substitute 'pt' with your own environment name in following steps)

Step 1:  On graphite:     
    
    source activate pt
    
Step 2:  On graphite:	   
   
    which python
    
Step 3:
   Get print: 	/home/zy223/.conda/envs/pt/bin/python; 
   We will use the file path for bin in next step: /home/zy223/.conda/envs/pt/bin/
    
Step 4:  On graphite:	
    
    export PATH=/home/zy223/.conda/envs/pt/bin/:$PATH
    
Step 5:  On local machine: 
    
    ssh your_netid@graphite-login.coecis.cornell.edu -L 127.0.0.1:1234:NODE_NAME:8888 
   (For Prof. Cardie's student, an example here for NODE_NAME is nikola-compute05)
   
   (If 8888 is used, change it with any number between 8000 and 10000, but note that you should also change the port number in step 7 with the number you use in this step)

Step 6:  On grahite:     
   
    srun -p interactive --pty --nodelist=NODE_NAME /bin/bash

Step 7:  On grahite:     
   
    XDG_RUNTIME_DIR=/tmp/your_netid jupyter-notebook --ip=0.0.0.0 --port=8888
    
Step 8:

   On local browser:    http://127.0.0.1:1234/?token=LONG_ALPHANUMERIC_STRING_FROM_JUPYTER-NOTEBOOK_OUTPUT
