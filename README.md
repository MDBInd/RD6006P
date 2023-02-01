# Riden RD6006P controller via ESPHome

This is a fork from the good work of [wildekek](https://github.com/wildekek/rd6006-controller) and ideas from [Baldanos](https://github.com/Baldanos/rd6006).

It is recomended to upgrade the stock firmware to the [alternative UniSoft firmware](https://www.eevblog.com/forum/testgear/ruideng-riden-rd6006-dc-power-supply/msg3998257/#msg3998257) as it offers better functionality. 

I have made several adaptations and improvements on the origianl ESPHome yaml configuration that enables the ESP-12F on the WiFi module to work with the RD6006P with its 5 digit of accuracy.

With this firmware you can control a Riden RD6006P Power Supply via [Home Assistant](https://www.home-assistant.io/). It uses [ESPHome](https://esphome.io/) to abstract modbus commands and expose them to Home Assistant and makes it super easy to interface with your device over WiFi.

It is intended as a replacement for the Riden mobile and PC software which after testing did not work particularly well.

## Advanced features
- Produce a triangle wave with adjustable step and delay. From 0V to OVP (Over Voltage Protection).
- Produce a sine wave with adjustable delay. From 0V to OVP (Over Voltage Protection).

Note: OVP can be set by pressing Shift + V-SET on the RD6006P.
## Requirements - Stock firmware:
- An FTDI adapter (Initial flash)
- The chip-enable pin on the RD6006P should be physically disconnected
- The RD6006P should have the TTL setting enabled

## Requirements - UniSoft firmware:
- An FTDI adapter (Initial flash)
- RD6006P settings:
  - UART Interface: TTL+EN
  - Skip keys lock: ON

## Initial flash of ESP-12F

- Jump GPIO0 to GND to enter the ESP8266 to programing mode (UART) by soldering a wire between the pins.

- Install Python and Pip if you have not already.

```
sudo apt install python python-pip
pip install esphome
```

- Flash the firmware with ESPHome

```
esphome run rd6006p.yaml
```

- Remove the jumper between GPIO0 and GND after a successful flash.

- Install the WiFi module into the RD6006P ready for use.

This is all much easier to do before you install the WiFi module inside the RD6006P. The case is designed in a way that its not easy to remove the WiFi module once installed. If the board is already installed you may need a set of dental probes to help pry the board out for flashing.

Once the board has been flashed once using this method all future flashing can be done wirelessly using ESPHome's OTA feature.
