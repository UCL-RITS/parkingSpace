### Setup the Env to run pyEGA tool from RDS nodes (ALTERNATIVE METHOD)

Provided you are minimally experienced with python and the Linux CLI, you can try to install the tool by using the following alternative method, if the EASY method guide did not succeed, or if you are experiencing troubles with running **conda** and the pyEGA tool on our custom Systems installation.


The following instructions can be run only when anaconda/miniconda setup has been successfully performed and the environment is functional for the user.

Please get in touch if you experience any trouble running the commands in the following guide.

##### Environment Initialization :  

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

##### Instructions :

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
### Login with custom credentials to EGA/EBI remote servers

In order to be able to download data-sets you should register on EGA website and upon registration receive your **User Access Credentials** that will be needed by the tool to access the remote servers on your behalf, and allow you to download the needed data-sets.

Credentials can be passed to the pyEGA client tool in 2 ways :  

1. **interactive**, via the command line ( ! ADVISED METHOD ! )

  `pyega3 <command1> <argument1>`

  just run the tool as above and at prompt input in 2 steps username and the password.


2. using a `.json` **configuration file** with the credentials stored in it ( ! LESS SECURE METHOD ! )  

- clone the default config-file into your protected home folder and modify it with your text editor of choice to include only your own EGA credentials:  

  `cp ega-download-client/pyega/config/default_credential_file.json /home/my_username/pyEGA3-Creds.json`

- when running commands, point the tool to use your current credential file with the `-cf` flag  

    `pyega3 -cf /home/my_username/pyEGA3-Creds.json <command1> <argument1>`




**IMPORTANT :**  

If you are working in a shared environment or project folder, please consider that **we strongly recommend our users to use method 1. above** , and  advise against the use of method 2. for reasons related to data privacy and security.

If you choose to use method 2 for any reason, please make sure that you store your credentials in a `.json` file that resides in **your own (private) home folder** and **NOT in a group-shared/accessible folder**, such as normally is the case for projects folders, for instance.  



---

###### examples:

- test that your own credential-file is working and check what data-sets you have access to :

  `pyega3 -cf /home/my_username/CredentialsFile.json datasets`



For more information and instructions, please see Refs below, "video tutorial" at video paragraphs :
- Defining your credentials file ( at [0:41"] of the recording )  

- Interactive login ( at [8':27"] of the recording )


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

###### Video Tutorial  
[https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=be79bb93-1737-4f95-b80f-ab4300aa6f5a](https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=be79bb93-1737-4f95-b80f-ab4300aa6f5a)
