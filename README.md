# Rouge - A replacement for Logitech's Squeezebox
This is the full project for Rouge, a replacement for the crud that is the Logitech Squeezebox.
The project has arisen out of the personal need for a standalone networked audio player that can
play FLAC files from any typical network share including NAS devices

### Feature Set
- Linux based embedded system
- Full connectivity stack including the ability to mount network shares
- High quality audio reproduction with an on-board D/A converter capable of 24 bits / 192kHz
- Graphics front panel display (initially proposed as VFD but Futaba discontinued VFD manufacture)
- Ability to display Japanese titles (J-pop) on FLAC files that are from Japanese artists. This requires a complete Japanese Unicode font
- Leverages Armbian running on an AllWinner H2 SoC (OrangePi Zero LTS)
- Ability to work with USB attached sound cards e.g. ASUS XONAR MK 2

### Project Structure
Project consists of a standard ARMBIAN installation (with software installed) on the OrangePi. The serial port mates with a UART on the STM32.
The STM32F072RB implements the MICON
 - MICON (Man Interface CONtrol) that drives the LCD display, reads the optical encoder and power button, reads the IR sensor, and controls the DIR chip (digital interface receiver)

The MICON application is written in C which is compiled using Atollic TrueSTUDIO*. This requires creation of an initial project and then transplantation of CMSIS and
the STM32F072 Standard Peripheral Libraries. Note that we DO NOT USE STM32CubeIDE at this time because a) the HAL gets in the way of us doing real hardware driving and
b) any change to the device peripherals is not easy because the HAL is in the way. If you change it using the IOC file, it rubs out all your code. Pretty dumb!

### Linux
This project is designed to work with Armbian Focal. A number of steps are required to be performed (specifically armbian-config), as well as installation of software on the boot medium. A complete ready-to-run SD card image will be provided. However note that the OrangePi Zero requires a small hardware modification to gain access to the S/PDIF output on the AllWinner H2.
 
