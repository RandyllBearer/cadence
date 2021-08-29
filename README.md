# discord_music_bot
First stab at building a self-hosted music bot for discord.

# Environment Set-Up

This "Environment Set-Up" guide assumes that you are working on a windows machine. If you're already working in a linux environment then feel free to skip this entire chapter. If you're on MacOS I'm sorry, but you'll need to figure that one out. IDK it well enough.

- Go to https://ubuntu.com/download/desktop and download the .iso of the latest Ubuntu LTS (Long-Term-Support) branch. When we go to build our VM we'll be pulling from this .iso
- Go to https://www.virtualbox.org/wiki/Downloads and download the latest 64-bit VirtualBox distribution for Windows hosts
- Install VirtualBox, install all additional network/convenience utilities
- Once VirtualBox is ready, click the "New" button
- Decide on a name for the virtual machine, I usually do something like "linux_ubuntu", and for type/version choose an ubuntu/linux 64 bit distro.

(Note: Remember the name you choose for your virtual machine, you will need the name in a later step)

- Assign the virtual machine some memory, the more you give it the smoother it'll be. I usually assign 8 GB (8192)
- If you don't want to mess with virtual disk mounting (which will not be covered here) click "create a virtual hard disk now"
- Just choose a "VDI" (VirtualBox Disk Image), dynamically allocated, give it something like 20 GB
- You should now see your VM listed in VirtualBox with the "Powered Off" state, double click it to run the initial set-up

(Note: At this point the VirtualBox window is gonna be tiny (like 640x480), don't worry about this for now, we'll be changing it after we get the OS installed.)

- VirtualBox should now prompt you for a media / optical drive source, select the ubuntu .iso file we downloaded in step 1
- Go through Ubuntu's initial set-up set up your accounts, download your updates, install livepatch, etc. Reboot if it prompts you to
- Once ubuntu is ready, we're gonna run some commands in the terminal inside the VM. There is probably an easier way to do the following, but this is what I did and it has worked for me.

- First things first, we need some prerequisites:
```
sudo apt-get update
sudo apt-get install build-essential gcc make perl dkms
reboot
```

- Then power it back up and run to install the utilities for modifying screen resolution:
```
sudo apt-get install virtualbox-guest-utils virtualbox-guest-x11 virtualbox-guest-dkms
```

- Then we're gonna turn it off again. Also, close out of the VirtualBox application as well and open a Windows command prompt. The following command should allow our virtualbox window to render a bit more snappily.
```
"C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" modifyvm "<name of your virtual machine in VirtualBox>" --vram 256
```

- Then we can power VirtualBox back up and launch our VM again. Run the following command to finalize installing host/guest vm utilities:
```
sudo apt-get install dkms & sudo apt-get install virtualbox-guest-dkms
```

- Power off the vm, close it out, and re-launch it one last time. It should be good to go know. Window should be able to be resized correctly and the display should render sufficiently. Open VirtualBox, click on your VM, and check "Display" settings. You should now see a "Video Memory" slider at 256mb.
- Install VS Code & any application-specific extensions, such as for Javascript, Java, Ruby, code linters, bracket closers, HTML, etc.
- Open a terminal and install docker
```
sudo apt install docker.io
docker --version
```

- Create a folder in our Ubuntu OS to hold this cloned repository, somewhere like "~/workspace"
- navigate into "~workspace" with ```cd workspace```
- install git
```
sudo apt-get install git
git --version
```
