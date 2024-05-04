---
description: Add a heading sensor
---

# Heading

For effective INS, we need a heading sensor. This functionality is built into the UBlox-F9P. You can buy the kit pre-configured from Ardusimple, or construct from two SimpleRTK2B kits.

In most applications, the moving base is the main boat GNSS. It receives corrections from a CORS station and is cm accurate. It is configured to send RTCM data to a Rover, so the Rover can figure out where it is with respect to the moving base.

1. Designate one kit as Moving Base and one as Rover.
2. Download the 1Hz setup files from Ardusimple and flash the two units.
3. Connect TX1 on the Moving Base to RX2 on the Rover (the red wire!).

[![](https://github.com/IOTECH-Donegal/RTK/raw/main/Recipe4/MovingBase.jpg)](https://github.com/IOTECH-Donegal/RTK/blob/main/Recipe4/MovingBase.jpg)

4. Ensure you have an RTK Fix position on the base, you can use recipe 1 for test purposes.
5. On the Rover, use U-Centre to read UBX-NAV-RELPOSNED. This should show heading, distance and accuracy.

This is a sloppy test, in reality, GND and IOREF should also be connected.

Next projects to further develop this are:

* Hook the Rover to a RPi and decode UBX-NAV-RELPOSNED to output NMEA0183 sentences, HDG/HDM/HDT.
* Make a second connection from the Moving Base to another Rover. Now you can calculate heading, pith, roll, yaw, etc.

A full diagram of a working system is shown below.

[![](https://github.com/IOTECH-Donegal/RTK/raw/main/Recipe4/RPi.jpg)](https://github.com/IOTECH-Donegal/RTK/blob/main/Recipe4/RPi.jpg)

The topmost RPi (RTKRover2) takes an NTRIP feed from Wi-Fi (rtk2go.com) and uses str2str to feed it through a serial port (/dev/ttyS0) to the Moving Base. Take a look at the accompanying **autoexec.sh** file. For more detail, review Recipe 5. I'm using a Pi Zero with a serial card, so I have a TX/RX light and I can see when this is working.

The Moving Base is using the generic configuration from Ardusimple, but is has RTK accuracy due to the RTCM feed from RTKRover2. We need to use UART2 for RTCM from Moving Base to UART2 on the Heading Sensor.

This is bizarre, but on the Ardusimple boards:

* TX2 conects to UART2 RX
* RX2 conects to UART2 TX

I know the wiring looks backwards, but check [https://www.ardusimple.com/simplertk2b-hookup-guide/](https://www.ardusimple.com/simplertk2b-hookup-guide/)

Connect RX2 on the Moving Base (which transmits!) to TX2 on the Heading Sensor (which receives!).

Helpfully, as they are connected:

* The GNSS->XBEE light on the Moving Base shows activity.
* The XBEE->GNSS light on the Heading Sensor shows synchronised activity.

I can use U-Centre to verify a good heading reading. The heading reading is only available in UBX protocol, this is fed to another RPi (Heading2) for parsing and translation. A [UBX parser](https://github.com/IOTECH-Donegal/HeadingSensor) has been written and tested as a heading sensor.

A working evaluation assembly is shown below.

[![](https://github.com/IOTECH-Donegal/RTK/raw/main/Recipe4/Assembly.jpg)](https://github.com/IOTECH-Donegal/RTK/blob/main/Recipe4/Assembly.jpg)
