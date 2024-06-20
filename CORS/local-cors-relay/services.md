# Services

Once its all tested and working, it needs to be set up as services which start on each boot.

## Setup str2str

I need to pull down the NTRIP stream first.

```
[Unit]
Description=STR2STR Service
After=network.target

[Service]
ExecStart= /home/johnoraw/str2str -in ntrip://john.oraw@iotech.ie:@rtk2go.com/Umricam:2101 -out ntrips://:test@localhost:12101/Azul -out serial://ttyACM0:115200:8:n:1
Restart=always
User=johnoraw

[Install]
WantedBy=multi-user.target

```

```
# Raspberry Pi
sudo cp str2str.service /usr/lib/systemd
# UB2204
sudo cp str2str.service /etc/systemd/system

# All
sudo systemctl status str2str
sudo systemctl enable str2str.service
sudo systemctl status str2str
```

## Setup the caster

I create a directory called services and then create **myntripcaster.service**

```
[Unit]
Description=NTRIP Caster
After=network.target

[Service]
ExecStart= /home/johnoraw/myntripcaster /home/johnoraw/ntripcaster.json
Restart=always
User=johnoraw

[Install]
WantedBy=multi-user.target

```

To put this operational

```
sudo cp myntripcaster.service /usr/lib/systemd
sudo systemctl enable myntripcaster.service
sudo systemctl status myntripcaster
```

## Setup a Client

Anything which will consume from the caster also needs a service. The config below is from Azul, ProjectP (Position and Sonar).

```
[Unit]
Description=STR2STR Service
After=network.target

[Service]
ExecStart= /home/johnoraw/str2str -in ntrip://test:test@192.168.14.100:12101/Azul -out serial://ttySC0:19200:8:n:1
Restart=always
User=johnoraw

[Install]
WantedBy=multi-user.target
```

```
sudo cp str2str_client.service /usr/lib/systemd
sudo systemctl enable str2str_client.service
sudo systemctl status str2str_client
```
