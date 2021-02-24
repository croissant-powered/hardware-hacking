# Hardware hacking

Resources related to hardware/IoT hacking. Securited-oriented and targeted at
beginners.

## Bookmarks

### Forums

  - https://hackaday.com
  - https://media.ccc.de
  - https://eevblog.com
  - https://wikipedia.org (convenient for learning the various acronyms)

### EEPROM (SPI)

  EEPROM chips are a good target because it's easy to extract and analyze
  memory dumps from EEPROM. A Bus Pirate v3 and a Pomona clip can be used to
  dump the memory. Use `binwalk` and GHIDRA (or IDA) to reverse-engineer the
  firmware.

  - https://wrongbaud.github.io
  - https://flashrom.org

### JTAG/SWD

  A debugging interface widely deployed in CPUs/MCUs found on embedded devices.
  Bus Pirate + OpenOCD on a laptop can be used to interface the target device.
  If the JTAG pinout is not known, it can be brute-forced with
  e.g. Raspberry Pi + JTAGenum (watch out for voltage levels, the Raspberry Pi
  only supports 3.3V). JTAG can be used to dump memory that is mapped to the
  address space of the targeted CPU. It's also possible to use OpenOCD and hook
  up `gdb` to execute firmware in a step by step fashion.
    
  - https://media.ccc.de/v/26c3-3670-en-blackbox_jtag_reverse_engineering
  - https://wrongbaud.github.io

### UART (also RS232)

  A serial port, typically offering access to a root console. The Bus Pirate
  can be used here again (watch out input voltage though, a logic level
  shifter may be required).
    
  - https://www.riverloopsecurity.com/blog/2020/01/hw-101-uart/
    
### CAN

  Network stack for embedded devices. No security. USBtin can be used to
  interface CAN.
    
  - https://dangerouspayload.com/2020/03/10/hacking-a-mileage-manipulator-can-bus-filter-device
  - https://www.fischl.de/usbtin
    
### USB

  Use `lsusb` to enumerate devices, Wireshark to monitor USB traffic, and PyUSB
  to develop custom USB drivers.
    
  The GreatFET board + FaceDancer firmware is interesting for USB. It can be
  used to emulate USB devices, and it can be used as an intercepting proxy
  for USB. Bonus: it's all Python.

  - https://www.youtube.com/watch?v=K7Glcep_iGc
  - https://github.com/pyusb/pyusb/blob/master/docs/tutorial.rst
  - https://media.ccc.de/v/SHA2017-221-facedancer_2_0
  - https://www.devalias.net/devalias/2018/05/13/usb-reverse-engineering-down-the-rabbit-hole/

### RFID

  Get a couple of RFID reader/writer/emulators such as the ChameleonMini and some
  RFID tags to experiment.
    
  - https://kasper-oswald.de/gb/chameleonmini/
    
## Get started

  If starting from scratch I would recommend to play around with an Arduino kit
  first. I can't stress enough the educational value you'll get out of it. Some
  of the underlying perks:
    
  - Electronic components
  - Analogic vs digital signals
  - Tension dividers
  - PWM
  - How to write and flash firmware
  - ...
    
## Tools

  - Precision screwdriver set. Preferably one with a hole in the handle (to use as a pivot for stubborn screws) and a magnetic tip.
  - Multimeter. Pick one with a continuity test mode (with audio signal).
  - Bus Pirate v3. This is a popular tool for interfacing hardware buses with your laptop. Great value.
  - A soldering iron + solder wire. Cheap ones are ok but get higher quality if possible.
  - Logic analyzer. Preferably one supported by https://sigrok.org/wiki/Supported_hardware#Logic_analyzers. See https://articles.saleae.com/logic-analyzers for a guide. Pick one with fairly high sampling frequency (200 MHz is lots already) and a wide voltage input range (convenient because some protocols like RS232 can be relatively high-voltage).

