Their are 2 methods to RDP Linux machine from Windows, Linux or Mac. One is RDP and another VNC. Below are the instruction to access Arch/Manjaro from Windows.

### Install Tiger-VNC server on Arch:

```bash
## Install TigerVNC
sudo pacman -S tigervnc

## Setup password for VNC
vncpasswd

## Setup which user can use VNC and on which display server.
## below line needs to be added in file /etc/tigervnc/vncserver.users
## I am adding display 2 to be used by user "jai"
:2=jai


## Check what desktop is available for remote login
ls /usr/share/xsessions


## Setup user specific specific configuration in file
## /home/jai/.config/tigervnc/config
session=gnome
geometry=1920x1080
localhost
alwaysshared
dpi=96

## Start the VNC server (remember to use same display server number)
## This command will run VNC service on 5902
systemctl enable vncserver@:2

## most of the time system reboot is required.
sudo reboot

```

Read more about VNC on these sites:
https://forum.manjaro.org/t/root-tip-how-to-tigervnc-quick-setup/140780
https://wiki.archlinux.org/title/TigerVNC



### Download Tiger-VNC client on Windows:

Download latest Tiger-VNC viewer on Windows example: "vncviewer64-1.14.1.exe"

Open Powershell and run:

```powershell
## Login to remote machine and open SSH tunnel for VNC port
ssh jai@192.168.0.100 -L 5902:localhost:5902
```

Open Tiger-VNC command and give below URL and connect.

```
## This is becuase after SSH tunneling remote port is mapped to local port
127.0.0.1:5902
```


https://sourceforge.net/projects/tigervnc/files/stable/1.14.1/


### Trouble-shooting

#### Lock files
If connection is abruptly disconnect then a socket file will be lingering around impacting new session. To remove old files delete
```bash
## Check if file is available 
ls -rlt /tmp/.X2-lock

## Delete file and restart the service (Better to stop the service and then delete the file)
rm /tmp/.X2-lock
```

#### Permissions
Make sure the do these setting with the user who want to run VNC session. Setting up with another user make mess-up with file permissions.

#### Log files
Log files are available in `/home/jai/.vnc` directory.

#### Service 
```bash
systemctl status vncserver@:2
```

#### Firewall

Make sure required ports are open if you are not using SSH tunneling.
