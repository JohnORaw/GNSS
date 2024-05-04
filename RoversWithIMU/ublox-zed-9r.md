# UBlox ZED 9R

This project uses a Sparkfun Ublox ZED-9R for navigation with heading. The most simple design is one which uses an add-on UART board for RTK and uses ttyS0 for data. It is intended for use with either rtklib\str2str or with the accompanying RTCM3 client.

ProjectRLogger is the first version, this logs data only.

<figure><img src=".gitbook/assets/ProjectP.jpg" alt=""><figcaption></figcaption></figure>

1. Configure fresh RPi 3B+ running Raspbian 64
2. Do the usual post install work.
3. Configure to use the Waveshare Serial Expansion Hat using [https://github.com/JohnORaw/Raspbian/blob/main/Waveshare/SerialExpansionHAT/readme.md](https://github.com/JohnORaw/Raspbian/blob/main/Waveshare/SerialExpansionHAT/readme.md)

