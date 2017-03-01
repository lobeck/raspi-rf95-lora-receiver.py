# raspi_rf95_lora_receiver.py

A Python and `wiringpi` based LoRa receiver for RaspberryPi

## Overview

This is a small receiver software tested with RaspberryPi 3 and the [Adafruit RFM95W ](https://www.adafruit.com/products/3072)

The wiring is based on [LoRasPI](https://github.com/hallard/LoRasPI), but it should work with any RFM95.
 
Currently it uses continous RX mode, allows for crc validation and prints the packet unstructured to the console. There is no support for addressing or other advanced more features yet.

## Example

    GPIO_CALLBACK! 1488286567.54
    RX_DONE | VALID_HEADER
    last packet length 24
    last packet address 120
    reading data [1, 2, 0, 0, 72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100, 32, 35, 56, 50, 0, 32, 32, 32]
    LoRaPacketHeader(source=1, dest=2, id=0, flags=0)
    data Hello World #82
    valid headers 70
    valid packets 65
    last packet SNR -6
    last packet RSSI -90
    
    GPIO_CALLBACK! 1488286577.25
    RX_DONE | CRC_ERROR | VALID_HEADER
    last packet length 24
    last packet address 144
    reading data [1, 2, 0, 0, 72, 101, 108, 172, 99, 32, 87, 126, 114, 124, 68, 32, 1, 24, 22, 106, 32, 35, 36]
    LoRaPacketHeader(source=1, dest=2, id=0, flags=0)
    data Hel�c W~r|D j #$
    valid headers 71
    valid packets 65
    last packet SNR -12
    last packet RSSI -90


## Motivation

I took heavy inspiration from [RadioHead](https://github.com/hallard/RadioHead), however i didn't like the lack of interrupt support.

This combined with a lack of crc validation, reservations against C++ and pure curiosity motivated me, to create another  receiver implementation in Python.
 
## License

Copyright (C) 2017 - Christian Becker

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, version 3 of the License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.