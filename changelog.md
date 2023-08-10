# dspic33ck-power-pwm-phase-shift, release v1.1.0

### Release Highlights

Version 1.1.0 of this code example is a maintenance cycle release, which is required to keep the source code provided being fully supported by the most recent development tool chain. In this release no functional changes have been made in comparison with the previous version.

### Features Added\Updated

* Updated gitignore file filtering clutter of MPLAB X IDE 6.05 and later
* Fixed typos in leading comment of main.c
* Removed interrupt register bits, which are not supported by DFP versions v1.5.135 and later
* Switched XC16 compiler version to v2.00
* Switched Device File Pack (DFP) to version 1.10.341
* Removed obsolete virtual folder from MPLAB X project explorer
* Changed label of PWM Module register set from P33C_PWM_SFRSET_t to P33C_PWM_MODULE_t

&copy; 2023, Microchip Technology Inc.

---

# dspic33ck-power-pwm-phase-shift, release v1.0.0

### Release Highlights

This is the initial release demonstrating the basic configuration of a high-resolution PWM generator of the dsPIC33C family of devices.
This example is part of a series of code examples highlighting specific operating modes and features.

### Features Added\Updated

In this intial version the on-board LED of the dsPIC33CK Digital Power Plug-In Module is toggled with a interval üperiod of 300 ms, when the controller is running at maximum speed of 100 MIPS.
After startup, 90 degrees phase shift will be generated between pwm generator #1 and pwm generator #3. By pressing the on-board push button *USER* on the Digital Power Develpoment Board, the phase shift is toggled between the initial 90 degrees and 180 degrees.
