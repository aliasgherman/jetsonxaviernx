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

# Install jetson-inference from Source
Containers are fine, but almost nothing works on this platform. I mean if you go for Tensorflow, then you are unable to get a container with latest libraries. Same for pytorch. And you get one container and then want to install other libraries or updates but the eco-system is simply behind.

So, on my second run, I would prefer jetson-inference installation from source. And then build my developer resources from there.

https://github.com/dusty-nv/jetson-inference/blob/master/docs/building-repo-2.md


# Great blog
https://medium.com/swlh/the-newbie-guide-to-setting-up-a-jetson-nano-on-jp4-4-230449346258

# Install pycuda
sudo nano ~/.bashrc
export PATH=${PATH}:/usr/local/cuda/bin
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/cuda/lib64

Save and exit.

Check if nvcc --version is working on command line now. If yes, then proceed to next command
pip3 install pycuda

# Deepstream Python Apps
May need to change chmod -R 777 for /opt/nvidia else all modifications will require sudo
https://docs.nvidia.com/metropolis/deepstream/dev-guide/text/DS_Python_Sample_Apps.html

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
