# Exploration of historical data from sweetpotato

#### This repository host:   
* scripts in the code folder. 
* Notebooks (jupyter Notebooks) to develop and report on the analysis.   
* Containers to reproduce environments across machines using [Docker](https://docs.docker.com/)  
* Environment files to reproduce environments across machines using [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/)  

#### To start:
Populate the data folder

*In a CBSU machine*  

*In your laptop*  


##### Repository contents:
    |-- .gitignore
    |-- LICENSE.md
    |-- README.md
    |-- code/
        |--.gitignore
        |--README.md
        |-- my_script.py 
    |-- data/
        |--.gitignore
        |--README.md
    |-- docker/
        |--.gitignore
        |--README.md
        |--Dockerfile
        |--environment.yml
        |--run_docker.sh
    |-- notebooks
        |--.gitignore
        |--exploratory/
           |--README.md
           |--.gitignore
        |--reports/
           |--README.md
           |--.gitignore

#### To use Docker for the jupyter notebooks:
*In a CBSU machine*  
1. First you need a reservation in a cbsuxxx machine  
2. Login and navigate to workdir with `cd /workdir` and make a folder with the netid `mkdir mynetid`  
3. Navigate to the folder `cd mynetid` and clone the repository `git clone`  
4. Navigate to the docker folder in the repository and build the image  
`docker1 build -t labdocker /workdir/mynetid/myrepo/docker`  
5. To check on the functionality start the container and turn on the jupyter lab server  
`docker1 run -it --rm -p 8888:8888 biohpc_mynetid/labdocker jupyter lab --no-browser --ip=0.0.0.0 --allow-root --NotebookApp.token='local_dev'`  
6. Navigate to your browser `http://cbsuxxx.biohpc.cornell.edu:8888/` and use the token `local_dev` to use the server  
7. Turn the container off.  
8. To actually run the container, use the script run_docker.sh  

CBSU machines doesn't use docker, but an alias docker1

*In your laptop*  
Go and install [Docker](https://docs.docker.com/):  
For Mac: https://docs.docker.com/docker-for-mac/  
For Windows: https://docs.docker.com/docker-for-windows/  
For Linux: https://docs.docker.com/engine/installation/  

1. Create a `.env_dev` file with development environment variables  
  We want to keep passwords secret, so this file won't be in the repository and the .gitignore has been instructed to ignore it
```
# random seed for reproducible models
random_seed=42

#database password
db_password=1234
```
2. Run `docker-compose build --no-cache`. This will build the development image with all the packages I defined installed within it.
3. Run `docker-compose up` and navigate to your browser to find jupyter server running on `http://localhost:8888`
4. Access it by entering in the token `local_dev`.
5. Once you are done, remember to shutdown jupyter server and docker   
  Go to the terminal and Press Ctrl+C   
  `docker-compose down`
6. More instructions coming ...  

#### To use conda:

*In a CBSU machine*  

1. Instructions coming ...

*In your laptop*

1. Go and install [conda](https://docs.docker.com/)  
2. More instructions coming ...

####  Who do I talk to?
* Katherine Mejia-Guerra (mm2842@cornell.edu)  