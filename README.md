![image](https://github.com/user-attachments/assets/f11f5d3a-4bc3-4ead-ba16-23fee96c62ab)
# Automated Remote Observatory Control &amp; Guard

***ARO-Master*** is an affordable and integrated control system for ***Automated Remote/Robotic Observatories*** with **Roll-Off-Roof** or non-rotating **Clamshell Domes** design.

A _***Remote*** Observatory_ is any observatory that can be operated without a physical presence near the equipment, whether the user is in the next room or on the other side of the planet. Of course, if the user is in the next room, any problems that arises can be more easily resolved, on the other hand if you are on the other side of the planet things are more complicated, in the development of _Aro-Master_ we tried to take this into account.    
In addition to sliding _Roof_ movement management and _Pier power_ management, one of the essential requirements was the need to close the roof even when the power supply fails, for this purpose an integrated switching power supply (SMPS) + uninterruptible power supply (UPS) + battery management system (BMS) system was used, along with a simple 12V external battery (Gel, AGM, Acid), which allows security for remote operation.

## Overview
This project started in 2015 and to date it has undergone several upgrades in terms of hardware and software. The first version was developed around an STM32-E407 microcontroller but this quickly proved to be insufficient for everything I wanted to implement, both in terms of hardware and firmware features. The current version uses a **Raspberry PI 4** with at least 2GB of memory for the ***ARO-Master box*** and uses **RP2040/RP2350** microcontrollers for the ***Pier-Relay box*** .  
This system is in use in my personal observatories and those of some colleagues, two of which are located in Tunisia and are remotely controlled from Europe.

**The software/firmware is fully proprietary and written in C/C++, it doesn't have dependencies on external libs or code. Remote control must be taken very seriously, all code must be fully under our control.**

## Main components are:
### ***ARO-Master*** control box
Hardware & firmware that implement the server/daemon for Observatory control (remote and local).  
This is the main brains that allows you to connect and control all the equipment, open/close the roof, see weather conditions, see the sky, see the observatory interior, control Piers power etc.
### ***Pier-Relays*** box <sup>optional</sup>
Relays box for each _Pier_ that allows you to turn on and off the equipment (mount, PC, power box, etc.). This is basically a Smart Plug with the difference that it is controlled by the pier's PC.


### Internal firmware Web Server for magement and system setup
- No software instalation needed
- Accessible from anywhere
- OS independent using Windows, Linux, Android or Mac browser
- Auto firmware updates
- Direct integration with _uAstro SkyPatroll_ (MSP) or _uAstro Weather Station_ (MWS)
### Alpaca Daemon for Multiclient and MultDevice
- Alpaca Discovery aware (no setup or configuration needed)
- Implements Alpaca devices Dome, Switch (system switches and pier relays), ObservingConditions and SafetyMonitor
- No need to install ASCOM drivers
- Devices can be accessed simultaneously from different computers
### Faults monitoring
- Mains voltage
- Battery voltage
- Motor current
- Weather (rain, clouds)
- Wind speed, temperature, humidity and dew point
- Lux
- External alarm
- Logged users
- Internet not available
- System CPU temperature
- Sunrise 
### Other functionalities
- Watchdog reboots system on hardware/software fails
- Sends Email on Fault or roof open/close
- _ARO-Master box_ internal cool fan and heater control
### Piers power control
- Depending on the system configuration, up to 32 pier power relays can be controlled.
- Pier power relay reset with timed rearm (for pier reboot)
- Auto user logoff timer (turns off all relays)
- ‘Relay box’ is installed at each pier
- Daisy-chain UTP cable  pier connection, easy and less cabling
### Roof/shutter Safety – Automatic close on:
- Power fail (Mains or Battery)
- Meteo event (rain, wind, lumens, clouds)
- External signal input (third-party control)
- Optional close at Astronomical Sunrise
### Roof/shutter Safety – Prevent open if:
- If ‘Emergency’ button pressed
- Setup option ‘Enabled’ is not active
- No Meteo source present
- No Internet detected
### Roof/shutter Control
- Internal high current H-Bridge for DC motor control
- Manual Open and Close buttons
- Manual Emergency/stop button
- Roof open/close limit switch sensor input
- Roof moviment Timeout, if no position reatched (ex: limit switch fails) in the given time then stop motor
- Roof response Timeout, if no movement (ex: motor stall, jammed rack & pinion, blocked roof, etc) in the given time then stop motor
- Internal PWM motor control with programable _Frequency_, _Start Duty_, _Max Duty_ and _Acceleration_
- Internal relays to control external motor systems (eg: garage motors and similar)
### Power suply & UPS
- Switching 12v power supply
- Integrated UPS for interrupted motor operation
- Integrated battery charger (external battery)
- **Closes the roof securely even in the event of a complete power failure**

> [!IMPORTANT]
> Since this system can also be used in an observatory with several independent piers and mounts, it is no longer practical to park one/all the mounts before moving the roof.
> Therefore, the design of the observatory's sliding roof system must take into account the possibility of moving it regardless of the position of the telescopes, typically mounting the ceiling at a height that does not interfere with any of the installed OTAs, or using lower piers.  
> In Clamshell Domes type observatories the design itself allows the dome to be opened and closed without any concern about the OTA position.

## Next step?
### Plase take a look ate the [Hardware section](https://github.com/almtree/aro-master/tree/main/hardware) and then the [Software/Firmware section](https://github.com/almtree/aro-master/tree/main/firmware)

## License
When I made the decision to share this project I intended to make it public, but recent developments have changed that intention. So, for now I will share the firmware only in its compiled form (without the sources) and the hardware schematics are provided as reference material only. There will be a commercial version of the ***ARO-Master box*** that can be purchased, in addition there is also extra hardware that can be purchased by end users, such as the rack and pinion and motor for roof movement.
.
.
