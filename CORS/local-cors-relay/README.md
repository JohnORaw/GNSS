---
description: For when you have more than one rover in Wi-Fi range
---

# Local CORS relay

Working with the survey boat AZUL, I needed RTCM3 to multiple GNSS from RTK2GO. There is no need for multiple streams to the Internet and RTK2GO can get very upset with bad client behavior. I used a single Pi Zero to take the NTRIP stream and then made it available via a local caster. All working as of 24FEB24.

## Setup str2str

Configured the RPi as&#x20;

```
sudo apt upgrade

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

The command line to test **str2str** is

```
 ./str2str -in ntrip://john.oraw@iotech.ie:@rtk2go.com/Umricam:2101 -out serial://ttyACM0:115200:8:n:1
```

This takes a feed from rtk2go and forwards it to USB. I have a UBX F9P sitting on ttyACM0 to verify.

## Adding a caster

I'm adding a simple Linux open source caster so anything can consume the NTRIP stream. For diagnostics, I can use my laptop to test I'm getting that stream.

```
# Install the NTRIP caster
git clone https://github.com/tisyang/ntripcaster.git
cd ntripcaster
git submodule update --init

# Compile ntripcaster
cmake CMakeLists.txt
make
cd
 
# Copy up to home directory, renaming
cp ./ntripcaster/ntripcaster ./myntripcaster
```

We need a **ntripcaster.json** file. Note the non-standard port 12101.

```
{
        "listen_addr":"0.0.0.0",
        "listen_port": 12101,
        "max_client": 0,
        "max_source": 0,
        "max_pending": 10,
        "tokens_client": {
                "test:test": "*"
        },
        "tokens_source": {
                "test": "*"
        }
}
```

## Laptop Test

I open one SSH windows and run **ntripcaster** to test.

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

Then I open a second SSH window to use str2str as a source for the caster.

<figure><img src="../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

And I can see this data being forwarded to the caster.

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Finally I set up STRSVR on my laptop to also consume this stream.

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

And verify it is subscribing to the caster and receiving data.

<figure><img src="../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

And a final cross check at the caster...

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

This shows the source of my as localhost (127.0.0.1).

It shows my laptop as a client (192.168.1.1).

## RPi Test

The test string for a local RPi to consume the local CORS is

```
./str2str -in ntrip://test:test@192.168.14.100:12101/Azul
```

A working string as used on the Azul test boat is

```
./str2str -in ntrip://test:test@192.168.14.100:12101/Azul -out serial://ttySC0:19200:8:n:1
```

