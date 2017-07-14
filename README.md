# RPiDiskWiper
RPiDiskWiper turns a raspberry pi into an automated disk wiper

## **DISCLAIMER**

Do not install this on your laptop/desktop unless you know what you're doing. Will it work? Sure but be careful. **As a precaution, the install script will not enable wiping of the devices connected during install time.** So if you have an HDD connected that you intend to wipe, please unplug it before you run the install script or it will be ignored. And lastly, you can't hold me responsible if this tool wipes data you need. Just saying...

---

## Installation

```
git clone https://github.com/iscrow/RPiDiskWiper.git
cd RPiDiskWiper
./install
```

That's it. Optionally edit the script `wiper` to adjust how you'd like to wipe your devices.
It can wipe multiple devices in parallel. Actions are logged in `/tmp/wiper.log` which you can follow with `tail -F /tmp/wiper.log`

RPiDiskWiper also takes control of the onboard RPi LEDs.
The patterns are as follows:
* For devices being wiped you get a blink from both LEDs at the same time. So for 2 devices being wiped we get the pattern: `[Green+Red][Green+Red] [Pause] [Green+Red][Green+Red] [Pause]...`
* For completed devices we get a single green blink each so for one device being wiped and one already completed we get the pattern: `[Green+Red][Green] [Pause] [Green+Red][Green] [Pause]...`
* For two completed devices and none being wiped we get the pattern: `[Green][Green] [Pause] [Green][Green] [Pause]...`

After wipe, the script creates a DOS partition table on the disk with a single partition and formats is at FAT32. You can change the filesystem in `wiper`. It also adds a timestamp file on the newly created filesystem.

If you remove a disk before the wipe is complete the script will flash the error pattern on the LEDs. It will cause no problems on the RPi. You can re-insert the disk and the wipe will start from the beginning. 

To wipe multiple devices, connect them in any order you like. Or start the RPi with them already connected. It doesn't matter. It will find them and wipe them.

## Uninstall

```
cd RPiDiskWiper
./uninstall
```

## Related Projects
I started this project because I could not find anything that did exactly what I wanted. I did look at a few options and I got some ideas for my implementation from the following projects:

* [https://github.com/Real-Time-Kodi/PiBAN](https://github.com/Real-Time-Kodi/PiBAN)
* [https://github.com/craigmayhew/USBCleanser](https://github.com/craigmayhew/USBCleanser)
