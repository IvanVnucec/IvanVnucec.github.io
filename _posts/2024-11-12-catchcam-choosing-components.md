---
title: "Catchcam: Choosing Components"
categories:
  - Blog
tags:
  - catchcam
---

## Introduction

Lets choose major hardware components for the Catchcam project. As I've written [before](https://ivanvnucec.github.io/tags/#catchcam), the idea is to have a plug and play device that alerts if the vehicle is approaching a speed camera via sound and LED signal.

Catchcam draws power from built in USB-C socket that is connected to a vehicle USB socket. As for user interfaces, it has a small speaker, Volume potentiometer, System status LED, GPS signal status LED, and Camera alert LED, and Software update button (more on that later).

In order to know the current position, Catchcam has GNSS module with on-board Antenna.

In order to reproduce audio alerts, Catchcam also incorporates DAC, Low-pass anti aliasing/reconstruction filter, and Audio amplifier.

Lets choose all the components.

## Components

### Microcontroller and Flash

First we will choose the microcontroller. Initially, I was thinking about choosing one of the simpler STM32 microcontrollers such as STM32F407 with hardware FPU, but the prices are astronomical, and in my opinion, there are better and cheaper alternatives. Also, the onboard Flash memory is around 1MB, which might be too low in order to store more than 66000 camera positions along audio samples. I would certainly need external flash to incorporate all of that.

