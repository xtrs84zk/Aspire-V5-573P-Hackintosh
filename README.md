# Aspire V5-573P Hackintosh
EFI and resources for doing hackintosh on the Acer Aspire V5-573P-74508G1.

## Instructions
*Copy the EFI folder on your installer USB to boot. <br/>
*Install macOS. (I'm using APFS file system on my SSD) <br/>
*If something fails, refer to [RehabMan's guide](https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/) for laptops.

## Post Installation
*Once installed, copy /Library/Extensions to /Library/Extensions and do... :) <br/>
```bash
sudo kextcache -i /  
```
For keyboard layout (the latin american one) - Using A layout. <br/>
Thanks to neosergio for [this](https://github.com/neosergio/Latam-Keyboard). 
```bash
git clone https://github.com/neosergio/Latam-Keyboard.git && cd Latam-Keyboard && cp -v Latam*.* ~/Library/Keyboard\ Layouts/
```

Download [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/) and configure your serial number, the one on the plist is a scramble of the one I'm using. For iMessage and so, use this guide to configure: [An iDiot's Guide To iMessage](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/) .

## What's working
*USB ports <br/>
*Sleep <br/>
*Integrated Graphics <br/>
*Battery indicator <br/>
*Touchscreen (before Catalina, working fine for 1 finger on Mojave) <br/>
*Full 8gb's of ram <br/>
*Trackpad <br/>
*Keyboard backligth <br/>
*Some fn keys

## What's sometimes working
*Brightness, if the slider dissapears, just wait until next OS update and it will appear again (idk why). <br/>
*HDMI video output (it worked on Mojave, as far as I can remember)


## What's not working
*Power off. (Restart to clover and press the power button) <br/>
*Wifi / Bluetooth (Using bluetooth from an Intel card and Ethernet myself) <br/>
*HDMI audio output. (never tried, I asume it never worked)
*Native audio (have used VoodooHDA in the past, trying to get Apple ALC working but can't seem to be able to figure the correct layout for this ALC 282.)

## Special thanks
[USB Map](https://github.com/corpnewt/USBMap) - corpnewt's tool