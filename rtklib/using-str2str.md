# Using str2str

This is **autoexec.sh**

```
#!/bin/bash
# by: JOR
# Date: 14MAY21
# Function: autoexec for Linux
# Leave this script in /home/pi
# Script: autoexec.sh

HOMEPATH="/home/pi"

# Configure hardware serial port
stty -F /dev/ttyS0 clocal raw speed 115200

# Get RTCM3 from RTK2GO and send to Ardusimple on S0
$HOMEPATH/rtklib/str2str/str2str -in ntripcli://:@rtk2go.com/Umricam -out serial://ttyS0:115200:8:n:1
```

This is example code for RPi Zero, acting an an NTRIP client to RTK2GO and forwarding RTCM3 to the serial port.

Be warned, the GPIO serial is 3v3 only, you can connect this to a PRi or an Ardusimple, but its not RS232 levels.

This connects to UART1 on a Ardusimple configured as a Rover.
