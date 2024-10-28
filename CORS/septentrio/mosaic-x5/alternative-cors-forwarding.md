---
description: The Janky Method
---

# Alternative CORS forwarding

Some earlier models of Mosaic didn't have working Ethernet. When a host connects to USB1, it detects two serial ports. One is used as a forwarder to 192.168.3.1 to allow for local configuration of the device. If using a RPi, this port can be forwarded via SSH to a remote computer.

The second serial port is addressed by the mosaic as USB2 and can be configured to ingress/egress RTCM or NMEA. A RPi can then be used with STR2STR as a forwarder. &#x20;
