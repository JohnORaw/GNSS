# Configuration

1. Configure fresh RPi 3B+ running Raspbian 64
2. Do the usual post install work.
3. Configure to use the Waveshare Serial Expansion Hat using [https://github.com/JohnORaw/Raspbian/blob/main/Waveshare/SerialExpansionHAT/readme.md](https://github.com/JohnORaw/Raspbian/blob/main/Waveshare/SerialExpansionHAT/readme.md)

## GNSS

Clone the GNSS repo

```
cd ~
git clone git@github.com:JohnORaw/ProjectP.git
```

Test using

```
cd ProjectP
/NMEALogger.py
```

