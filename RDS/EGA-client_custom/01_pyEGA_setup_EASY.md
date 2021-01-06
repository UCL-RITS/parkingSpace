# PyEGA tool setup on RDSS

## Prerequisites

- Guide 00 - miniconda installation

## Environment Setup : run pyEGA tool from RDS nodes ( EASY METHOD)

#### Instructions

- add the requested repositories needed by the tool as per its original Repo instructions  

  `conda config --add channels bioconda`  
  `conda config --add channels conda-forge`  

- check that the added channels are present in the output of the command as per example below :

  `conda info`

  the output should return the following :  

  ```   
  channel URLs : https://conda.anaconda.org/conda-forge/linux-64
                 https://conda.anaconda.org/conda-forge/noarch
                 https://conda.anaconda.org/bioconda/linux-64
                 https://conda.anaconda.org/bioconda/noarch
                 https://repo.anaconda.com/pkgs/main/linux-64
                 https://repo.anaconda.com/pkgs/main/noarch
                 https://repo.anaconda.com/pkgs/r/linux-64
                 https://repo.anaconda.com/pkgs/r/noarch```

(where **bioconda** and **conda-forge** can be spotted as clearly added.)

- install the pyEGA_cliet tool directly from anaconda repositories  

  `conda install pyega3`

- check installation path  

  `which pyega3`

  (example of output : )  
  `/mountPoint/projectName/bin/pyega3`

- test the tool is operational by running :   

  `pyega3 -d -t datasets`

---

Use the tool's help for more info  

`pyega3 --help`

Plus if possible Refer to the original tool documentation.
