Creating a Windows + WSL (Windows Subsystem for Linux) development environment for RedCarpet dev and analysts
===============================



**Install Windows Terminal**

Windows Terminal is a better shell for Windows. Everything else (including coding, etc) will happen in Windows Shell. Your Linux virtual machine will also run inside Windows Terminal. 

OPTIONAL: you can customize the look and feel here - https://www.youtube.com/watch?v=mnWA4EP2Zhw  & https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701


**OS Requirements**

Windows 10 version 2004 and higher (Build 19041 and higher) or Windows 11.  
To check your version and build number, type `winver` in Windows Terminal.

Please make sure that virtualization is enabled inside of your computer's BIOS. The instructions on how to do this will vary from computer to computer, and will most likely be under CPU related options.

**Setup Windows Subsystem for Linux - Version 2 (WSL2)**

reference: https://docs.microsoft.com/en-us/windows/wsl/install

Follow these steps

- Open Windows Terminal as administrator. You can do this by right clicking on Windows Terminal and choosing "run as administrator"

- Run in Windows Terminal Powershell
```
wsl --install
```
- The first time you launch a newly installed Linux distribution, a console window will open and you'll be asked to wait for a minute or two for files to de-compress and be stored on your PC. All future launches should take less than a second. You will then need to create a user account and password for your new Linux distribution.

![image](https://user-images.githubusercontent.com/76883/136389494-ef7382fb-3099-4708-80ba-7b37a8c189bf.png)


- CONGRATULATIONS! You've successfully installed and set up a Linux distribution that is completely integrated with your Windows operating system!
- close Windows Terminal and reopen. You will see a new tab in Windows Terminal that says "Ubuntu". From now on, everything else will be done in this terminal.


**Set up VSCode**

First, to use VS code on WSL, you will need to install on windows and access it via remote since WSL does not have a graphical interface
- install vscode - https://code.visualstudio.com/download
- install WSL extension in vscode - https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl  (another way to install is Open your VS code and click
`ctrl +shift+x` and type *“wsl”* on the market search bar. Select Remote — WSL and press install.)
- Once the installation is completed, head back to the Ubuntu terminal and type `code .` (notice *“code” + “.”*). When you click enter, you will see is the message `“the Installing VS Code Server c7d83e57…”` What is happening here is WSL is installing a smaller VS code server that matches the VS version installed on Windows (client-side). The server will then communicate to the VS code on Windows, and the small server will receive any changes we made on Windows VS code. The server will, in turn, install and host extensions in WSL
- From this point forward, You can launch a new instance of VS Code connected to WSL by opening a WSL terminal, navigating to the folder of your choice, and typing `code .`



**Install Python**
- Go to https://docs.conda.io/en/latest/miniconda.html to find the list of miniconda releases
- download the release. remember when you download stuff, the file and goes to a different directory than your WSL home directory. ***we strongly recommending copying it to home directory. Running linux commands in wsl from other directories is VERY SLOW**
- Run the installation script: `$ bash miniconda[YOUR VERSION].sh` ( example `$ bash miniconda-3-5.2.0-Linux-x86_64.sh`)
- alternatively, you can do this
    - `wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`
    - `bash Miniconda3-latest-Linux-x86_64.sh`
    - `source ~/.bashrc`
   
- Read the license agreement and follow the prompts to accept. When asks you if you'd like the installer to prepend it to the path, say yes.
- Close the terminal and reopen it to reload .bash configs.
- Manually add the miniconda bin folder to your PATH. To do this, I added "`export PATH=/home/user1234/miniconda3/bin:$PATH`" to the bottom of my `~/.bashrc` file
- run `which python` it should work !

**Install Jupyter** 
- if you install miniconda above, then jupyter comes pre-installed
- To open jupyter, type `$ jupyter notebook --no-browser`. The no browser flag will still run Jupyter on port 8888, but it won't pop it open automatically. it's necessary since you don't have a browser (probably) in your subsystem. In the terminal, it will give you a link to paste into your browser. If it worked, you should see your notebooks!


(data scientists, risk and strategy teams setup ends after you install jupyter. dev/tech teams please continue forward)
--------------------

**Install Docker**

- Update your Linux software repository with `sudo apt-get update`
- Download Docker dependencies `sudo apt-get install apt-transport-https ca-certificates curl software-properties-common gnupg  lsb-release`
- Add Docker PGP key `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`
- Install the Docker Repository `echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
- Update the software repository `sudo apt-get update`
- Install the latest Docker version `sudo apt-get install docker-ce docker-ce-cli containerd.io`
- Running Docker service `sudo service docker start` (you need to do this once each time before running docker in your windows terminal)
- Check Docker service status `sudo service docker status`
- sudo docker run hello-world


**Running k3s on WSL2**
- [https://www.youtube.com/watch?v=TLugDYu0QYQ](https://www.youtube.com/watch?v=TLugDYu0QYQ)

**Recommended: Memory Optimization for WSL**
https://github.com/microsoft/WSL/issues/4166#issuecomment-526725261

Create a `%UserProfile%\.wslconfig` file in Windows and use it to limit memory assigned to WSL2 VM.
NOTE: to go to `%UserProfile%` , just open File Explorer and put `%UserProfile%` in address bar. you will go to the right directory

Example
```
[wsl2]
memory=6GB
swap=0
localhostForwarding=true
```

This will still consume the entire 6GBs regardless of Linux memory usage, but at least it'll stop growing more than that.

** WSL hangs**
Sometimes you will notice that WSL hangs. Especially after a reboot. Even opening a new WSL/Ubuntu window in Windows Terminal will hang.

the fix is easy. In Windows Terminal, type `wsl.exe --shutdown` and then wait until the command completes. Then you can open a new WSL/Ubuntu terminal

