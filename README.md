# Aspire V5-573P Hackintosh
EFI and resources for doing hackintosh on the Acer Aspire V5-573P-74508G1.

![Screenshot](screenshot.png)
## Instructions
Copy the EFI folder on your installer USB to boot. <br/>
Install macOS. (I'm using APFS file system on my SSD) <br/>
If something fails, refer to [RehabMan's guide](https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/) for laptops. <br/>Feel free to reach out if you need any help or found how to fix something.<br/>
[Telegram](https://t.me/xtrs84zk) | [Twitter](https://twitter.com/xtrs84zk) 

## Post Installation
Once installed, copy /Library/Extensions to /Library/Extensions and repair permisions. Read [this guide](https://www.tonymacx86.com/threads/guide-installing-3rd-party-kexts-el-capitan-sierra-high-sierra-mojave-catalina.268964/) for instructions on how to install correctly the kernels. [Hackintool](https://www.tonymacx86.com/threads/release-hackintool-v2-8-6.254559/) is a great tool to do this job. 
```bash
git clone https://github.com/xtrs84zk/Aspire-V5-573P-Hackintosh.git &&
cd Aspire-V5-573P-Hackintosh &&
cd Library/Extensions 
cp * /Library/Extensions
sudo kextcache -i /  
```
For keyboard layout (the latin american one) - Using A layout. <br/>
Thanks to neosergio for [this](https://github.com/neosergio/Latam-Keyboard). 
```bash
git clone https://github.com/neosergio/Latam-Keyboard.git && cd Latam-Keyboard && cp -v Latam*.* ~/Library/Keyboard\ Layouts/
```

Download [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/) and configure your serial number, the one on the plist is a scramble of the one I'm using. As for how to configure it, the correct way is described here: [An iDiot's Guide To iMessage](https://www.tonymacx86.com/threads/an-idiots-guide-to-imessage.196827/) .

## What's working
USB ports <br/>
Sleep <br/>
Integrated Graphics <br/>
Battery indicator <br/>
Full 8gb's of ram <br/>
Trackpad <br/>
Keyboard backligth <br/>Fn5, Fn6, Fn7, Fn9, Fn8 as expected. <br/>
Some Fn keys migth have diferent behavior.

## What's sometimes working
Touchscreen (before Catalina, working fine for 1 finger on Mojave) <br/>
Audio with VoodooHDA. (Still trying to get Apple ALC to work on ALC 282) <br/>
Brightness, if the slider dissapears, just wait until next OS update and it will appear again (idk why). <br/>
HDMI video output (it worked on Mojave, as far as I can remember) <br/>
It migth freeze the next couple of reboots after a System Update, that's why it's advised to always do a clean install rather than upgrade. Don't worry, it'll go back to normal after that. 

## What's not working
Power off. (Restart to clover and press the power button) <br/>
Wifi / Bluetooth (Using bluetooth from an Intel card and Ethernet myself) <br/>
HDMI audio output. (never tried, I asume it never worked)

## Contributing

New fixes are always welcome. Just issue or send a pull request. Don't forget to scramble the serial number and so before the push. 

## Special thanks
[USB Map](https://github.com/corpnewt/USBMap) - corpnewt's tool <br/>
[VoodooHDA](https://github.com/chris1111/VoodooHDA-2.9.2-Clover-V14) - Yeah, we hate it, we love it. <br/>
[Hackintool](https://www.tonymacx86.com/threads/release-hackintool-v2-8-6.254559/) - For making it easier on newer releases.