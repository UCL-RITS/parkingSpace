
### MINICONDA MANUAL INSTALLATION PROCEDURE :  

1. navigate to your RDS project folder  

  (example):  
  `/mountPoint/projectName`  

2. download the official  

  **miniconda** _DataScience selfcontained Python Development environment_  

  from :  https://docs.conda.io/en/latest/miniconda.html#linux-installers

  `curl -LOks https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`

3. verify the installer file's checksum integrity of the downloaded file :  

  `shasum -a 256 Miniconda3-latest-Linux-x86_64.sh`  

  This will make sure that the downloaded file is not corrupted and that its signature matches the one from the website.  
  (**HINT :** just compare the first and last 3/4 digits of the signatures; if they do NOT match this means that the file downloaded has been CORRUPTED and it must be re-downloaded and re-checked).

  example with the value from the website for that package - long string is the checksum -:
```
Python 3.8 	Miniconda3 Linux 64-bit 	89.9 MiB 	1314b90489f154602fd794accfc90446111514a5a72fe1f71ab83e07de9504a7
```

4. clear the `PYTHONPATH` environment variable in the shell;  
 this variable is NOT needed at present and almost certainly it will cause installation issues at this time and on this particular configuration and setup.

 (example: clear it by setting it to an empty value, as below, and press ENTER)

 `PYTHONPATH=`

- **in your own project folder** set the installer file executable for yourself  :

  `chmod u+x Miniconda3-latest-Linux-x86_64.sh`

- run the following command to copy the current working directory path:

  `pwd`

  and select + copy the output of the command;

  (example of output :  
  `/mountPoint/projectName`  
  this text must be copied and it will be pasted later on, during miniconda installation process; - see the following instructions ).

5. execute the program and begin the local installation of miniconda:

  `./Miniconda3-latest-Linux-x86_64.sh`


  - after the interactive tool has started, press in sequence to continue the process:

  `ENTER`  (to effectively start the installation)  
  `space`  (to scroll down the T&C pages)  
  `space`  (to scroll down the T&C pages once more)  
  `yes`    (to confirm T&C/licence acknowledgment)  


- paste now here the value from the path copied at the step above and make a new folder afterwards:

  (example:  
    if you copied `/mountPoint/projectName`  from the previous steps, paste this value here as shown below and please **NOTE** the following:  
  the last sub-folder in the pasted path (in this case "/miniconda3"), has been manually added to make a new local sub-folder, that will contain this installation:

  `/mountPoint/projectName/miniconda3`  

  type then

  `yes`    (to confirm initialization of miniconda3 installation)


6. From your project folder, navigate to miniconda3 parent folder (example  `/mountPoint/projectName/software`)

  run the following 1-liner command :

  `OUTFILENAME=fixPythonPath ; PATH=$PWD/miniconda3/bin:${PATH} ; echo -e "\nPATH=$PATH \n" >> ./$OUTFILENAME ; echo -e "\nPYTHONPATH=/usr/lib/python3.6/site-packages/ \n" >> ./$OUTFILENAME ; source $OUTFILENAME`

  this will create a file called `fixPythonPath` in your current directory, allowing your terminal shell to reference - **ONLY for the current session** - the local `minicondaX` installation of the Python interpreter and not the system global one(s).

  **IMPORTANT:**  
  - every time you LOG OUT, your defaults will be restored;  

  - every time you LOG IN, you will need to run from the folder where the `fixPythonPath` file is located :

  `source ./fixPythonPath`

  To test your setup is good, run from CLI :

  `which conda`  
  `which python`  
  `which pip`  

  and check that the commands' output returns the binaries from your local installation path, and not the global system installation ones :

  `/mountPoint/projectName/miniconda3/bin/conda`  
  `/mountPoint/projectName/miniconda3/bin/python`  
  `/mountPoint/projectName/miniconda3/bin/pip`  






---
##### REFS:

##### miniconda:

https://docs.anaconda.com/anaconda/install/linux/

installation  
https://conda.io/projects/conda/en/latest/user-guide/install/linux.html#install-linux-silent

linux installers and checksums  
https://docs.conda.io/en/latest/miniconda.html#linux-installers


Repos:  
https://github.com/EGA-archive  
https://github.com/EGA-archive/ega-download-client
