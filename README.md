# ocdy1001's Void Linux Rice
## Step 1: Install Void on your pc:
If you have Void on a usb:
0. Boot from usb.
1. Void boots and asks to login.
2. Use login: ``root``.
3. Use password: ``voidlinux``.
4. type ``sudo su``, enter. (commands from now on like ''this'')
5. ``void-installer``
6. The installer comes up, go to each field and configure
7. Have a ext4 that mounts  to ``/``
8. Have a 128M fat32 partition for boot, let it mount to ``/boot/efi``
9. Have 4G + swap partion
10. Goto install, let it do its thing.
11. When prompted to reboot, say yes.
12. Your new, clean, sexy Void os boots now into the terminal. There is nothing else.
## Step 2(optional) Configure wifi:
0. This is for when you don have a cable and the network section in the installer failed.
1. Login as root, i had one command where sudo would do.
2. View your network interfaces ``sudo ip link show``
3. Pick your interface, called _interface from now.
4. List all networks by running ``sudo iw dev wlp2s0 scan | grep -i ssid``
5. Pick one called _ssid from now.
6. You know the password for the network, called _key from now.
7. Backup example conf: ``cp /etc/wpa_supplicant/wpa_supplicant.conf /etc/wpa_supplicant/wpa_supplicant-std.conf``
8. Populate the conf with our data. ``wpa_passphrase _ssid _key >> /etc/wpa_supplicant/wpa_supplicant.conf``
9. For some reason had to do ``killall wpa_applicant``;
10. ``wpa_supplicant -i _interface -c /etc/wpa_supplicant/wpa_supplicant.conf``
11. ``dhcpcd _interface``
12. Should work now, ``xbps-install -S`` should work.
13. If not, i also had to repeat some steps. If it prompts that it has this file in /usr/.... after step 10, just remove it with ``rm filename``. and repeat step 10.
14. ``wpa_supplicant -B -i<interface_name> -c<path/to/configuration/file> -Dwext`` could also work at step 10.
## Step 3 Install Rice:
0. Assuming you have internet access now and you only have void installed: there is only a terminal. No windows etc.
1. Login as a normal user.
2. Install git: ``sudo xbps-install -Sy git``
3. Make a dir for all git projects: ``mkdir ~/git``
4. Goto the new dir: ``cd ~/git``
5. Pull this repo(assuming you read this on another device): ``git clone https://github.com/ocdy1001/VoidLinuxRice.git``
6. ``cd /``
7. Give exec rights: ``chmod +x ~/git/VoidLinuxRice/install.sh``
8. Run it ``~/git/VoidLinuxRice/install.sh``
9. It does stuff(installing using xbps and copying config files).
10. You now have the programs, my configs, repos installed, system updated etc.
11. ``startx``
12. Should see a space image background.
13. Press ``windowskey+enter`` to fire up a terminal.
14. ``windowskey+shift+b``, to fire up the browser, log in, browser should be dark themed, else choose gtk+ in the settings.
15. Done.
