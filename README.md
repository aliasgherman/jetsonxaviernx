# jetsonxaviernx
My Journey with Xavier NX

# Keyboard is required.
I only had a USB Mouse to start up the board. To enter the user password/details, I copied some text using mouse from the license items to begin with.

# VNC option Screen resolution
NVidia has a vnc connection page. BUt we need to define virtual screen resolution in the X11.org file to have a better/higher screen resolution for remote vnc when no HDMI is plugged in

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
