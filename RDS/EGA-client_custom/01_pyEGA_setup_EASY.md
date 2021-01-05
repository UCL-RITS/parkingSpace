
### Setup the Env to run pyEGA tool from RDS nodes ( EASY )

The following instructions can be run only when anaconda/miniconda setup has been successfully performed and the environment is functional for the user.

Please get in touch if you experience any trouble running the commands in the following guide.

#### Instructions

- add the requested repositories needed by the tool as per its original Repo instructions  

`conda config --add channels bioconda`  
`conda config --add channels conda-forge`  

`conda info`

the output should return:

```
channel URLs : https://conda.anaconda.org/conda-forge/linux-64
               https://conda.anaconda.org/conda-forge/noarch
               https://conda.anaconda.org/bioconda/linux-64
               https://conda.anaconda.org/bioconda/noarch
               https://repo.anaconda.com/pkgs/main/linux-64
               https://repo.anaconda.com/pkgs/main/noarch
               https://repo.anaconda.com/pkgs/r/linux-64
               https://repo.anaconda.com/pkgs/r/noarch
```
- install the pyEGA_cliet tool directly from anaconda repositories  

  `conda install pyega3`

- check installation path  

  `which pyega3`

  (example of output : )  
  `/mnt/gpfs/live/ritd-ag-project-rd0000-projectA/bin/pyega3`

- test the tool functions  

  `pyega3 -d -t datasets`

---

Use the tool's help for more info  

`pyega3 --help`

Refer to the original tool docs.
