---
description: Use a local base & connect to rover using XBee
---

# Local Base

The Ardusimple web site is very good, read the notes there before you begin.

1. Clearly mark one of the units as Base and the other as Rover. If you have purchased them as a kit, they are already marked.
2. Check the units have the latest firmware release, 1.13 at time of writing. Check **UBX-MON-VER**.
3. Assemble the units with the XBee radio, antenna etc. connected.
4. From the Ardusimple website, download the basic configuration files for

* Base
* Rover 1Hz

5. Upload the configuration to the units using U-Centre.

* Go to **Tools->Receiver Configuration**
* Select the correct configuration file and transfer **Transfer File -> GNSS**

6. Go to **UBX-CFG-CFG** and **Save Current Configuration**.
7. Restart the units.

* On the Rover you should see XBee -> GPS light
* On the Base, you should see GPS -> XBee light

8. Site the antenna with a good view of the sky, I need 270 degrees clear to get a good RTK solution.
9. On the base:

* Check **UBX-CFG-TMODE3**, you should see the parameters for Survey-In. The default value is 2.5m and 60 seconds.
* Check **UBX-NAV-SVIN**, this will show when Survey-In is complete.
* You do not need to connect U-Centre to the base after Survey-In is complete.

10. On the rover:

* At start-up, the Rover will go from **No Fix**, to **2D**, **3D/DGNSS**, **Float** and finally **Fixed**.
* Check the 3D and 2D accuracy values, they should be 2cm and 1cm respectively.

[![](https://github.com/IOTECH-Donegal/RTK/raw/main/Recipe2/Fixed.jpg)](https://github.com/IOTECH-Donegal/RTK/blob/main/Recipe2/Fixed.jpg)

My PDOP and HDOP figures are bad, I only have 270 degree view, trees up to c. 30 degrees. I am using a base which has performed a Survey-In and that has limitations. The maximum accuracy of the unit is c. 1m, my base will have this accuracy only. The rover will be accurate to within 2cm/1cm, but only with respect to the base. This is perfect for some applications, but for absolute accuracy, the base requires a precise position, see Recipe 3.
