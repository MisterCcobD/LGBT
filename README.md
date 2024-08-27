LGBT
Linux Guids & Beginner Tutorials
 Always have timeshift or equivalent 
 Always 3-2-1 backup rule 
Maintain three copies of your data: This includes the original data and at least two copies.
Use two different types of media for storage: Store your data on two distinct forms of media to enhance redundancy.
Keep at least one copy off-site: To ensure data safety, have one backup copy stored in an off-site location, separate from your primary data and on-site backups.
Always backup important data, more important data, more copies are needed
 Never forget the master-password 
 Research everything 

General things and good practices

Fergot user password? well this method is sort of cross-compatible
do this from live usb :
Mount the partition into usb-live in /mnt then enter access chroot with ⁠su⁠ an then just change user’s password with ⁠passwd username⁠enternewpassword enternewpassword  or ⁠passwd #for root password⁠
then exit. You remember the username right? Oh.....boot in the os, check username and start again...
tip for Manjaro, from liveusb do this and select the proper OS/DRIVE from the list and do it like this
⁠manjaro-chroot -a
passwd #for root⁠ enternewpassword enternewpassword
passwd username #for user password⁠⁠ enternewpassword enternewpassword

System logs and app logs
install Gnome-logs very good for logs

The export LANG=C command
is used in Unix-like operating systems (such as Linux) to set the LANG environment variable to C. This has specific implications for how programs handle language and locale settings
⁠export LANG=C⁠ - is the default locale for Unix systems. It specifies standard, predictable behavior that doesn't depend on the system's language or regional settings. This locale uses the ASCII character set, and programs behave in a consistent way regardless of the user's actual location or language preferences.
After running this command, all subsequent commands in the same terminal session will use the C locale. To revert to the default locale, you would either unset the LANG variable or set it to the appropriate locale (e.g., en_US.UTF-8).

Write logs into files with tee
with this command i can redirect any displayed info in terminal by ⁠|⁠redirecting the command and use tee to write into some file somewhere:
⁠inxi -b | tee /path/to/file/basic-info.log⁠ with this i  display basic info about my system and redirect it to basic-info.log in /home/user/Desktop/basic-info.log
dpkg --get-selections | tee /path/to/file/packages.list⁠ with this command i listed all packages installed on Ubuntu-based system and basically created or wrote into a file named  packages.log in Desktop

quick check filesystems
 ⁠df -m⁠

Cheeck partitions
lsblk -fa
LANG=C sudo parted -l
free to show memory in short

Nvidia specifics
  carefully  research this  everytime  you want to experiment:⁠nvidia-smi -h⁠ & ⁠nvidia-smi power-hint

arch
sudo pacman -Syyy for package updates
sudo pacman -Syyu for package upgrades

enable aur 
sudo pacman -S --needed git baseto install base github → git clone https://aur.archlinux.org/yay.git → cd yay -> makepkg -si → yay --version
install lenopow from git ( download file archive then make install then lenopow -h
install Brave always sudo pacman -S brave-browser
inxi --admin --verbosity=7 --filter --width for device info when needed combined with inxi -Fazy for device info and there is Manjaro Log helper app for the same thing
this one is to show log journal
journalctl -b-1 -p4 --no-pager 

This will drop al caches also see this site https://www.linuxatemyram.com also check this for maintanance https://wiki.manjaro.org/index.php?title=System_Maintenance
echo 3 | sudo tee /proc/sys/vm/drop_caches
 checking Nvidia specifics:
mhwd -li for gpu
mhwd -l
mhwd -kernel -li for kernel
lsb_release -si⁠rc for Manjaro version

Install .wine
 there are a couple sudo pacman -S wine winetricks wine-mono wine_gecko DONT INSTALL STAGING IF YOU DONT NEED sudo pacman -S wine-staging
after that configure wine prefix with windows programs and needed fonts NEVER INSTALL ALL/EVERYTHING CARRREFOUL WITH .NET EITHER LATEST EITHER OLDER WATCH THIS https://www.youtube.com/watch?v=lI09QLkqZiE&t=1s&pp=ygUVaW5zdGFsbCB3aW5lIGNvcmVjdGx5
install appimage lawncher so you can install official appimages->https://github.com/TheAssassin/AppImageLauncher/wiki
⁠yay -S appimagelauncher⁠ or paru -S appimagelauncher⁠ or ⁠pamac build appimagelauncher

 to find top 10 most resurse-intensive processes:
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head
BEST WAY TO SOLVE MEMORY PROBLEM IS TO CREATE SWAP PARTITION: FOR Manjaro USE THIS GUID!
https://wiki.manjaro.org/index.php?title=Swap
system monitoring: htop
piper for mouse settings⁠

debian
install inxi ⁠apt install inxi⁠
install gdebi so you can install downloaded official .deb apps later ⁠apt install gdebi gdebi-core⁠
install appimage lawncher so you can install official appimages->https://github.com/TheAssassin/AppImageLauncher/wiki/Install-on-Ubuntu-or-Debian
sudo apt install software-properties-common
sudo add-apt-repository ppa:appimagelauncher-team/stable
sudo apt update
sudo apt install appimagelauncher

⁠memory & swap - https://forums.linuxmint.com/viewtopic.php?t=388392
⁠⁠a good one to see memoryfree -h⁠
To configure swap memory do these:
sudo swapoff -a # stop swapfiles if any ->
sudo fallocate -l 10G /swapfile # make swapfile ->
sudo chmod 600 /swapfile # setup swapfile ->
sudo mkswap /swapfile # makeswapfile -> 
sudo swapon /swapfile # activate swapfile -> 
sudo swapon --show # show swapfile⁠
drop all caches from ram ⁠sync; sudo sysctl vm.drop_caches=3⁠
list all cache processes ⁠lsof /media/path/to/drive⁠->system monitor, identify and kill the sucker
cat /proc/meminfo | grep -i cached Displays the cached memory specifically.

  Performance 
DXVK_FILTER_DEVICE_NAME="NVIDIA" MANGOHUD_CONFIG=gpu_name mangohud gamemoderun %command%
"dxvk_filter..." will tell Proton to skip all devices not having "NVIDIA" in their name. To ensure exact name of GPU, you can use vulkaninfo --summary and use that exact name in front of dxvk_filter... (this only works on DX8 to DX11 games though. for DX12 games if this did not work, one can use VKD3D_VULKAN_DEVICE=0 or VKD3D_VULKAN_DEVICE=1 depending on dGPU being known to the system as first or second device).
"mangohud" will show you name of the GPU doing the rendering. This should show your Nvidia GPU. When performance drop occurs, pay attention if the name changes to your AMD Renoir iGPU...
"gamemoderun" will ensure your laptop does not go into a power saving state.
&

DXVK_FILTER_DEVICE_NAME="NVIDIA" DXVK_HUD=1 gamemoderun %command% ⁠ This should create an overlay showing the renderer device on top left of the screen. This should show the name of your Nvidia GPU. When performance throttles, see if that name changes to another device or not. BTW since we already used a solution (DXVK_FILTER_DEVICE_NAME="NVIDIA"), this performance problem might not happen again. So try removing this as well if you were unable to replicate this issue.
 PERONAL NOTE - JUST IN CASE GAMEMODE BROKE OR MANGOHUD BROKE, REINSTALL
