<p align="center"><img src="https://i.ibb.co/qm9m4Pt/Wireless.png" width="200"></a>
<h1 align="center"><b>How to set up and use ADB Wirelessly</b></h1>
<br />

## NFO:
The standard ADB Configuration involves a USB Connection to a physical Device.
If you prefer, you can switch over to TCP/IP Mode and connect ADB via WiFi instead.

# Requirements:
* USB Driver for your Device or Universal ADB Driver
* [Platform-Tools](https://developer.android.com/studio/releases/platform-tools) or [ADB & Fastboot++](https://github.com/K3V1991/ADB-and-FastbootPlusPlus)
* [Termux](https://play.google.com/store/apps/details?id=com.termux) or [Terminal Emulator for Android](https://play.google.com/store/apps/details?id=jackpal.androidterm)

## If you don't know your Device's IP you can:
<details>
  <summary>Click to expand</summary>
* Check the IP in the WiFi Settings of your Device
* Use ADB to discover IP (via USB):
1. Connect the device to the computer via USB
2. In a Command Line, type: 
```adb shell ifconfig``` 
and copy your Device's IP Address
</details>

## Non-rooted Device:
**Note: Make sure your Device and your Computer are on the same Network**

1. Connect the Device to the Host Computer with a USB Cable
2. Type the following Command to listen for a TCP/IP Connection on a Port (default 5555):
```
adb tcpip <port>
```
Switches to TCP/IP Mode

3. Disconnect the USB Cable from the Device
4. Type: adb connect ```<ip address>:<port>```

## Example:
```
adb tcpip 5555
```
```
adb connect 192.168.0.101:5555
```

## Revert back to USB Debugging use the following Command:
```
adb usb
```
<br />

## Rooted Device:
**Note: When you have a rooted Device but don't have Access to a USB Cable**

Open a Terminal App on the Device and type:
```
su
```
```
setprop service.adb.tcp.port <tcp port number>
```
```
start adbd
```

## Example:
```
setprop service.adb.tcp.port 5555
```
In a Command Line on the Computer, type:
```
adb connect 192.168.1.2:5555
```

## Turn it off:
```
setprop service.adb.tcp.port -1
```
```
stop adbd
```
