# dockerR_template

#### This repository host a template to launch a workstation with RStudio server:   
* Folder for notebooks (R Notebooks) to report/develop analysis.   
* Folder for data to host data, files in this folder are not sync to the git repository.  
* Folder for code to host scripts to populate data folder.  
* Container to reproduce workstation environment using [docker.](https://docs.docker.com/)  

#### To start
Clone the repository `git clone`, and populate the data folder

##### General view of the repository:
    |-- .gitignore
    |-- LICENSE.md
    |-- README.md
    |-- docker-compose.yml
    |-- code
        |-- script-to-populate-data_dir.sh 
    |-- data
        |--.gitignore
    |-- docker/
        |--Dockerfile
    |-- notebooks
    
    
##### Launch Docker

1. To use the docker images you first need to install Docker:  

* For Mac: https://docs.docker.com/docker-for-mac/  
* For Windows: https://docs.docker.com/docker-for-windows/  
* For Linux: https://docs.docker.com/engine/installation/  

2. Create a `.env_dev` file with development environment variables  
  We want to keep passwords secret, so this file won't be in the repository and the .gitignore has been instructed to ignore it
```
# random seed for reproducible models
random_seed=42

#database password
db_password=1234
```
3. Run `docker-compose build --no-cache`. This will build the development image with all the packages I defined installed within it.
4. Run `docker-compose up` and navigate to your browser to find Rstudio running on [http://localhost:8787](http://localhost:8787). 
5. Access it by entering user `rstudio` and the password `local_dev`.
6. Once you are done, remember to shutdown the server and docker   
  Go to the terminal and Press Ctrl+C   
  `docker-compose down`