# Install RTKLIB

One of the starting points is to get a good clean copy of RTKLIB on a Linux server or RPi.

```
sudo apt update
sudo apt upgrade
sudo apt install cmake -y
sudo apt install libev-dev -y
sudo apt install git -y
git clone https://github.com/tomojitakasu/RTKLIB.git -b rtklib_2.4.3
cd RTKLIB/app/consapp/str2str/gcc
make
cp str2str ~/
cd ~

 

```

In more recent times (and for a PC version of RTKLIB, I am using [RTKLIB: demo5 b34k](https://github.com/rtklibexplorer/RTKLIB/releases).&#x20;