The decision has fallen on the popular [rp2040](https://www.raspberrypi.com/products/rp2040/specifications/) microcontroller from Raspberry Pi Ltd. I've really liked this option because it features flexible I/O, with dual-core Arm Cortex-M0+ processor, 264 on-chip SRAM, and best of all - Drag-and-drop programming using mass storage over USB. I love the idea that you can simply update the software by just drag-and-drop already built firmware, which is ideal for my project because an ease of update of camera positions is a must. You dont need any external hardware or software, nor you need any special computer knowledge. Its as simple as using an USB drive.

The software resides on the `W25Q128JVSIQ` external 16MB flash which has a plenty of storage for all the camera positions and audio samples (which populates most of the flash).

### GNSS Module and Antenna

The second major part of the project is a GNSS module. I've searched for a low cost solution and stumbled on the `SIM68M` module from SIMCom Wireless Solutions Co.,Ltd. I've also seen u-blox ones, but I've had good experience with the SIMCom in the past. SIM68M features in-built LNA amplifier with an option to suply power to the active GNSS antenna. Also, SIM68M supports all of the major GNSS sattelite constelations so the device can work globally wide.

With the GNSS module comes the GNSS antenna. I've spent great deal of time in order to find best solution for my case. Idea is that the device would reside on the vehicle dashboard with the clear view of the sky in order to achieve best position tracking. There are several solutions to choosing antenna type. There are active and passive antennas. The difference is that the active antenna has build in LNA amplifier with the SAW filter in order to amplify and filter GNSS signal. Passive antennas lack those features. In the high-noise/low-signal scenarios, the active antenna is recommended. In my case, with the clear sky view and with GNSS module build-in LNA amplifier, I've choosen the passive type antenna. Moreover, I've heard that there might be a conflict if you use active antenna with LNA because there might be over-saturation of GNSS signal, but I'm not sure about that claim because GNSS signal is really weak anyway. Besides active and passive ones, the GNSS antennas comes in different design. There are PCB patch antennas, Ceramic chip antennas, Ceramic Patch antennas, and Helix antennas. Helix antennas are have good signal reception regardles of its orientation, and its popular in hand-held devices but rather small. The larger the antenna, the more signal amplification it has (with respect to the dipole antenna ofcourse). Ceramic chip antennas are compact solution for mobile devices but they are rather small. PCB patch antennas are nice because you dont need to have another part, but I'm not sure how good they are in terms of signal amplification. As Catchcam is not hand-held, nor particularry small, I've choosen to go with the `KH-GPS252504-WY` cemramic patch antenna.

### Audio

#### Speaker

The next comes the speaker with its owm audio reproduction circutry. There are varaitiy of speakers out there. There are phisically large ones with good Audio spectrum reproduction especially in the low frequencies (bass tones), but they are rather large. As for the smaller ones, they are ones with the external power leads so you can position them onto the product case, and there are trough-hole/SMD ones with that can be directly soldered to the board. I've choosen `GSPK2307P-8R1W` - trough-hole, 1W, 8 Ohm, 88 dB speaker. Its 23 mm in diameter and 6.8 mm in height. I've stumbled on the SMD ones but they are rather expensive compared to the trough-hole ones. I would like to power the speaker with the USB 5V VBUS. With the 500 mA VBUS current limit (defined by the USB standard), theoretically we can have max. power of 2.5W (5V * 500 mA) so 1W at the speaker side couild be easily accomplishied. I'm not sure about the sound level at 1W, but we'll see. I'm affraid that the user might miss the camera alert if they are listening to loud music.

#### Audio Amplifier

The speaker is driven by the Audio amplifier that draws power from the VBUS voltage. I've seen the popular and design-proven `LM358` but have dropped the idea because the signal input has to be biased. I've stumbled on the [Did I make the cheapest DIY amplifier?](https://www.youtube.com/watch?v=I4WP1u4hwpw) video that references cheap chinese `FM8002A` audio amplifier. It can power deliver 1.5W (with 8 Ohm load), handle 5V power supply, and the input signal does not need to be biased. The speaker can easily be connected between VO1 and VO2 inputs, and it also features a Shutdown mode which mutes the output. I like the Shutdown option because I'm affraid that the noise can creep into audio signal trough the USB car connection.

#### DAC and Reconstruction filter

The audio amplifier input signal is generated with 12-bit `TM8211` DAC and Low-pass anti-aliasing/reconstruction filter (Sallen-Key topology). TM8211 is another chinese `PT8211` knockoff. The data from the microcontroller comes over I2S bus to the 12-bit DAC connected to the filtered 5V VBUS, which gives 0-2.5V signal swing. Data is sampled with around 44.1kHz. Signal from the DAC output is reconstructed with the active Low-pass filter with a cut-off frequency set to about 22.05 kHz. I've choosen `` OP-AMP because it is rail-to rail amplifier and can be powered with the 5V. Gain of the Low-pass filter is set to 1. I will write about signal generation and filtering in another post.

I've also incorporated `RK10J12R0A0B` knob type potentiometer so the user can set the audio volume. The potentiometer resistance directly affects the audio amplifier gain so the signal to the speaker can be reduced all the way to the zero.

### User Interfaces

#### USB-C Connector

As for the USB connector, I've choosen standard USB-C (USB v2.0) SMD connector at 90 deg. angle and it will be placed somewhere on the board so it pertrudes nicely to the device case. I've added `NCP361SNT1G` USB Over-voltage and Over-current protection IC circutry, and added `USBLC6-2SC6Y` ESD protection to the VBUS and data lines.

#### LEDs

As for the LEDs, I've choosen `12-22SURSYGC/S530-A2/TR8` 90 deg. angle SMD leds that incorporates both Green and Red LED in the same package. Those are for the System status LED and for the GNSS signal status LED. The idea is that the System status LED blinks periodically with the green color, and if some error happens, it stays red. Similarily, the GNSS signal status stays green as long as the GNSS data is valid, and if signal is lost, it stays red. As for the Camera detected LED, it is `TJ-S3210SW5TGLC6B-A5`, also 90 deg. angle but with a single blue colored LED. The driving current for the Camera detected LED is somewhat higher at 10 mA, so it's visible even under daylight sun.

And lastly, there is a small `TSA002A3518B` 90 deg. angle push-button that enables software updates. The idea is that the user can easily update its device software by connecting it to a PC and simply drag-and-drop the firmware that has been previusly downloaded. In order to to that, the button needs to be pressed when the user connects it to a PC. That would trigger the in-built rp2040 USB mass storage bootloader which would then show the microcontroller storage as USB mass media device and enable drag-and-drop feature.

## Conclusion

And that is basically it when it comes to the components. We're left with the passive components that will not be discussed.

I've thought a lot about incorporating battery in the system so the device can be mounted on a vehicles that are lacking USB port (old vehicles or motorcicles) but I've dropped the idea for now because that would complicate the design and I'm not sure about dropping design simplicity in the prototype phase. I've also been thinking about incorporating GSM module so the devices would have been updated automatically, but that was also dropped because of the complexities involving a server that would enable those updates, and also I would need to have SIM cards that works across the globe regardles of the telecom provider which greatly increases complexity.
