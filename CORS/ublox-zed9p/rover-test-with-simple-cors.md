# Simple CORS

Do some background reading on [www.rtk2go.com](http://www.rtk2go.com/) and find the closest NTRIP mount point. This is just a test, so even if its some distance away, this should work.

Our test site is Umricam:2101, located north of Buncrana, Ireland, roughly at 55.166N, 7.435W.

Always take a backup of the Ardusimple configuration before you begin a configuration session.

In U-Centre, select **Tools**, **Receiver Configuration**, set a file name and then click **Transfer GNSS->File**

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

1. Take an Ardusimple GPS and connect it to a conventional PC via USB.
2. Download and run the latest version of U-Center software from U-Blox.
3. Go to Receiver->NTRIP Client and enter in the location of the NTRIP server you are using. If its within 40kms or so, you should get RTK FIXED. If the distance is greater you may not get better than RTK FLOAT.
4. It only takes seconds for me to lock.

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Note that the RTK number crunching is taking place on board the UBlox ZED9P chip. This general approach will also work with commercial CORS services, however, these services tend to cost >€1,000/year.

Using the output data is more of a problem. What if I need the NMEA strings for an instrument, or to log? Well you can log in U-Centre, but we really need a way to get data out. There are 5 interfaces on the underlying chip. I will not discuss SPI or I2C here, that is for another recipe. But we have two UARTs, which allow serial data to be transmitted and recieved. The XBee interface on the Ardusimple board is configured for UART2 by default.

## Warning

Serial standards like RS232, RS422 and RS485 use high voltages, +/- 15VDC. Raspberry Pi and UBlox boards use 3.3VDC. If you connect them, you will fry the board. We can connect RPi to UBlox directly, but that is for another recipe. To get data out of an Ardusimple board, we can use the RS232 interface and then configure UART2 in U-Centre to output NMEA.

\


<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

I can connect this serial port back to an instrument, a logger, or back into the same laptop to use with a different piece of software. There are other ways to do this, but this is a simple and flexible solution.
