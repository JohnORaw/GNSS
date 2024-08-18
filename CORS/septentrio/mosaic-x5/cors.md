# CORS

Do some background reading on [www.rtk2go.com](http://www.rtk2go.com/) and find the closest NTRIP mount point. This is just a test, so even if its some distance away, this should work.

Our test site is Umricam:2101, located north of Buncrana, Ireland, roughly at 55.166N, 7.435W.

1. Create an account with RTK2GO and [register](http://rtk2go.com/sample-page/new-reservation/) your base station with a unique name and password.
2. Under Corrections->NTRIP, configure a new NTRIP correction. Under Configure Output, set to RTCMv3.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

3. If this is working, check [here](http://rtk2go.com:2101/). If I scroll down, I can see my site.

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
