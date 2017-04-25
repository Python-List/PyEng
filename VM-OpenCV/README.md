# Install virtualbox
https://www.virtualbox.org/wiki/Downloads
* Download binaries for your OS (use the package for Windows, or see this page if you are using a mainstream Linux distro,
if you use Arch or Gentoo, you might have some more work to do, like installing the correct driver , see this guide for instance: https://wiki.archlinux.org/index.php/VirtualBox#Installation_steps_for_Arch_Linux_hosts
* A pain point is to enable the virtualisation to 64 bit depending on your OS and Bios settings (see this article, particularly the "Bottom line" section, http://www.fixedbyvonnie.com/2014/11/virtualbox-showing-32-bit-guest-versions-64-bit-host-os/#.WP22Y9Ay_Dc)
if you have only 32 bit VMs enabled in Virtualbox and wish to have 64 bit VMs supported

# Install a Mint VM: 
* Download an ISO: https://www.linuxmint.com/download.php 
*use what's needed for your Virtualbox install, 32 vs 64 bits, which desktop you prefer is up to you, I personnally enjoy XFCE*

* Start VirtualBox
* Click on New
* Name it however you want (for this tutorial, I used OpenCV-Test)
* Select the type as Linux
* Select the version as Ubuntu
* Keep all the default options until the size allocation for the hard drive
* Here use at least 10 GB (as Mint requires 9.8GB to install), to be safe, double it to 20GB
(true enough, that is a lot, but for this overhead, you get a nicely configured system)
* Click on create
* Select your newly created VM
* Click on Configuration
* Go to "storage"
* Select the "empty" under IDE Controller
* Click on the CD icon next to the dropdown showing "Secondary master IDE"
* Choose "select a disk..."
* Select your previously downloaded Mint iso
* Select again your VM in the main menu
* Click on start

# The install procedure shall begin:

* First of all, patiently wait (it can take several minutes, as the OS is loading into memory, which is no small task by any mean)
*Note: Do not bother about warning/error messages, except if the system crashes (never happened to me, though if it happens let me know)*
* Let the default user log in (mint)
* On the desktop click on "Install Linux Mint"
* Keep English (except for personal use, I would recommend to always use English, as there is more help available online in this language, if any issue shall arise)
* Keep the default "Erase the disk and install Mint" (except if you know what you are doing), and click on Continue when it asks for confirmation
* Choose your TimeZone
* Choose your Keyboard Layout
(most of the time the two settings above are well recognized)
* Enter your username, password, and VM name
* Go drink several coffees
* When it's over click on Restart now
* Remove the ISO from the IDE Controller (in the configuration -> storage, see previous section)
You should be on the desktop now

# Let's install OpenCV3 with Python3

* Install build tools: `sudo apt install build-essential cmake git pkg-config`
* Install video libraries (you can use more if necessary): sudo apt install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev`
* Install the GUI features of OpenCV: `sudo apt install libgtk2.0-dev`
* (Optional) Install some functions to optimize Opencv: `sudo apt install libatlas-base-dev gfortran`
* Install pip for python3: `sudo apt install python3-pip`
* Install virtualenv (for convenience): `sudo pip3 install virtualenv virtualenvwrapper`
* Add in your ~/.bashrc: 
```bash
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
export WORKON_HOME=$HOME/.virtualenvs
```
* Source the .bashrc: `source ~/.bashrc`
* Create and switch to a new "cv" virtualenv: `mkvirtualenv cv`
(You should see (cv) appear on the command line next to your username, if you did not modify the default PS1)
* Install Python3 header and dev tools: `sudo apt install python3.5-dev`
* Install numpy: `pip install numpy`

* Checkout OpenCv:
```bash
git clone https://github.com/Itseez/opencv.git
cd opencv
git checkout 3.2.0 #or use a different version
```

* Create a build directory and generate the configuration:
 ```bash
 mkdir build
 cd build
 cmake -D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=/usr/local \
	..
```

You should see, after some time, a report including:
```
...
FFMPEG: YES
...
```

* Compile:`make -jX` (X being the number of cores)
* Again coffee is in order
* Install: sudo make install
* Add new dynamic library to your environment: sudo ldconfig
* Add the lib in your virtualenv (mine is "cv"): `ln -s /usr/local/lib/python3.5/site-packages/cv2.cpython-35m.so ~/.virtualenvs/cv/lib/python3.4/site-packages/cv2.so`


Try it:

* Switch to your virtualenv (if you deactivated it): `workon cv`
* Start python: `python`
You should see (as well as a bunch of other infos): `Python 3.5.2`
* Import opencv cv2 library: `import cv2`
* Check the version: `cv2.__version__`
* You should see: `3.2.0` (or the version you checked out of OpenCV's github)
