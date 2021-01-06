# PyEGA tool setup on RDS systems

## Prerequisites

- Guide 00 - miniconda installation  
- unsuccessfull run of Guide 01
- basic experience with Python and Linux CLI

## Environment Setup to run pyEGA tool on RDS systems (ALTERNATIVE METHOD)

If the procedure highlighted in the EASY method guide was NOT successful, or the User is experiencing troubles with running **conda** and the `pyEGA_client` tool itself on RDS custom Systems, the User can try to perform an installation of the tool by using this alternative method.


### Environment Initialization :  

- initialize the conda environment

  `conda init bash`

  **NOTE 1 :**  
  if the users are attempting to follow this guide in the same shell session, straight after installing anaconda/miniconda (as per the previous guide), they may experience the following error:

  ```
  conda activate <VirtualEnv-NAME>

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

  in this case, please **close your shell session and start a new one** (the environment should be reset and setup correctly the second time you log back in)

  **NOTE 2 :**  
  ( to run apps with the System's interpreter **python 3.6** **may be necessary** to set the environmental variable `PYTHONPATH` as follows : )

  `PYTHONPATH=/usr/lib/python3.6/site-packages/`

### Instructions :

- pick a name for your virtualEnv and set it with this variable  

  `testVENV="chosen-name"`  

- create a basic virtualEnv with the 2 minimum requirement packages (**pip, psutil** ) for this tool to run :  

  `conda create --name $testVENV pip psutil`  

- activate the newly created virtualEnv  

  `conda activate testVENV`  

- clone the pyEGA_client github repo

  `git clone https://github.com/EGA-archive/ega-download-client.git`

- browse into the repo (sub)folders to find the **requirements.txt** file  


**------------------------------------------------------------------ ! IMPORTANT ! ---------------------------------------------------------------------------**  
please do NOT run the **bash scripts** from the original Repo guide, as the basic custom environment is already setup here, and any further needed tweak is highlighted below.   
**-----------------------------------------------------------------------------------------------------------------------------------------------------------------**  

- install the tools dependencies (requested packages) :

  `conda install --yes --file requirements.txt`  

  **NOTE :**  
  in case of conda installation failures or if a manual installation of a specific package/version is needed, please install them like this:   

  ```
  conda install -c bioconda python-htsget
  conda install -c conda-forge psutil
  conda install -c conda-forge tqdm
  ```

- list and inspect the properties of your base and newly created virtualEnvs :  

  `conda info --envs`  
  `conda list`  

- test that the downloaded tool is working once all dependencies have been installed and conflicts resolved, by navigating to its folder and running the main program command like this :

  `./pyega3.py -d -t datasets`

  you should see the expected output

---


Use the tool's help for more info  

`pyega3 --help`

and Refer to the original tool's online documentation. (see Refs below)

If further guidance is needed, please make sure to check the original github Repo documentation;  
specifically the main **README.md** file for more info and help on the following topics :

- access EGA datasets with a credential file or via interactive CLI session
- retrieve datasets with the tool and save them in a specific path, by pointing the destination path to somewhere else (if needed).

---

### Refs

###### pyEGA3 - EGA python client version 3.4.0
[https://github.com/EGA-archive/ega-download-client](https://github.com/EGA-archive/ega-download-client)  
###### pyEGA   
[https://github.com/blachlylab/pyega](https://github.com/blachlylab/pyega) by James Blachly
