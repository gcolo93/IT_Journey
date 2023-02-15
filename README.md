# IT_Journey
Collection of IT information

## Disclaimer
Majority of all code and files are done using Visual Studio Code  
Most processes described will be the base minimum required to complete tasks  
There are more technical ways of completing these tasks that will not be discussed here  

## Visual Studio Code Installation

### Windows
Download exe from here: https://code.visualstudio.com/download  

### Linux
Step 1: Import Microsoft GPG key
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc  

Step 2: Add VS Code repository
    sudo tee /etc/yum.repos.d/vscode << ADDREPO  
    [code]  
    name=Visual Studio Code  
    baseurl=https://packages.microsoft.com/yumrepos/vscode  
    enabled=1  
    gpgcheck=1  
    gpgkey=https://packages.microsoft.com/keys/microsoft.asc  
    ADDREPO  

Step 3: Install VScode
    sudo yum install code

Step 4: Launch VScode
    code

### Mac

## Cloning Process
Click the 'Code' drop down list  
Copy the https link  
Open source control in VScode  
Clone and save repo  


## Commit Process
### WARNING: DO NOT COMMIT TO MAIN
Change branch from main to desired branch  
    Bottom left of VScode UI  
Open source control  
Enter commit message  
Commit
Sync Changes







