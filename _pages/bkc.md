---
title: 7 March 2019 Sign Up
subtitle: Join the Geeks Hour to build your own IoT Temperature and Humidity sensor
description: 
featured_image: /images/blog/esp8266-bme280.jpg
---

## Overview
Hi everyone --

I've been playing around with some very simple hardware that makes for exceptionally good home IoT devices at very low prices... and without connection to a surveillance cloud.

It's all trivially easy to do -- but, the documentation online is truly awful, meaning it took me a few weeks to get everything worked out.

So, instead, I'm hosting a geeks hour to show you how to do it easily.

We'll chat about [two](https://homebridge.io/) [different](https://www.home-assistant.io/) automation hubs (both of which can run on a raspberry pi or on another machine in a docker container) and some exceptionally simple/inexpensive wifi remote sensor hardware ([NodeMCU]() on [ESP8266 microcontrollers](https://www.aliexpress.com/item/Update-Industry-4-0-New-esp8266-NodeMCU-v2-Lua-WIFI-networking-development-kit-board-based-on/32358722888.html?spm=a2g0s.9042311.0.0.49264c4d5tGDeK), with some simple [temperature and humidity sensors](https://www.aliexpress.com/item/High-Precision-AM2302-DHT22-Digital-Temperature-Humidity-Sensor-Module-For-Uno-R3/32292594513.html?spm=2114.search0104.3.38.70de7323dWSi7y&ws_ab_test=searchweb0_0,searchweb201602_2_10065_10068_10130_10890_10547_319_10546_317_10548_10545_10696_453_10084_454_10083_433_10618_431_10307_537_536_10059_10884_10887_100031_321_322_10103,searchweb201603_54,ppcSwitch_0&algo_expid=476abcb2-2728-4905-8d20-b58a1628c653-5&algo_pvid=476abcb2-2728-4905-8d20-b58a1628c653)).

If you'd like to join, please [register](#sign-up) register below.  I have 20 sets of senors and microcontrollers, so if we get fewer than 20 sign ups, everyone can take home their own!

Andrew

## Prerecs
To prepare for the workshop, please download the following items to your local machine:
* [ESP8266 Serial Drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers) from [Silicon Labs](silabs.com) 
* [ESP8266 Firmware](nodemcu-master-15-modules-2019-01-06-01-35-33-float.bin) (I've pre-compiled this for you and am hosting it... but if you want to build your own, it's easy, and you can do so [here](https://nodemcu-build.com), just be sure to include the needed modules including wifi, your sensor type, etc. Again, contact me if you want more info.)
* [ESPlorer](https://esp8266.ru/esplorer/) (requires java)
* [NodeMCU PyFlasher](https://github.com/marcelstoer/nodemcu-pyflasher/releases) (Mac and Windows availible, if you're running linux, you can either build it from source or write me and I'll get you going.)
* Software for your NodeMCU device (in this case, [homebridge-mcuiot](https://github.com/NorthernMan54/homebridge-mcuiot/tree/master/nodemcu/lua) -- download all the Lua files, or clone the whole repo)

## Sign Up
<center><iframe src="https://docs.google.com/forms/d/e/1FAIpQLSfRk9-yhr-H6eiBg00nzxA9_JErhNgxLZaX_eozvdTN6osAiQ/viewform?embedded=true" width="640" height="662" frameborder="0" marginheight="0" marginwidth="0">Loading...</iframe></center>