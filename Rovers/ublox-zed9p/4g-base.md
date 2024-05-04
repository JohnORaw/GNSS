---
description: Getting RTCM to rovers via the Internet
---

# 4G Base

For a practical system on a boat or for field survey, recipe 1 is none too practical. A better design would be for a self-contained system in an IP68 sealed enclosure, using minimum power, with minimum components. A single GNSS board will do, but we need a way to get RTCM correction into it. Depending on the requirements, there are X-Bee modules for Bluetooth, Wi-Fi/NTRIP Cleint, 4G etc.

Assuming there is Wi-Fi available on the boat, the cheapest and most flexible option is to use a PI Zero. Two options have been considered to pull an NTRIP stream down from a remote CORS.

1. STR2STR from RTKLIB
2. A dedicated python script to do the same.

The advantage of the python script is that we can add functionality and see what is happening under the hood. We can add a basic display, so status is available in real-time to the surveyor. The production system will use a 1.3" LCD, but could use E-Paper if a refresh rate of 5 seconds can be achieved. I think the production system will also use USB.

The accompanying file str2str.sh is a Linux script to configure the hardware port, in this prototype I'm using an I2C/SPI serial HAT with two serial ports, the first port is ttySC0. Check here for the [hardware descriptions.](https://github.com/IOTECH-Donegal/Raspbian)

To do this with python, there is a [dedicated NTRIP repo.](https://github.com/IOTECH-Donegal/NTRIP/tree/main/readme.md)
