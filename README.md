# cyberdyne_ethercat
#Installing Skynet Cyberdyne Project
The Downloads
1.	Debian Buster Cyberdyne Image: https://github.com/grotius-cnc/LINUX_RTOS/releases/tag/1.0.0
2.	Software files (important to match versions): https://sourceforge.net/projects/skynet-software/files/skynet_soft-1.0.tar.gz/download
3.	Skynet Project: https://github.com/grotius-cnc/skynet_robot_control_rtos_ethercat/releases/download/1.0.23/Skynet_Project-13.tar.gz

#Setting up the OS


#Installing Software Files
Type ip a and figure out the name of the Ethernet port you want to use for ethercat
![image](https://github.com/adnanamir010/cyberdyne_ethercat/assets/80971069/1152c13c-34f3-4847-8da4-1e38824a5a2b)
 
In my case it is enp0s3

Navigate to skynet_soft-1.0/ethercat/data/ and edit the etheract_install.sh script

![image](https://github.com/adnanamir010/cyberdyne_ethercat/assets/80971069/f09c3c1d-3e1d-4ef6-ad52-9b6dfc5b7a1d)

Replace the device name mentioned there with your own

![image](https://github.com/adnanamir010/cyberdyne_ethercat/assets/80971069/bb3855a5-73fe-40c1-88f0-ffad46d41ffa)

Save and exit

#Fixing Qt
export QT_SELECT=qt5
In a terminal type: sudo nano /usr/lib/x86_64-linux-gnu/qtchooser/qt5.conf
When it opens replace the first line with /usr/local/include/qt/5.15.1/gcc_64/bin/
Now copy the contents of this file and create a file called default.conf in the same folder
Paste the contents of qt5.conf in default.conf
Run qmake –version to verify that you are using Qt version 5.15.1 in /usr/local/include/qt/5.15.1/gcc_64/lib

#Compiling the project
qmake 'QMAKE_CFLAGS_ISYSTEM=-I'.
export LD_LIBRARY_PATH=/usr/local/lib
. /usr/local/include/linuxcnc-rip/scripts/rip-environment

