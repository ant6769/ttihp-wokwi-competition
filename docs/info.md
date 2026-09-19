<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This project simulates a simplified digital heart-rate monitor. Pressing the
Pulse button (ui_in[0]) represents one detected heartbeat, similar to how a
real pulse sensor would send one pulse per heartbeat. Each press increments
a 4-bit counter, shown on uo_out[3:0]. If the count reaches or exceeds a set
threshold (12 pulses), the Alarm output (uo_out[7]) goes high, simulating a
tachycardia (high heart rate) alert. The Reset button (ui_in[1]) clears the
counter back to zero.

## How to test

1. Press the Reset button to clear the counter to 0.
2. Press the Pulse button repeatedly, one press per simulated heartbeat.
3. Watch the binary count on uo_out[3:0] increase with each press.
4. Once the count reaches the threshold (12), confirm the Alarm output
   (uo_out[7]) goes high.
5. Press Reset again and confirm the count returns to 0 and the alarm clears.

## External hardware

None — this project uses only the chip's onboard input and output pins. No external sensors, displays, or PMODs required.
