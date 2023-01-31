# Riden RD6006P controller via ESPHome

This is a fork from the good work of [wildekek](https://github.com/wildekek/rd6006-controller).

It is recomended to upgrade the stock firmware to the [alternative UniSoft firmware](https://www.eevblog.com/forum/testgear/ruideng-riden-rd6006-dc-power-supply/msg3998257/#msg3998257) as it offers better functionality. 

I have made several adaptations and improvements on the origianl ESPHome yaml configuration that enables the ESP-12F on the WiFi module to work with the RD6006P with its 5 digit of accuracy.

With this fimrware you can control a Riden RD6006P Power Supply via [Home Assistant](https://www.home-assistant.io/). It uses [ESPHome](https://esphome.io/) to abstract modbus commands and expose them to Home Assistant and makes it super easy to interface with your device over WiFi.

It is intended as a replacement for the Riden mobile and PC software which after testing did not work particularly well.

The functionality is currently *very* limited, but can easily be extended by borrowing ideas from https://github.com/Baldanos/rd6006, which was a huge inspiration for this project.

## Requirements - Stock firmware:
- An FTDI adapter (Initial flash)
- The chip-enable pin on the RD6006P should be physically disconnected
- The RD6006P should have the TTL setting enabled

## Requirements - UniSoft firmware:
- An FTDI adapter (Initial flash)
- RD6006P settings:
  - UART Interface: TTL+EN
  - Skip keys lock: ON

<img width="1028" alt="image" src="https://user-images.githubusercontent.com/2332647/171522772-cb27c1a2-5ebc-4385-a022-043dd3dfc149.png">
