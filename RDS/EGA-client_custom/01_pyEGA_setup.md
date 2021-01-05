### Setup the Env to run pyEGA tool from RDS nodes  


`conda init bash`

may get error:
```
 conda activate testVENV

CommandNotFoundError: Your shell has not been properly configured to use 'conda activate'.
To initialize your shell, run

    $ conda init <SHELL_NAME>

Currently supported shells are:
  - bash
  - fish
  - tcsh
  - xonsh
  - zsh
  - powershell

See 'conda init --help' for more information and options.

IMPORTANT: You may need to close and restart your shell after running 'conda init'.
```


( to run apps with python 3.6 from System may need to set `PYTHONPATH=/usr/lib/python3.6/site-packages/` )

- pick a name for your virtualEnv and set it with this variable  
  `testVENV="chosen-name"`  

- create the virtualEnv with basic packages for this tool to run  
  `conda create --name $testVENV pip psutil`  

- activate the virtualEnv  
  `conda activate testVENV`  

- clone the pyEGA_client github repo and browse into its (sub)folders to find the **requirements.txt** file  ( in this case it was in the **ega-download-client-master** folder )

**----------------------------------------------------------------------------- ! IMPORTANT ! ------------------------------------------------------------------------------------------**  
please do not run the bash scripts from this Repo as the basic custom environment is already setup and further tweaks highlighted below.   
**---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------**  

- install the tools dependencies (requested packages) :

  `conda install --yes --file requirements.txt`  

- if a manual installation is needed for the packages, install them like this:   
```
conda install -c bioconda python-htsget
conda install -c conda-forge psutil
conda install -c conda-forge tqdm
```

- check and list your base and created virtualEnvs :  
`conda info --envs`  
`conda list`  

- test that the downloaded tool is working once dependencies have been installed, by navigating to its folder and runnning the main program command like this :

  `./pyega3.py -d -t datasets`





**HINT :** Please check the original Repo documentation and **README.md** file for more help and instructions.

See the original documentation



---

#### 2DOs

- instructions for the user on how to create in their own home folder their credential file to use to access EGA datasets, with this tool and how to point it to their credential files
