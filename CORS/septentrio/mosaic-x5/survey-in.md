# Survey In

Do this work immediately after install and before doing anything else! Your CORS needs to know exactly where its antenna is.

All post-processing has been carried out using [RTKLIB: demo5 b34k](https://github.com/rtklibexplorer/RTKLIB/releases). Earlier versions did not understand the Septentrio binary format.

Create a top level directory with the date to keep your workflow. Mine is **Mosaic 18AUG24**.

## Logging

In RxControl, go to Logging->RxControl Logging. I set the location under Global and logged for 24 hours.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

## RINEX data

Download RINEX data suitable for your location. I use the [OSI service](https://gnss.osi.ie/download-rinex.php) and the site FOYLE and MALIN.&#x20;

Instructions for doing this in NI to be added (DL).

I create separate directories for FOYLE and MALIN and moved the files for these sites to these directories.
