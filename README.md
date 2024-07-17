A very common problem where it is not possible to connect to 2 printers/instances in Klipper, or only 1 is that it has a connection, this is due to USB ports.
In my case I have 2 Ender 3 V3 SE, with the same Board/Chip and only 1 works.
Inside the printer.cfg file you need to change the data with the right USB port.
To find the port, first connect the 2 USB cables on the Printers, and then open SSH and type: 

ls /dev/serial/by-path/*

It will show all the USB connections by the Printers

Copy paste that USB path and replace with the original MCU:


ORIGINAL:

[MCU]
serial: /dev/serial/by-id/usb-1a86_USB_Serial-if00-port0
#serial: /dev/ttyUSB0
restart_method: command

CHANGE TO:
(IT CAN CHANGE THE DATA INFO, THIS IS MY USB PORTS)
PRINTER 1(ex)

[mcu]
serial: /dev/serial/by-path/platform-xhci-hcd.0-usb-0:1:1.0-port0
#serial: /dev/ttyUSB0
restart_method: command

Then change to the Instance on Klipper for Printer 2 and find same MCU, and replace for:

[mcu]
serial: /dev/serial/by-path/platform-xhci-hcd.1-usb-0:2:1.0-port0
#serial: /dev/ttyUSB0
restart_method: command


Dont enable ttyUSB0 

Thats it
