![image](https://github.com/user-attachments/assets/f11f5d3a-4bc3-4ead-ba16-23fee96c62ab)
# Automated Remote Observatory Control &amp; Guard

ARO-Master is a project to implement an affordable and easy to build remote control system for Automated Remote/Robotic Observatories.
It's composed of two components:

### ARO-Master control box:
Hardware & firmware that implement the server/daemon for Observatory control (remote and local). This is the main brains that allows you to connect and control all the equipment, open/close the roof, see weather conditions, see the sky, see the observatory interior, control user login, control the Piers etc.
### Pier-Relays box:
Relays box for each pier that connected to ARO-Master, allows you to turn on and off the equipment (mount, PC, power box, etc.) 

## Overview:
I started this project in 2015 and to date it has undergone several developments in terms of hardware and software. The first version was developed around an STM32-E407 microcontroller but this quickly proved to be insufficient for everything I wanted to implement, both in terms of hardware and firmware features.
The current version uses a **Raspberry PI 4** with at least 2GB of memory for the **ARO-Master box** and uses **RP2350** microcontrollers for the **Pier-Relay box**.

This system is in use in my personal observatories and those of some colleagues, two of which are located in Tunisia and are remotely controlled from Europe.

## License:
When I made the decision to share this project I intended to make it public, but recent developments have changed that intention. So, for now I will share the firmware only in its compiled form (without the sources) and the hardware schematics are provided as reference material only.
There will be a commercial version that can be purchased as a kit or already assembled, in addition to the two electronic components mentioned (ARO-Master box & Pier-Relays box) there is also extra hardware that can be purchased by end users, such as the rack and pinion and motor for ceiling movement.

