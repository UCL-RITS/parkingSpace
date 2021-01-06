# Login with custom credentials to EGA/EBI remote servers

## Prerequisites

- Guide 00 - miniconda installation
- Guide 01 (or Guide 02 alternatively) - pyEGA_client installation
- online registration to EGA/EBI website to acquire User Access Credentials

## Users Access

In order to be able to download data-sets you must be registered on the EGA website and upon registration receive your **User Access Credentials** ; these will be needed by the tool to access the remote servers on your behalf, and allow you to download the needed data-sets.

Credentials can be passed to the pyEGA client tool in 2 ways :  

1. **interactive**, via the command line ( ! ADVISED METHOD ! )

  `pyega3 <command1> <argument1>`

  just run the tool as above and when prompted input your username and then your password.


2. using a `.json` **configuration file** with the credentials stored in it ( ! LESS SECURE METHOD ! )  

- clone the default config-file into your home folder; modify the new file with your text editor of choice to include only your own EGA credentials:  

  `cp ega-download-client/pyega/config/default_credential_file.json /home/my_username/pyEGA3-Creds.json`

  edit `/home/my_username/pyEGA3-Creds.json`

- when running the tool, point to your current credentials file with the `-cf` flag  

    `pyega3 -cf /home/my_username/pyEGA3-Creds.json <command1> <argument1>`




**IMPORTANT :**  

If you are working in a shared environment or project folder, please consider that **we strongly recommend our users to use method 1. above** , and  advise against the use of method 2. for reasons related to data privacy and security.

If you choose to use method 2 for any reason, please make sure that you store your credentials in a `.json` file that resides in **your own (private) home folder** and **NOT in a group-shared/accessible folder**, such as normally is the case for projects folders, for instance.  



---

###### examples:

- test that your own credential-file is working and check what data-sets you have access to :

  `pyega3 -cf /home/my_username/CredentialsFile.json datasets`

---
**HINT :**  
For more information and instructions, please see Refs below, "video tutorial" at video paragraphs :
- Defining your credentials file ( at [0:41"] of the recording )  

- Interactive login ( at [8':27"] of the recording )



---

### Refs

###### pyEGA3 - EGA python client version 3.4.0
[https://github.com/EGA-archive/ega-download-client](https://github.com/EGA-archive/ega-download-client)  
###### pyEGA   
[https://github.com/blachlylab/pyega](https://github.com/blachlylab/pyega) by James Blachly

###### Video Tutorial  
[https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=be79bb93-1737-4f95-b80f-ab4300aa6f5a](https://embl-ebi.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=be79bb93-1737-4f95-b80f-ab4300aa6f5a)
