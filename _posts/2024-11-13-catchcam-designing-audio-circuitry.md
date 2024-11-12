---
title: "Catchcam: Designing Audio Circuitry"
categories:
  - Blog
tags:
  - catchcam
header:
# TODO: add header image
  image: /assets/images/components.jpg
# TODO: remove this once finished
published: false
---

In this post, I will be discussing the audio circuitry of the Catchcam. The audio circuitry is responsible for converting the digital audio data from the microcontroller into an analog signal that can be played through a speaker. Below is a block diagram of the audio circuitry of the Catchcam.

// TODO: add block diagram

The audio circuitry consists of:

- power supply filtering,
- digital-to-analog converter (DAC),
- anti-aliasing (reconstruction) filter (AAF),
- audio amplifier, and
- speaker.

Let's discuss each of these components in detail.

## Filtering Noise from a Vehicle's USB Port for an Audio Power Supply

When designing an audio power supply, it's important to ensure a clean and stable power source. In this case, the power supply needs to be at 5 volts and will be directly sourced from the USB connector, which is connected to a vehicle's USB port.

However, vehicle USB ports can be a bit noisy, so we need to filter out this noise before it reaches the audio circuitry. A common approach is to use a PI filter.

### Avoiding Ferrite Beads

Many PI filter designs online utilize a ferrite bead inductor. However, I've read [here](https://electronics.stackexchange.com/a/649064/428232) that ferrite beads can actually amplify noise at certain frequencies and are not recommended for new designs, regardless of how popular they are.

Instead, I decided to use a `MLP2012H2R2MT0S1`, 2.2 μH inductor in a small 0805 package rated at 1 amps. This type of inductor is less prone to amplifying noise compared to the ferrite bead.

### Calculating the Capacitor Values

I used [this video](https://www.youtube.com/watch?v=Q2xXRtFi8rc) to calculate the values of the capacitors. I spent a lot of time researching to find the best values, but then I came across a post on the Electrical Engineering Stack Exchange that made me realize the exact values of the capacitors don't matter that much, as long as they're in the right ballpark.

Be carefull about the input capacitors because the maximum capacitance of a USB device is restricted by the specification to avoid voltage droop at the USB port, so only a 10 uF can be connected at a time. However, I've placed more than 10 uF in parallel (as you can see in the scheme below) in order to increase the filtering. I can do that without violating the USB specification because I have inrush current limiting IC connected to the VBUS line (see my older blog post about choosing components).

### The Final PI Filter Design

So, here is the PI filter I ended up with:

// TODO: add schematic

This filter should effectively remove the noise from the vehicle's USB port, providing a clean 5V power supply for the audio circuitry.

You may ask why there are multiple 0.24 Ohm series resistors? The resistors can provide additional damping and help with stability, but they are not essential for the basic noise filtering functionality of the PI filter. Here is a [good video](https://www.youtube.com/watch?v=ylfaaEp9iMo) from MicroType Engineering that explains the benefits of adding series resistors to a PI filter. This video helped a lot.
