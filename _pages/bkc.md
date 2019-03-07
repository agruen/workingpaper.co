---
title: 7 March 2019 Sign Up
subtitle: Join the Geeks Hour to build your own IoT Temperature and Humidity sensor
description: 
featured_image: /images/nodemcu-bkc/3.jpg
---

## Overview
Hi everyone --

I've been playing around with some very simple hardware that makes for exceptionally good home IoT devices at very low prices... and without connection to a surveillance cloud.

It's all trivially easy to do -- but, the documentation online is truly awful, meaning it took me a few weeks to get everything worked out.

So, instead, I'm hosting a geeks hour to show you how to do it easily.

We'll chat about [two](https://homebridge.io/) [different](https://www.home-assistant.io/) automation hubs (both of which can run on a raspberry pi or on another machine in a docker container) and some exceptionally simple/inexpensive wifi remote sensor hardware ([NodeMCU](nodemcu.com) on [ESP8266 microcontrollers](https://www.aliexpress.com/item/Update-Industry-4-0-New-esp8266-NodeMCU-v2-Lua-WIFI-networking-development-kit-board-based-on/32358722888.html?spm=a2g0s.9042311.0.0.49264c4d5tGDeK), with some simple [temperature and humidity sensors](https://www.aliexpress.com/item/High-Precision-AM2302-DHT22-Digital-Temperature-Humidity-Sensor-Module-For-Uno-R3/32292594513.html?spm=2114.search0104.3.38.70de7323dWSi7y&ws_ab_test=searchweb0_0,searchweb201602_2_10065_10068_10130_10890_10547_319_10546_317_10548_10545_10696_453_10084_454_10083_433_10618_431_10307_537_536_10059_10884_10887_100031_321_322_10103,searchweb201603_54,ppcSwitch_0&algo_expid=476abcb2-2728-4905-8d20-b58a1628c653-5&algo_pvid=476abcb2-2728-4905-8d20-b58a1628c653)).

Andrew

