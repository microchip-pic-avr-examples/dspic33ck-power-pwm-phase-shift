<div id="readme" class="Box-body readme blob js-code-block-container">
 <article class="markdown-body entry-content p-3 p-md-6" itemprop="This needs to be locked down and 'never' changed">
 <p><a target="_blank" href="https://www.microchip.com" rel="nofollow"><img src="images/microchip.png" alt="MCHP" width="200";"></a></p>

# dsPIC33C High-Resolution PWM Configuration: Lab 4
**Phase-Shifted PWM Waveform Generation**

<p><center><a href="https://www.microchip.com/MA330048" rel="nofollow">
<img src="images/ma330048.jpg" alt="dsPIC33CK Digital Power Plug-In Module" width="300"></a></center></p>

- - -

## Summary
Learning how to use the High Resolution PWM Module of dsPIC33C MP devices, Lab 4:
Code example for dsPIC33CK and dsPIC33CH devices showing a basic configuration of the high-resolution PWM module using two PWM generator channels generating a Phase-Shifted PWM waveforms

- - -

## Related Documentation
- [dsPIC33CK256MP508 Family Data Sheet](https://ww1.microchip.com/downloads/en/DeviceDoc/dsPIC33CK256MP508-Family-Data-Sheet-DS70005349G.pdf)
- [dsPIC33CK256MP508 Family Silicon Errata and Data Sheet Clarification](https://ww1.microchip.com/downloads/en/DeviceDoc/dsPIC33CK256MP508-Family-Silicon-Errata-and-Data-Sheet-Clarification-DS80000796G.pdf)
- [dsPIC33CH512MP508 Family Data Sheet](http://ww1.microchip.com/downloads/en/DeviceDoc/dsPIC33CH512MP508-Family-Data-Sheet-DS70005371D.pdf)
- [dsPIC33CH512MP508 Family Silicon Errata and Data Sheet Clarification](http://ww1.microchip.com/downloads/en/DeviceDoc/dsPIC33CH512MP508-Family-Silicon-Errata-and-Data-Sheet-Clarification-DS80000805F.pdf)

**Please always check for the latest data sheets on the respective product websites:**
- [dsPIC33CK256MP508 Family](https://www.microchip.com/dsPIC33CK256MP508)
- [dsPIC33CH512MP508 Family](https://www.microchip.com/dsPIC33CH512MP508)

## Software Used 
- [MPLAB® X IDE v5.40](https://www.microchip.com/mplabx-ide-windows-installer)
- [MPLAB® XC16 Compiler v1.60](https://www.microchip.com/mplabxc16windows)
- [MPLAB® Code Configurator v4.01](https://www.microchip.com/mplab/mplab-code-configurator)

## Hardware Used
- Digital Power Development Board, Part-No. [DM330029](https://www.microchip.com/DM330029)
- dsPIC33CK Digital Power Plug-In Module (DP PIM), Part-No. [MA330048](https://www.microchip.com/MA330048)
- Alternatively: dsPIC33CH Digital Power Plug-In Module (DP PIM), Part-No. [MA330049](https://www.microchip.com/MA330049)

## Supported Target Devices
- [dsPIC33CK256MP506](https://www.microchip.com/dsPIC33CK256MP506)
- [dsPIC33CH512MP506](https://www.microchip.com/dsPIC33CH512MP506)
- Code compatible with all Single and Dual Core dsPIC33C MP families of devices

- - -

## Setup
- Plug-In the dsPIC33CK or dsPIC33CH Digital Power Plug In Module into the Digital Power Development Board PIM socket J1
- Open and compile the firmware and program the DSC

<br><center><img src="images/dm330029.jpg" width="400"></center><br>

## Operation
After the device has been programmed and the MCU starts up, a 90 degrees phase shift between the two synchronized PWM Generators is generated see below screen capture. Both PWM Generator #1 and #3 are configured in complementary mode with 200 kHz frequency and 50% duty cycle waveform outputs.  PWM Generator 1 output is available at PWM1H/L pins while PWM Generator 3 output is available at PWM3H/L pins. 

<br><center><img src="images/pwm90phaseshift.png" width="400"></center><br>
<br><center>*CH1(blue):PWM1H  CH2(green):PWM1L  CH3(red):PWM3H  CH4(purple):PWM3L*</center><br>

By pressing the on-board push button *USER* on the Digital Power Development Board, the phase shift  is toggled between the initial 90 degrees and 180 degrees see below screen capture.

<br><center><img src="images/pwm180phaseshift.png" width="400"></center><br>
<br><center>*CH1(blue):PWM1H  CH2(green):PWM1L  CH3(red):PWM3H  CH4(purple):PWM3L*</center><br>


Please refer to section *FIRMWARE QUICK-START GUIDE* below for more information on the initialization process and code structure.

<br><center><img src="images/dm330029-pinmap.png" width="600"></center><br>
 
- - -

## FIRMWARE QUICK-START GUIDE

This code example builds on previous code examples showing how to use Microchip Code Configurator (MCC) to set up device clock domains. 
Although MCC also supports configuration tools for the High Resolution PWM module, PWM configuration in this example builds on generic peripheral drivers to help users better understand the peripheral architecture and key aspects of specific configurations and operating modes. 
In each PWM example code project the PWM configuration procedure is located in the user file pwm.c, where each register bit required to achieve/enable the specific function or mode of interest is set and its function described with comments.
Once users are familiar with the architecture, features and capabilities, both configuration options (generic peripheral library or MCC) may be used.

#### a) Project Directory Structure <br/>
The project contains four sub-directories
1. config: location of all hardware abstraction header files
2. common: location of generic peripheral drivers 
3. MCC Generated Files: all device configuration files auto-generated by MCC
4. root: application user code

On the hard drive, main.c/h are located in the MPLAB X project directory. 
All other user files, incl. peripheral drivers, are located in the sub-directory *sources*. 
Files generated by MCC are always located in their own sub-directory *mcc_generated-files* 

#### b) Using the generic PWM peripheral driver <br/>  
The PWM peripheral driver files p33c_pwm.c/h provide data structures representing the Special Function Register (SFR) sets of PWM generators and the PWM base module. These 'virtual' PWM objects are used to load, read and modify PWM generator configurations without the need for hard-coded instructions, which would make the code hard to migrate from one peripheral to another or even across devices.To simplify PWM configurations, in these examples, each register is reset to a known default state before the user configuration of interest is set. Thus, only the register setting which really matters for a certain features/function are shown.

To learn more about the generic PWM driver, its supported features and intended use cases, please read the comments inside p33c_pwm.c.

#### c) Executing the Code Example <br/> 
This code has been written to automatically start up and perform the function of interest. Please read the demo instructions on top of file main.c to learn more about the code example, test points, expected signals and demo mode operation.



- - - 

© 2020, Microchip Technology Inc.
