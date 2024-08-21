LGBT
Linux Beginner Guids & Tutorials
 Always have timeshift or equivalent 
 Always 3-2-1 backup rule 
Maintain three copies of your data: This includes the original data and at least two copies.
Use two different types of media for storage: Store your data on two distinct forms of media to enhance redundancy.
Keep at least one copy off-site: To ensure data safety, have one backup copy stored in an off-site location, separate from your primary data and on-site backups.
Always backup important data, more important data, more copies are needed
 Never forget the master-password 
 Research everything 
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
This will drop al caches also see this site https://www.linuxatemyram.com/:
echo 3 | sudo tee /proc/sys/vm/drop_caches
 checking speciffics:
mhwd -li for gpu
mhwd -l
mhwd -kernel -li for kernel
lsb_release -si⁠rc for manjaro version
Install .wine
 there are a couple sudo pacman -S wine winetricks wine-mono wine_gecko DONT INSTALL STAGING IF YOU DONT NEED sudo pacman -S wine-staging
after that configure wine prefix with windows programs and needed fonts NEVER INSTALL ALL/EVERYTHING CARRREFOUL WITH .NET EITHER LATEST EITHER OLDER WATCH THIS https://www.youtube.com/watch?v=lI09QLkqZiE&t=1s&pp=ygUVaW5zdGFsbCB3aW5lIGNvcmVjdGx5
install appimage lawncher so you can install official appimages->https://github.com/TheAssassin/AppImageLauncher/wiki
⁠yay -S appimagelauncher⁠ or paru -S appimagelauncher⁠ or ⁠pamac build appimagelauncher
pacman -Ql <package_name> for package contents and pacman -Qo<file_path_or_software_command) for package owner

partition lsblk -fa

LANG=C sudo parted -l

free for free ram
 to find top 10 most resurse-intensive processes:
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head
BEST WAY TO SOLVE MEMORY PROBLEM IS TO CREATE SWAP PARTITION: FOR Manjaro USE THIS GUID!
https://wiki.manjaro.org/index.php?title=Swap
echo $PATH and which <software_command> for software location

sound devices aplay -L and storage usage LANG=C df -h
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
⁠⁠a good one to see memoryfree -h
sudo swapoff -a # stop swapfiles if any ->
sudo fallocate -l 10G /swapfile # make swapfile ->
sudo chmod 600 /swapfile # setup swapfile ->
sudo mkswap /swapfile # makeswapfile -> 
sudo swapon /swapfile # activate swapfile -> 
sudo swapon --show # show swapfile⁠
drop all caches from ram ⁠sync; sudo sysctl vm.drop_caches=3⁠
list all cache processes ⁠lsof /media/path/to/drive⁠->system monitor, identify and kill the sucker