## Prerecs
To prepare for the workshop, please download the following items to your local machine:
* [ESP8266 Serial Drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers) from [Silicon Labs](silabs.com) 
* [ESP8266 Firmware](nodemcu-master-15-modules-2019-01-06-01-35-33-float.bin) (I've pre-compiled this for you and am hosting it... but if you want to build your own, it's easy, and you can do so [here](https://nodemcu-build.com), just be sure to include the needed modules including wifi, your sensor type, etc. Again, contact me if you want more info.)
* [ESPlorer](https://esp8266.ru/esplorer/) (requires java)
* [NodeMCU PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher/releases) (Mac and Windows availible, if you're running linux, you can either build it from source or write me and I'll get you going.)
* Software for your NodeMCU device (in this case, [homebridge-mcuiot](https://github.com/NorthernMan54/homebridge-mcuiot/tree/master/nodemcu/lua) -- download all the Lua files, or clone the whole repo)

## Session Instructions

### Preparing your hardware
1. Your kit should come with four parts:
    ![](/images/nodemcu-bkc/1.jpg)
    1. NodeMCU Microcontroller
    2. AM2302 (DHT22) Temperature/Humidity Sensor
    3. Cables with pin adaptors
    4. Micro USB cable
2. Putting software on the Microcontroller (please be sure you've already downloaded everything in the [Prerecs](#prerecs) section above)
    1. First, we'll install the [Silicon Labs drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers) for your system
    2. Next, we'll use the  the [NodeMCU PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher/releases) to load the [firmware](nodemcu-master-15-modules-2019-01-06-01-35-33-float.bin) onto the microcontroller
        - Connect your microcontroler to your laptop with the included USB cable.
        ![](/images/nodemcu-bkc/2.jpg)
        - Open PyFlasher, select the select the correct serial port from the list, and pick the correct connection speed and type.  The ones in the screenshot seem to work well for these devices, but your milage may vary... Be sure to try things if they don't work for you.
        - Select the firmware to load, choose erase flash, and then click the big 'Flash NodeMCU' Button!
        ![](/images/nodemcu-bkc/pyflasher.png)
3. Now that we have NodeMCU on your microcontroller, we need to install the software to read from the sensor and publish the data over HTTP.  For this project, we're using [homebridge-mcuiot](https://github.com/NorthernMan54/homebridge-mcuiot/tree/master/nodemcu/lua).  We'll use the [ESPlorer](https://esp8266.ru/esplorer/) to actually "install" the software on the microcontroller.
    1. After downloading all the files in the `lua` folder, we need to edit a two of them.
    ![](/images/nodemcu-bkc/lua.png)
        - First, we'll add the correct WiFi information to the `passwords_sample.lua` file.  Note the file has blanks for two WiFi networks.  Delete the second one.  After you're finished, rename the file `passwords.lua`.
        ![](/images/nodemcu-bkc/passwords.png)
        - Second, we need to edit the `config.lua` file.  Here we tell the microcontroller which type of sensor we're using (line 4 `DHT`), that we do not want the LEDs running all the time (line 8 `2`), and which pin we will use for data from the sensor (line 17 `5` -- we'll use pin 5, because it's next to the ground and power pins).
        ![](/images/nodemcu-bkc/config.png)
    2. Now, we need to connect to our functioning microcontroller using ESPlorer.  To do so, we open the app, select the correct serial port, enable `DTR` and `RTS` and set the bitrate to `115200`.  Then we click the big `open` button.
    ![](/images/nodemcu-bkc/esplorer-setup.png)
    3. Once connected, we can upload the `homebridge-mcuiot` software.  To do so, we must upload six files individually, by clicking the upload button, finding them on our system, and clicking open for each.  The five files we need to upload are:
        - config.lua
        - led.lua
        - main.lua
        - passwords.lua
        - setup.lua
        - test.lua
    ![](/images/nodemcu-bkc/esplorer-upload.png)
    4. After uploading all the files, we can now test our microcontroller to see if it can connect to WiFi.  We use the ESplorer to run the test by selecting `dofile("")` from the action menu; editing it to add our test tool, so it reads `dofile("test.lua")`, and then clicking the send button.  If the microcontroller panics, it will reboot.  Run the test file again. (This happens with regularity.)
    ![](/images/nodemcu-bkc/esplorer-test.png)
    If the test is successful, ESPlorer will display the connected WiFi network and the device's IP address.
    ![](/images/nodemcu-bkc/esplorer-test-running.png)
4. Next, we'll attach our sensor to the microcontroller.
    1. Close ESplorer and unplug your microcontroller from your laptop.
    2. Attach your pin cables to the `3V3`, `GND`, and `D5` pins.  They're all next to one another.
    ![](/images/nodemcu-bkc/4.jpg)
    3. Using the colors of your pin cables as your guide, make the following connections on your AM2302 sensor module:
        - `3V3` --> `VCC` (middle pin)
        - `GND` --> `GND` (bottom pin)
        - `D5`  --> `DAT` (top pin)
        ![](/images/nodemcu-bkc/5.jpg)
5. Now we can re-connect the microcontroller to your laptop via USB, and see if it is pulling data from the sensor.
    1. After re-connecting, open ESPlorer and open the connection again (it should have saved your settings from before).
    2. Run the test file again, by entering `dofile("test.lua")` into the action menu and clicking send.
    3. If you connected the sensor correctly, ESPlorer will show you the readout from the sensor, as illustrated below.
    ![](/images/nodemcu-bkc/esplorer-sensor-test.png)
6. To access the data remotely, you can visit the IP address shown by ESPlorer in your browser.  It's a simple JSON formatted file, accessible by HTTP.  You can incorporate this into your own application, or use many different home automation tools to read this file.  If you use the Apple ecosystem, you can install the client portion of [homebridge-mcuiot](https://github.com/NorthernMan54/homebridge-mcuiot/) along with [homebridge](https://homebridge.io/).  There is good documentation for this on the sites for both pieces of software.
![](/images/nodemcu-bkc/browser.png)
7. Once you're ready to perminently install your sensor, we need to add one more file to our microcontroller, `init.lua`, which tells it to run the homebridge-mcuiot software on boot.  To do so, click the upload button, find the `init.lua` file downloaded earlier, and click open. 
8. Congrats!  Go plug your controller in somewhere!