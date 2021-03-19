# Hardware hacking

Resources related to hardware/IoT hacking. Security-oriented and targeted at
beginners.

## Bookmarks

TODO: Include the
[Embedded Analysis guide](https://github.com/cyphunk/JTAGenum/wiki/Embedded-Analysis)
from the JTAGenum project.

### Forums

  - [Hackaday](https://hackaday.com)
  - [CCC](https://media.ccc.de)
  - [EEVblog](https://eevblog.com)

### EEPROM (SPI)

EEPROM chips are a good target because it's easy to extract and analyze
memory dumps from EEPROM. A Bus Pirate v3 and a Pomona clip can be used to
dump the memory. Use `binwalk` and GHIDRA (or IDA) to reverse-engineer the
firmware.

  - [wrongbaud.github.io](https://wrongbaud.github.io)
  - [flashrom.org](https://flashrom.org)

### JTAG/SWD

A debugging interface widely deployed in CPUs/MCUs found on embedded devices.
Bus Pirate + OpenOCD on a laptop can be used to interface the target device.
If the JTAG pinout is not known, it can be brute-forced with
e.g. Raspberry Pi + JTAGenum (watch out for voltage levels, the Raspberry Pi
only supports 3.3V). JTAG can be used to dump memory that is mapped to the
address space of the targeted CPU. It's also possible to use OpenOCD and hook
up `gdb` to execute firmware in a step by step fashion.
    
  - [#03 - How To Find The JTAG Interface - Hardware Hacking Tutorial](https://www.youtube.com/watch?v=_FSM_10JXsM)
  - [Blackbox JTAG Reverse Engineering (26C3)](https://media.ccc.de/v/26c3-3670-en-blackbox_jtag_reverse_engineering)
  - [wrongbaud.github.io](https://wrongbaud.github.io)

### UART (also RS232)

A serial port, typically offering access to a boot or root console. The Bus
Pirate can be used here again (watch out input voltage though, a bidirectional
logic level shifter may be required).
    
  - [#02 - How to Find the UART Interface - Hardware Hacking Tutorial](https://www.youtube.com/watch?v=6_Q663YkyXE)
  - [Hardware Hacking 101: Getting a root shell via UART (River Loop Security)](https://www.riverloopsecurity.com/blog/2020/01/hw-101-uart/)
    
### CAN

Network stack for embedded devices. No security. USBtin can be used to
interface CAN.
    
  - [Hacking a mileage manipulator CAN bus filter device (dangerouspayload.com)](https://dangerouspayload.com/2020/03/10/hacking-a-mileage-manipulator-can-bus-filter-device)
  - [USBtin](https://www.fischl.de/usbtin)
    
### USB

Use `lsusb` to enumerate devices, Wireshark to monitor USB traffic, and PyUSB
to develop custom USB drivers.
    
The GreatFET board + FaceDancer firmware is interesting for USB. It can be
used to emulate USB devices, and it can be used as an intercepting proxy
for USB. Bonus: it's all Python.

  - [Dan Weatherill: A call to arms - let's hack USB devices, it's mostly easier than you think](https://www.youtube.com/watch?v=K7Glcep_iGc)
  - [PyUSB](https://github.com/pyusb/pyusb/blob/master/docs/tutorial.rst)
  - [FaceDancer 2.0 (SHA2017)](https://media.ccc.de/v/SHA2017-221-facedancer_2_0)
  - [USB Reverse Engineering: Down the rabbit hole](https://www.devalias.net/devalias/2018/05/13/usb-reverse-engineering-down-the-rabbit-hole/)

### RFID

Get a couple of RFID reader/writer/emulators such as the ChameleonMini and some
RFID tags to experiment.
    
  - [ChameleonMini](https://kasper-oswald.de/gb/chameleonmini/)
    
## Get started

If starting from scratch I would recommend to play around with an Arduino kit
first. I can't stress enough the educational value you'll get out of it. Some
of the underlying perks:
    
  - Electronic components
  - Analogic vs digital signals
  - Tension dividers
  - FM, AM, PWM
  - Breadboarding
  - How to write and flash firmware
  - ...

Then, once these basics are out of the way, I would recommend to practice by
looking at whatever device you can get your hands on. Routers are typically
a good target because (1) they're fun, (2) you can get a copy of your home
model for cheap off eBay, and (3) somebody probably already put instructions
online on how to do it.
    
## Tools

  - Precision screwdriver set. Preferably one with a hole in the handle (to use
    as a pivot for stubborn screws) and a magnetic tip.
  - Multimeter. Pick one with a continuity test mode (with audio signal).
  - [Bus Pirate v3](http://dangerousprototypes.com/docs/Bus_Pirate). This is a
    popular tool for interfacing common hardware buses with your laptop. Great
    value.
  - Soldering tools. See
    [soldering](/soldering.md).
  - Logic analyzer. Preferably one supported by
    [sigrok](https://sigrok.org/wiki/Supported_hardware#Logic_analyzers). Saleae
    has published some interesting
    [guides](https://articles.saleae.com/logic-analyzers). Pick one with fairly
    high sampling frequency (200 MHz is lots already) and a wide voltage input
    range (convenient because some protocols like RS232 can be relatively high
    voltage). I currently use a Kingst LA2016.
  - A rotary tool/"dremel" is often convenient to have. I currently use a Proxxon
    Micromot 50/E (Proxxon > Dremel in terms of quality). I've also heard good
    feedback about die grinders but never used one myself.
