# Information gathering

One of the primary objectives is to obtain a copy of the firmware. To do so it
is necessary to gather information about the targeted device to understand where
is the non-volatile storage and if there are any debugging interfaces available.

## From the device

Information is initially gathered from the device itself:

  - **External labels**, which may provide the manufacturer name, model number,
    revision, and manufacturing date.
  - **Silkscreen printing**, which may provide the manufacturer name, model
    number,revision, and manufacturing date.
  - **Part numbers**, which are normally printed on all integrated circuits
    unless they have been scraped off by the manufacturer.
  - **Common pinouts**, often your board will have undocumented header
    pins or groups of contacts that are not wired to anything, but you can
    infer the purpose if it corresponds to a common pinout (e.g. an isolated
    group of 4 pins is likely to be a UART interface).

## Online

Online sources can be looked up to retrieve datasheets or obtain further
information about the device:

  - **Search engines**, by searching for the model or part number you will
    usually find the datasheet. `type:pdf` can
    help. If you struggle finding information about the device, try with
    [Baidu](https://baidu.com) or use a search engine aggregator like
    [searx](https://searx.space).
  - **Specialized websites**, like
    [DeviWiki](https://deviwiki.com) or [OpenWrt](https://openwrt.com).
  - [**fccid.io**](https://fccid.io), which provides internal images of the board
    and manuals. Every device sold in the US that uses electronic emissions will
    have an entry in the FCC. Pictures are often good enough to be able to read
    part number off integrated circuits, consequently it can be an
    outstanding source of information if you are working on an uncommon device
    and cannot disassemble it to look into it for whatever reason.
  - **Prior art**, if the device is popular it is likely to be already well
    documented in blogs or forums.

A thorough methodology would be to fill in a table with all part numbers of all
components found in the targeted device, and then retrieve the datasheet
for every one of them to understand what it does. With experience you will get
familiar with manufacturer brands and even recognize parts that you see reused
across different devices. Usually it is also possible to quickly identify the
role of common components (such as flash or EEPROM) at first glance.

## Datasheets

Datasheets are a mine of information because they contain every detail you need to know about the component, in particular:

  - **Purpose**, what the integrated circuit is used for. Often you will want
    to know if it has any non-volatile storage embedded in it.
  - **Pinout**, which provides a description of what every single pin does. By
    convention, pins are numbered in a clockwise fashion with pin 1 being
    identified with a small dot in one of the corners of the integrated circuit.
  - **Voltage ranges**, which should be known prior to interacting with the
    integrated circuit to avoid the risk of damage.
  - **Bus protocols** that are supported by the device. If you know which
    bus protocols or debugging interfaces are supported, you can interact with
    the device and perform interesting operations like dumping storage contents.
    The most common bus protocols are I2C, SPI, JTAG, and UART. The
    [Bus Pirate](http://dangerousprototypes.com/docs/Bus_Pirate)
    can interface all these common bus protocols, so it is a useful tool to have.
  - For more complex integrated circuits like MCUs or CPUs, the datasheet will
    also provide further details like the **physical address space layout**.
    
## Obfuscation
    
Every so often, you will find that manufacturers scrape off or cover the
integrated circuit in a blob of epoxy to make part numbers unreadable and make
the information gathering stage more difficult. In this case, it might still be
possible to identify the integrated circuit with this method:

  1. Take note of the integrated circuit package and number of pins.
  2. Identify GND pins by checking every single pin with a continuity test
     performed with the multimeter between the pin and ground.
  3. Download all datasheets you can find for an integrated circuit that is
     manufactured in this package and has the same number of pins.
  4. Retain integrated circuits that have a pinout that matches the position of
     the GND pins you observed.
