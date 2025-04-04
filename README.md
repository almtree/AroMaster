![image](https://github.com/user-attachments/assets/f11f5d3a-4bc3-4ead-ba16-23fee96c62ab)
# Automated Roll-Off-Roof Observatory Control &amp; Guard

***ARO-Master*** implements an affordable and integrated control system for ***Automated Remote/Robotic Observatories*** with **Roll-Off-Roof** design.

In addition to sliding roof movement management and pier management, one of the essential requirements was the need to close the roof even when the power supply fails, for this purpose an integrated switching power supply (SMPS) + uninterruptible power supply (UPS) + battery management system (BMS) system was used, along with a simple 12V external battery (Gel, AGM, Acid), which allows security for remote operation.

Main components are:
### ***ARO-Master*** control box
Hardware & firmware that implement the server/daemon for Observatory control (remote and local). This is the main brains that allows you to connect and control all the equipment, open/close the roof, see weather conditions, see the sky, see the observatory interior, control user login, control the Piers etc.
### ***Pier-Relays*** box <sup>optional</sup>
Relays box for each pier that connected to ARO-Master, allows you to turn on and off the equipment (mount, PC, power box, etc.) 

## License
When I made the decision to share this project I intended to make it public, but recent developments have changed that intention. So, for now I will share the firmware only in its compiled form (without the sources) and the hardware schematics are provided as reference material only.
There will be a commercial version that can be purchased as a kit or already assembled, in addition to the two electronic components mentioned (***ARO-Master box*** & ***Pier-Relays box***) there is also extra hardware that can be purchased by end users, such as the rack and pinion and motor for roof movement.

## Overview
I started this project in 2015 and to date it has undergone several developments in terms of hardware and software. The first version was developed around an STM32-E407 microcontroller but this quickly proved to be insufficient for everything I wanted to implement, both in terms of hardware and firmware features.
The current version uses a **Raspberry PI 4** with at least 2GB of memory for the ***ARO-Master box*** and uses **RP2040/RP2350** microcontrollers for the ***Pier-Relay box*** .

This system is in use in my personal observatories and those of some colleagues, two of which are located in Tunisia and are remotely controlled from Europe.

### Internal firmware Web Server for magement and system setup
- No software instalation needed
- Accessible from anywhere
- OS independent using Windows, Linux, Android or Mac browser
- Auto firmware updates
- Provides a Wi-Fi hotspot
- No need for extra Wifi router for connecting you Wifi devices (IP camera, Smart Plugs, etc) to the Internet 
- Direct integration with _uAstro SkyPatroll_ (MSP) or _uAstro Weather Station_ (MWS)
### Alpaca Daemon for Multiclient and MultDevice
- Alpaca Discovery aware (no setup or configuration needed)
- Implements Alpaca devices Dome, Switch (one for each pier), ObservingConditions and  SafetyMonitor
- No need to install ASCOM drivers
- Devices can be accessed simultaneously from different computers
- OS agnostic, works with Windows, Linux, Android, Mac OS, etc
### Faults monitoring
- Mains voltage
- Battery voltage
- Motor current
- Weather
- External alarm
- Logged users
- Internet not available
- Temperature, humidity and dew point
- System CPU temperature 
### Other functionalities
- Watchdog reboots system on hardware/software fails
- Sends Email on Fault or roof open/close
- _ARO-Master box_ internal cool fan and heater control
- Up Time, number of minutes since the controller was initialized
### Users/Piers control
- Up to 8 piers  (one user per ‘pier’)
- Internet control of pier relays (4 relays per pier, 110/220v 10A per relay)
- No need for third-party ‘smart Wifi plugs’
- Relay reset with timed rearm
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
- No Users logged in
- No Internet detected
### Roof/shutter Control
- Internal high current H-Bridge for DC motor control
- Manual Open and Close buttons
- Manual Emergency/stop button
- Roof open/close limit switch sensor input
- Roof moviment Timeout, if no position reatched (ex: limit switch fails) in the given time then stop motor
- Roof response Timeout, if no movement (ex: motor stall, jammed rack & pinion, blocked roof, etc) in the given time then stop motor
- Internal PWM motor control with programable _Frequency_, _Start Duty_, _Max Duty_ and _Acceleration_
- External (third-party) motor control using relay signals
### Power suply & UPS
- Switching 12v power supply with 350W
- Integrated UPS for interrupted motor operation
- Integrated battery charger (external battery)
- **Closes the roof securely even in the event of a complete power failure**

# Considerations on telescopes and observatory design
> [!IMPORTANT]
> Since this system can also be used in an observatory with several independent piers and mounts, it is no longer practical to park one/all the mounts before moving the roof.
> Therefore, the design of the observatory's sliding roof system must take into account the possibility of moving it regardless of the position of the telescopes, typically mounting the ceiling at a height that does not interfere with any of the installed OTAs, or using lower piers.
>  


