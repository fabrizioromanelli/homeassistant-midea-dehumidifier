# Home Assistant Custom Integration for EVA II PRO WiFi Smart Dehumidifier appliance by Midea/Inventor.

[![HitCount](http://hits.dwyl.com/barban_dev/homeassistant_midea_dehumidifier.svg)](http://hits.dwyl.com/barban_dev/homeassistant_midea_dehumidifier)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=5E7ULVFGCGKU2&source=url)


Author: Andrea Barbaresi =2020=

Licence: GPLv3

This repo contains a Home Assistant custom integration for EVA II PRO WiFi Smart Dehumidifier appliance by Midea/Inventor.
This Home Assistant custom component is baded on python library [***midea_inventor_lib***.](https://github.com/barban-dev/midea_inventor_dehumidifier): see library's readme and prerequisites to be able to control your device on Home Assistant.

Info about the dehumidifier appliance can be found [here.](https://www.inventorappliances.com/dehumidifiers/eva-ii-pro-wi-fi-20l)

You can buy the smart dehumidifier appliance (WiFi version) on Amazon (the two links below contain my referral code):
* [Amazon.co.uk](https://www.amazon.co.uk/gp/product/B07665CCSM/ref=as_li_qf_asin_il_tl?ie=UTF8&tag=barban0d-21&creative=6738&linkCode=as2&creativeASIN=B07665CCSM&linkId=a7408b12a09679586e1816acc3c9d74b)
* [Amazon.it](https://www.amazon.it/gp/product/B075486X31/ref=as_li_tl?ie=UTF8&camp=3414&creative=21718&creativeASIN=B075486X31&linkCode=as2&tag=barban03-21&linkId=33e8ff818aaa4b45f0c320e6661773b2)

Home Assistant custom-component
-------------------------------
***[NEW]*** Custom-component for the Home Assistant platform can be found on ``/homeassistant`` folder.
In order to activate the component, follow these steps:

**Step 1: Copy necessary files to your HA's configuration shared folder** 

Copy ***the content of*** ``/homeassistant`` folder (***not the folder itself***), ***including subfolders***, on your HA's configuration shared folder.

Copy ``/midea_inventor_lib`` folder on ``\deps\lib\python3.6\site-packages\`` of your HA's configuration shared folder.

Final result should look similar to this:
```
\\<ha_ip_address>
    └── config
        ├── custom_components
        │   ├── climate
        │   │   └── midea_dehumi.py
        │   ├── midea_dehumi.py
        │   └── sensor
        │       └── midea_dehumi.py
        └── deps
            └── lib
                └── python3.6
                    └── site-packages
                        └── midea_inventor_lib
                            └── libfiles...
```

**Step 2: Activate midea_dehumi platform on your HA's configuration file**

Add the following section in your ``configuration.yaml``
```
midea_dehumi:
  username: user@example.com
  password: passwordExample
```
As usual, you can hide your secret password by means of ``!secret`` notation by specifing it in ``secrets.yaml``

Alternatively, if you prefer, ``sha256password`` parameter can be used instead of the ``password`` one to specify password's sha-256 hash
```
midea_dehumi:
  username: user@example.com
  sha256password: cf76d55503cdee3....
```
**Step 3: Activate DEBUG-level logging (optional)**

It is highly suggested to activate DEBUG-level logging for the three components the midea_dehumi platform consists of. This let you perform troubleshooting analysis if the component doesn't work as expected.
```
logger:
  default: info
  logs:
    custom_components.midea_dehumi: debug
    custom_components.climate.midea_dehumi: debug
    custom_components.sensor.midea_dehumi: debug
```
** Step 4: Restart HA**

You can restart HA by using one of your preferred method (e.g. using restart button on Settings>General>Server Management og HA's Web dashboard).

If everything is ok, you will find the following two new entities in your HA dashboard:

* **climate.midea_dehumi_*[Device_ID]***
* **sensor.midea_dehumi_*[Device_ID]*_humidity**

By means of the climate entity, you can control your appliance whereas the sensor reports the detected current humidity of your environment.

If you cannot find the entities reported above, check the logs generated by HA to track the issue.

Donations
---------
If this project helps you to reduce time to develop your code, you can make me a donation.

[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=5E7ULVFGCGKU2&source=url)


