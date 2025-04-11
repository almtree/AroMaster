# Firmware lastest version: V1.7

The **Aro-Master** software/firmware runs as a '_daemon_' (a computer program that runs as a background process) on the Raspberry Pi and exposes its UI (user interface) through the embedded web-server.

Once connected to your LAN (your home or local network) one can access the ARO-Master web-server using a web browser that supports HTML 5.

I won't go into details on how to set up the Raspberry Pi (take a look here: https://www.raspberrypi.com/software/), the requirements are basically a ***Raspberry Pi 4*** with at least ***2GB RAM*** and Raspberry Pi OS installed, it's assumed that you have an basic understanding of how to access and use Linux on a Raspberry Pi, including how to use the command line to edit some text.

- Download the zip file with the latest firmware
- Extract the contents to that file to `/home` folder on the Rpi
- There will be created a folder with the name `/home/aro-master`
- Edit the `config.txt` file located in `/boot/firmware`
```
sudo nano /boot/firmware/config.txt
```
- Add a new line at the bottom immediately before `exit 0` and past the following line of text:
```
sudo /home/aro-daemon/aro-d
```

The final version of the file `/boot/firmware/config.txt` should look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Print the IP address
_IP=$(hostname -I) || true
if [ "$_IP" ]; then
  printf "My IP address is %s\n" "$_IP"
fi

sudo /home/paulo/ARO-Daemon/aro-d
exit 0
```
- Reboot the Raspberry Pi `sudo reboot now`

After that you should be able to access the web-page using the URL **http://aro.local** or **http://aro.home**

> [!NOTE]
> The _Assembled version_ of the ARO-Master Box comes with all hardware and software already installed

## The web page consists of
- System data info
- Weather data info
- Setup and configuration
- Image from the sky camera (if available)
- Meteo satellite image

The interface is supposed to be self-explanatory ... but sometimes there is a great distance between the 'supposed' and the reality, please let me know if you have any questions using  [GitHub Discussions](https://github.com/almtree/aro-master/discussions).


![firm_06](https://github.com/user-attachments/assets/156c094b-b79d-4d6f-9731-3b979528e2fb)

![firm_05](https://github.com/user-attachments/assets/6640d7d3-6aa2-4a54-b58c-dbec4bc60434)

![firm_04](https://github.com/user-attachments/assets/3fb8d5a0-7e9e-4977-8a98-c028b906dfed)

![firm_03](https://github.com/user-attachments/assets/e4367bbc-c2fe-441b-b787-2fd4c20e3e1e)



