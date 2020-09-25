# Aspire V5-573P Hackintosh
## OpenCore branch (WIP)

EFI and resources for doing hackintosh on the Acer Aspire V5-573P-74508G1. This branch is based on the work by Dortania on the [OpenCore Laptop Vanilla Guide](https://dortania.github.io/vanilla-laptop-guide/)

![Screenshot](./assets/screenshot.png)

## Status

- It boots! **EVEN BIG SUR**, installer and all. SIP enabled.

- Using OpenCore 6.2 33c1bed

  ![Bootloader](./assets/bootloader.png)


## Instructions

1. Format an USB with at least 16gb. USB 2.0 is easier than 3.0. Format it as hfs+ on a GPT map.

2. Get the installer .app from Apple and run as said in [this page](https://support.apple.com/en-us/HT201372).

   ```bash
   sudo /Applications/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
   ```

3. Copy the EFI folder on your installer USB to boot. (Must have a GUID partition table, copy the folder to the 200mb FAT32 one) <br/>

   ```bash
   # Run MountEFI to mount the EFI partition on the USB.
   git clone https://github.com/corpnewt/MountEFI && cd MountEFI && chmod +x MountEFI.command && ./MountEFI.command
   ```

   

4. Boot the installer and install macOS. <br/>

5. Use [MountEFI](https://github.com/corpnewt/MountEFI) to mount the ESP on the internal disk of your system and copy the EFI contents to it.<br/>

   ```bash
   # Cloning MountEFI to the new system and using it to mount internal EFI
   git clone https://github.com/corpnewt/MountEFI && chmod +x /MountEFI/MountEFI.command && sudo python3 MountEFI/MountEFI.command disk0 && open /Volumes/EFI/
   ```

   

6. Feel free to reach out if you need any help or found how to fix something. [Telegram](https://t.me/xtrs84zk) | [Twitter](https://twitter.com/xtrs84zk) 

## Post Installation
1. For keyboard layout (the latin american one) - Using B layout. 

```bash
git clone https://github.com/neosergio/Latam-Keyboard.git && cd Latam-Keyboard && cp -v Latam*.* ~/Library/Keyboard\ Layouts/
```

Then set it on System Preferences.

![Keyboard settings](./assets/keyboard.png)

2. ~~Use xzhih's [script](https://github.com/xzhih/one-key-hidpi) to enable hidpi.~~ For Big Sur, use [this fork](https://github.com/mlch911/one-key-hidpi) that does not need access to / nor disabled SIP.

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/mlch911/one-key-hidpi/master/hidpi.sh)"
```

   ![hidpi](./assets/hidpi.png)

3. Configure your serial number, uuid, and other identifiers. The ones on the plist are a scramble of the ones I'm using. As for how to configure it, the correct way is described in [this section](https://dortania.github.io/OpenCore-Desktop-Guide/post-install/iservices) of the guide.

3. Reboot a couple of times to let it sit.


## Some fixes

Error 500 on AppStore:

Log out of the AppStore and run this command in terminal.

```bash
defaults write com.apple.appstore.commerce Storefront -string \
    "$(defaults read com.apple.appstore.commerce Storefront | sed s/,8/,13/)"
```

## What's working
* USB ports <br/>
* Integrated Graphics <br/>
* Trackpad (With gestures) <br/>
* Wifi as emulated card. Works well most of the time.<br/>
* Bluetooth.
* Keyboard backligth. Fn3, Fn5, Fn6, Fn7, Fn9, Fn8 as expected. <br/>
* Brightness control. <br/>
* Audio. <br/>
* HDMI video output. <br/>
* Siri. <br/>
* Microphone.
* Battery indicator. <br/>
* HDMI audio output. (Thanks AppleALC) ✨

## What's sometimes working
* Some Fn keys migth have diferent behavior. (Fn + F12 lowers brightness and 'Pausa' increments it)
* Camera is DIM, works on well lit rooms.
* Sleep (OpenCore's sleep is way harder.) Well, it sleeps. Just KP's it's way back.<br/>
* Power off. (Restart to OpenCore and press the power button) <br/>

## What's not working
* Touchscreen (Big Sur doesn't like VoodooI2C), go back to [ad85ba](https://github.com/xtrs84zk/Aspire-V5-573P-Hackintosh/commit/ad85baa75662148a61e47ba679cee969b94cf8c0) for the last Catalina with touchscreen. <br/>



## Contributing

New fixes are always welcome. Just issue or send a pull request. Don't forget to scramble the serial number and so before the push. 

## Special thanks
* [Acidanthera](https://github.com/acidanthera/VoodooPS2) - For the macOS like trackpad experience, OpenCore and most of the kexts used.
* [USB Map](https://github.com/corpnewt/USBMap) - corpnewt's tool <br/>
* [Fewtarius's](https://fewtarius.gitbook.io/laptopguide/) - For the vanilla laptop guide. <br/>
* [VoodooHDA](https://github.com/chris1111/VoodooHDA-2.9.2-Clover-V14) - Yeah, we hate it, we love it. <br/>
* [xzhih](https://github.com/xzhih) - For the method to enable HiDPI. <br/>
* [Hackintool](https://www.tonymacx86.com/threads/release-hackintool-v2-8-6.254559/) - For making it easier on newer releases. <br/>
* [trs96](https://www.tonymacx86.com/threads/appstore-the-operation-couldnt-be-completed-com-apple-commerce-client-error-500.270957/post-1912788) -  For the solution to error 500 on AppStore. <br/>
* [neosergio](https://github.com/neosergio) - For the keyboard layout.
