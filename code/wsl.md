

**Install Windows Terminal**

Windows Terminal is a better shell for Windows. Everything else (including coding, etc) will happen in Windows Shell. Your Linux virtual machine will also run inside Windows Terminal. 
you can customize the look and feel here - https://www.youtube.com/watch?v=mnWA4EP2Zhw

https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701

When you run Windows Terminal - it lets you choose which kind of shell to run. Choose Powershell (for now). Later you will choose Ubuntu.

**OS Requirements**

Windows 10. Version 1903 or higher, with Build 18362 or higher.
To check your version and build number, type `winver` in Windows Terminal.

Please make sure that virtualization is enabled inside of your computer's BIOS. The instructions on how to do this will vary from computer to computer, and will most likely be under CPU related options.

**Setup Windows Subsystem for Linux - Version 2 (WSL2)**

Follow these steps

- Open Windows Terminal as administrator. You can do this by right clicking on Windows Terminal and choosing "run as administrator"
- Run in Windows Terminal Powershell
```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```
- restart your machine 
- Run in Windows Terminal Powershell
`dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`
- restart your machine
- Download and install - https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
- restart your machine
-  Run in Windows Terminal Powershell
`wsl --set-default-version 2`
- Open Windows Store (https://aka.ms/wslstore) and search for "Linux"
- Install Ubuntu
- https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6#activetab=pivot:overviewtab
- The first time you launch a newly installed Linux distribution, a console window will open and you'll be asked to wait for a minute or two for files to de-compress and be stored on your PC. All future launches should take less than a second. You will then need to create a user account and password for your new Linux distribution.
- CONGRATULATIONS! You've successfully installed and set up a Linux distribution that is completely integrated with your Windows operating system!


**Set up VSCode**

First, to use VS code on WSL, you will need to install on windows and access it via remote since WSL does not have a graphical interface
- install vscode - https://code.visualstudio.com/download
- install WSL extension in vscode - https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl  (another way to install is Open your VS code and click
`ctrl +shift+x` and type *“wsl”* on the market search bar. Select Remote — WSL and press install.)
- Once the installation is completed, head back to the Ubuntu terminal and type `code .` (notice *“code” + “.”*). When you click enter, you will see is the message `“the Installing VS Code Server c7d83e57…”` What is happening here is WSL is installing a smaller VS code server that matches the VS version installed on Windows (client-side). The server will then communicate to the VS code on Windows, and the small server will receive any changes we made on Windows VS code. The server will, in turn, install and host extensions in WSL
- From this point forward, You can launch a new instance of VS Code connected to WSL by opening a WSL terminal, navigating to the folder of your choice, and typing `code .`

**Install Docker**

Go to the 'Install and Run Docker on WSL2' section and follow the steps.

- Update your Linux software repository with `sudo apt-get update`
- Download Docker dependencies `sudo apt-get install apt-transport-https ca-certificates curl software-properties-common`
- Add Docker PGP key `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add –`
- Install the Docker Repository `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release) -cs) stable"`
- Update the software repository `sudo apt-get update`
- Install the latest Docker version `sudo apt-get install docker-ce`
- Check Docker service status `sudo service docker status`
- Running Docker service `sudo service docker start` (you need to do this once each time before running docker in your windows terminal)


