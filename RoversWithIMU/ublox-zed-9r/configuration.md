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

## RTCM

Configure to install and test str2str

```
# Install prereqs
sudo apt install cmake -y
sudo apt install libev-dev -y 
sudo apt install git -y

# Get RTKLIB
git clone https://github.com/tomojitakasu/RTKLIB.git -b rtklib_2.4.3

# Compile str2str
cd RTKLIB/app/consapp/str2str/gcc
make

# Copy str2str up to home directory
cp str2str ~/
cd ~
```
