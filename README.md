# jetsonxaviernx
My Journey with Xavier NX

# Keyboard is required.
I only had a USB Mouse to start up the board. To enter the user password/details, I copied some text using mouse from the license items to begin with. Else use a Ethernet connection for the first connection and perform ssh operations. Use vnc option so that you can setup the WIFI password (if you dont want to modify wpa files).
https://crookm.com/journal/2018/sharing-wifi-connection-over-ethernet

# VNC Installation on Xavier
https://developer.nvidia.com/embedded/learn/tutorials/vnc-setup

# VNC option Screen resolution
sudo apt-get install nano //cause vi is for mad people
sudo nano /etc/X11/xorg.conf

https://www.fatalerrors.org/a/jetson-nano-configuration-vnc.html

Add below in end of file and then reboot

Section "Screen"
   Identifier    "Default Screen"
   Monitor       "Configured Monitor"
   Device        "Tegra0"
   SubSection "Display"
       Depth    24
       Virtual 1920 1080 # Modify the resolution by editing these values
   EndSubSection
EndSection


# Anaconda ??? 
Working on the aarch64 download from archives of anaconda.

https://repo.anaconda.com/archive/

The file I used is Anaconda3-2021.05-Linux-aarch64.sh

# Setup remote jupyter server

On Xavier after installing ANaconda,
jupyter notebook --generate-config

THen

jupyter notebook password //setup a password here

Then run

jupyter notebook --no-browser

Now come to the laptop/pc (remote) and run

ssh -L 8080:localhost:8888 desktop@192.168.100.26
here desktop is the username on nvidia and 192.168.x.x is its IP. 8080 is what I will use on my laptop/

Now on a browser in laptop, run
localhost:8080 and viola. You are into the jupyter notebook of Xavier.
