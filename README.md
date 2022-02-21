## Project description
###  What is the aim of this project?
The aim of the project is to analyze mobile application vulnerabilities based on OWASP Security Shepherd tool. We will analyze issues from OWASP TOP 10 list, examine what vulnerabilities exist in applications and what are their consequences.
###  Preparing the work environment

 - Download the files **owaspSecurityShepherd_v3.1_VM.zip** and **owaspSecurityShepherd_v3.2.3_MobileDevice.7z** from the latest available version on [OWASP's website](https://github.com/OWASP/SecurityShepherd/releases) (as of 24.01.2022 it is 3.1).
 - Unzip the files (e.g. 7zip) and mount the image first in Oracle VM Virtual Box (recommended) or another virtual machine program. 
 - Change the network settings of the machine to "Host Only" mode
 - Start the machine, after a moment you should see the Linux command line, the machine will ask you to log in - log in using the login ***securityshepherd*** and password ***shepherd3.1***
 - After logging in, type the command *ifconfig* into the terminal and check the first address on the list and type it into the browser on your computer (the host of the virtual machine). 
 - Log in using the ***admin*** login and ***password*** password.
 - In the *Admin* tab, go under *Module Management* and then to *Change Module Layout*, where we enable *Tournament mode. 

The first VM is used to explore the content and verify the correctness of the tasks, now we'll move on to the actual part.

 - We import the second image (Mobile Device) into the VM Virtual Box.
 - When the machine starts, we go into the settings and connect the machine to the Internet in *Bridged* mode.
 - In addition, we "unclick" in the *Input* tab of the Virtual Box the integration of the mouse. 
 - The machine is ready to run. To move between the GUI and the terminal, use the keyboard shortcut ALT+F1 (terminal), or ALT+F7 (GUI). 



### Tools and useful commands to complete the lab.
We can complete the lab using only the tools included in the downloaded files, note that in the folder with the mobile machine, we have a package with dex2jar, and Java Decompiler. 
Moreover, useful commands will be mainly the basic "unix" ones - cd, cat, ls.



