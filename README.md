<!-- SPDX-License-Identifier: MIT -->
<!-- SPDX-FileCopyrightText: Copyright 2024 Sam Blenny -->
# Greenhouse Logger

**WORK IN PROGRESS (ALPHA)**


## Hardware


### Parts

This project is designed for making several loggers using parts on hand or
whatever is cheap and available. Each logger needs a dev board, temperature
sensor, setup-mode jumper, battery pack, and enclosure.

ESP32-S3 Dev Board:
- Adafruit Metro ESP32-S3 - 16 MB Flash, 8 MB PSRAM (#5500)
- Adafruit QT Py ESP32-S3 - 8 MB Flash, No PSRAM (#5426)
- Adafruit QT Py ESP32-S3 - 4 MB Flash, 2MB PSRAM (#5700)

Temperature Sensor and Setup-Mode Jumper:
- Waterproof 1-Wire DS18B20 Digital temperature sensor
- 4.7 kΩ thru-hole resistor
- Hookup wire
- Heat shrink tubing or electrical tape (prevent shorts)
- Proto PCB (optional, for keeping soldered wiring neater)
- Male header pins + 2 position removable jumper (or F-F DuPont wire)

Battery Pack:
- Qt PY option: 3xAA or 3xAAA battery holder + matching NiMH batteries
- Metro/Feather Option: Adafruit Lithium Ion battery pack (400+ mAh)

Enclosure:
- Water resistant outdoor junction box with cable gland
- Silica gel desiccant pack (2g should be enough)


### Tools and Consumables

You will need soldering tools and solder.


### Pinouts

**CAUTION:** For reliable temperature conversions with DS18B20 1-wire sensors,
be sure to wire up the 3.3V pin (red wire). Parasitic power with the DS18B20
sensors may be unreliable, particularly with the counterfeit sensors
[which are very common](https://github.com/cpetrich/counterfeit_DS18B20).

| Metro S3 | DS18B20      | 4.7 kΩ |
| -------- | ------------ | ------ |
| GND      | Black/Blue   |        |
| 3.3      | Red          | Lead 1 |
| A1       | Yellow/White | Lead 2 |


| Qt Py S3 | DS18B20      | 4.7 kΩ | 3xAA holder |
| -------- | ------------ | ------ | ----------- |
| GND      | Black/Blue   |        |             |
| 3V       | Red          | Lead 1 |             |
| A1       | Yellow/White | Lead 2 |             |
| GND      |              |        | Black       |
| BAT      |              |        | Red         |


### Soldering

*TODO*


## Related Documentation:

Dev Boards:
- https://learn.adafruit.com/adafruit-metro-esp32-s3
- https://learn.adafruit.com/adafruit-qt-py-esp32-s3

1-wire Temperature Sensing:
- https://learn.adafruit.com/using-ds18b20-temperature-sensor-with-circuitpython
- https://docs.circuitpython.org/projects/onewire/en/stable/
- https://docs.circuitpython.org/projects/ds18x20/en/stable/api.html

ESP32-S3 Battery Power and Deep Sleep:
- https://learn.adafruit.com/deep-sleep-with-circuitpython/overview
- https://docs.circuitpython.org/en/stable/shared-bindings/alarm/

Miscellaneous Python Tricks:
- https://docs.circuitpython.org/en/stable/shared-bindings/struct/
- https://docs.python.org/3/library/struct.html (pack, unpack)
- https://docs.python.org/3/library/functions.html#property (decorators)

Python Time Stuff:
- https://docs.circuitpython.org/en/stable/shared-bindings/time/#time.struct_time
- https://docs.circuitpython.org/en/stable/shared-bindings/time/#time.mktime
- https://docs.python.org/3/library/time.html#time.mktime
- https://docs.python.org/3/library/datetime.html#datetime.datetime.fromtimestamp
- https://docs.circuitpython.org/projects/datetime/en/stable/api.html#adafruit_datetime.datetime.fromtimestamp

MAX17048 Battery Fuel Gauge:
- https://learn.adafruit.com/adafruit-max17048-lipoly-liion-fuel-gauge-and-battery-monitor/python-circuitpython
- https://docs.circuitpython.org/projects/max1704x/en/stable/api.html
- https://www.analog.com/media/en/technical-documentation/data-sheets/MAX17048-MAX17049.pdf


## Updating CircuitPython

**NOTE: To update CircuitPython on the ESP32-S3 boards, you need to use the
.BIN file (combination bootloader and CircuitPython core)**

1. Download the CircuitPython 9.2.1 **.BIN** file from the relevant page on
   circuitpython.org:
   - [Adafruit Metro ESP32-S3](https://circuitpython.org/board/adafruit_metro_esp32s3/)
   - [Adafruit QT Py ESP32-S3 4MB Flash/2MB PSRAM](https://circuitpython.org/board/adafruit_qtpy_esp32s3_4mbflash_2mbpsram/)
   - [Adafruit QT Py ESP32-S3 No PSRAM](https://circuitpython.org/board/adafruit_qtpy_esp32s3_nopsram/)

2. Follow the instructions in the
   [Web Serial ESPTool](https://learn.adafruit.com/circuitpython-with-esp32-quick-start/web-serial-esptool)
   section of the "CircuitPython on ESP32 Quick Start" learn guide to update
   your board: first erase the flash, then program the .BIN file.


## Installing CircuitPython Code

To copy the project bundle files to your CIRCUITPY drive:

1. Download the project bundle .zip file using the button on the Playground
   guide or the attachment download link on the GitHub repo Releases page.

2. Expand the zip file by opening it, or use `unzip` in a Terminal. The zip
   archive should expand to a folder. When you open the folder, it should
   contain a `README.txt` file and a `CircuitPython 9.x` folder.

3. Open the CircuitPython 9.x folder and copy all of its contents to your
   CIRCUITPY drive.

To learn more about copying libraries to your CIRCUITPY drive, check out the
[CircuitPython Libraries](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries)
section of the
[Welcome to CircuitPython!](https://learn.adafruit.com/welcome-to-circuitpython)
learn guide.
