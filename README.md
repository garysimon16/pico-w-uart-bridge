Raspberry Pi Pico USB-UART Bridge
=================================

This program bridges the Raspberry Pi Pico HW UARTs to two independent USB CDC serial devices in order to behave like any other USB-to-UART Bridge controllers.

Disclaimer
----------

This software is provided without warranty, according to the MIT License, and should therefore not be used where it may endanger life, financial stakes, or cause discomfort and inconvenience to others.

Raspberry Pi Pico Pinout
------------------------

| Raspberry Pi Pico GPIO | Function |
|:----------------------:|:--------:|
| GPIO16 (Pin 21)        | UART0 TX |
| GPIO17 (Pin 22)        | UART0 RX |
| GPIO4 (Pin 6)          | UART1 TX |
| GPIO5 (Pin 7)          | UART1 RX |

## Changes made for Pico-W

Added LED indication of UART write transfers. Amended LED to use the WiFi driver.

LED comes on for USB connection, goes off for disconnect. For UART writes, LED toggles momentarily.

### To build

```
git clone [path]
mkdir build
./build.sh
```

### To test

Connect the TX and RX either of the same UART or two separate.

Either use echo and cat:

```
stty -F /dev/ttyACM0 [baudrate] # make sure same rate set on both
cat /dev/ttyACM1
echo "Hello" > /dev/ttyACM0
```
It might take two echo tries for print to appear.

Or use minicom with the provided configs.˛
