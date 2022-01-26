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
 This project is broken up into two key areas:
 - Service application running on Armbian as a daemon, which handles the network share mounting, manages Audacious in headless mode, playlist, and sound sink
 - MICON (Man Interface CONtrol) that drives the LCD display, reads the optical encoder and power button, reads the IR sensor, and controls the DIR chip (digital interface receiver)

The service application is written in C compiled with Code::Blocks for the armhf target and requires the arm-linux-gnueabihf GCC compiler to be installed.
The MICON application is written in C which is a project for the STM32CubeIDE (ARM Cortex M0). This may include libraries such as CMSIS and is dependent on ST Micro's libraries for the micro's peripherals. The latter is subject to change and what may work now may be broken in 2 years' time because ST Microelectronics has consistently changed the libraries over the years. When in doubt, clone the whole project!

### Linux
This project is designed to work with Armbian Focal. A number of steps are required to be performed (specifically armbian-config), as well as installation of software on the boot medium. A complete ready-to-run SD card image will be provided. However note that the OrangePi Zero requires a small hardware modification to gain access to the S/PDIF output on the AllWinner H2.
 
