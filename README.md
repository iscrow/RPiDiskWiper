# RPiDiskWiper
RPiDiskWiper turns a raspberry pi into an automated disk wiper

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
* Wiping: both LEDs in sync show a heartbeat pattern: .._.._.._
* Done: Normal LED function. Green show sdcard access and RED one is solid on
* Error: Green is off and Red flashed on and off ._._._
