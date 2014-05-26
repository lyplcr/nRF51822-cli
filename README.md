nRF51822-cli
==================

Provides a build system for nRF51822 projects.

Handles
- ~~Compilation~~
- Flash Programming
- SoftDevices

Heritage
---------

There are several similar projects available such as [this](https://github.com/hlnd/nrf51-pure-gcc-setup), [that](https://github.com/pauloborges/nrf51822-linux-template), and the [other](https://github.com/EarthLord/nrf51Demo). Each has their own merits.

This project aims to be as simple and well documented as possible, for example, the [very concise](https://github.com/pauloborges/nrf51822-linux-template/blob/master/scripts/erase.jlink) JLink shorthand commands are expanded and [written more naturally](https://github.com/hughobrien/nRF51822-cli/blob/master/flash).

Usage
-----
In practice:
- ./erase
- ./flash |SoftDevice| |Application|

The flash command takes as arguments a SoftDevice and an application.
- An internal lookup table determines the code offset for the given SoftDevice.
- The application is checked for SoftDevice compatibility.
- Both are flashed to the device.

The erase command takes no arguments.
- Erasing both region0 and region1 areas, if defined.
- Erasing the User Information Configuration Registers.

Tests
-----
Using the [Nordic NRFGo Studio](http://www.nordicsemi.com/chi/node_176/2.4GHz-RF/nRFgo-Studio) both the SoftDevice and the application binaries were read from the flashed chip and successfully verified against the original hexfiles.

Requirements
------------

- nRF51 SDK
- A SoftDevice, s100v5/v6/v7, s120
- SEGGER JLink
- nRF51822 Evaluation Kit board PCA1001

In each case, there are multiple versions of these available. The code should be easily modifiable to support them.
