<h3>Follow this article to install Ubuntu and set up VSCode.</h3>
https://medium.com/nerd-for-tech/how-to-setup-windows-subsystem-linux-with-visual-studio-code-on-windows-10-b06fdbe9b30b

<h3>Install Docker</h3>
Go to the 'Install and Run Docker on WSL2' section and follow the steps.

https://dzone.com/articles/wsl2-for-dockerized-net-core-application-subhankar

<h3>Make Docker autostart</h3>

Run:
<code>sudo visudo</code>

This will open your /etc/sudoers file, which controls how sudo command are executed. We’ll want to allow our user to start docker without being prompted for a password. Add the following line to the bottom:

<code>\<username> ALL = (root) NOPASSWD: /usr/sbin/service docker *</code> - Replace <username> with your system's username.

Make Docker start by adding it in your profile file. This will run this command everytime you open the terminal.

  <code>echo 'sudo service docker status || sudo service docker start' >> ~/.bashrc</code>
