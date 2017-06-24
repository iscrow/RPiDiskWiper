# RPiDiskWiper
RPiDiskWiper turns a raspberry pi into an automated disk wiper

## *DISCLAIMER*
*Do not install this on your laptop/desktop unless you know what you're doing. Will it work? Sure! And if your root disk shows up as /dev/sd\* it will get wiped without questions. Just saying...*
---
## Installation

```
https://github.com/iscrow/RPiDiskWiper.git
cd RPiDiskWiper
./install
```

That's it. Optionally edit the script `wiper` to adjust how you'd like to wipe your devices.
It can wipe multiple devices in parallel. Actions are logged in `/tmp/wiper.log` which you can follow with `tail -F /tmp/wiper.log`

RPiDiskWiper also takes control of the onboard RPi LEDs.
The patterns are as follows:
* Wiping: both LEDs in sync show a heartbeat pattern: `.._.._.._`
* Done: Normal LED function. Green show sdcard access and RED one is solid on
* Error: Green is off and Red flashed on and off `._._._`

After wipe, the script creates a DOS partition table on the disk with a single partition and formats is at FAT32. You can change the filesystem in `wiper`. It also adds a timestamp file on the newly created filesystem.

If you remove a disk before the wipe is complete the script will flash the error pattern on the LEDs. It will cause no problems on the RPi. You can re-insert the disk and the wipe will start from the beginning. 

To wipe multiple devices, connect them in any order you like. Or start the RPi with them already connected. It doesn't matter. It will find them and wipe them.

