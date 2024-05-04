# Services

Once its all tested and working, it needs to be set up as services which start on each boot.

## Setup str2str

I need to pull down the NTRIP stream first.

```
[Unit]
Description=STR2STR Service
After=network.target

[Service]
ExecStart= /home/johnoraw/str2str -in ntrip://john.oraw@iotech.ie:@rtk2go.com/Umricam:2101 -out ntrips://:test@localhost:12101/Azul -out serial://t
tyACM0:115200:8:n:1
Restart=always
User=johnoraw

[Install]
WantedBy=multi-user.target

```

```
sudo cp str2str.service /usr/lib/systemd
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
