<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This project is a simplified digital heart-rate monitor. Flipping the Pulse
switch (ui_in[0]) from off to on represents one detected heartbeat, similar
to how a real pulse sensor sends one pulse per heartbeat. Each on-flip
increments a 4-bit binary counter, built from four D flip-flops chained
together (each flip-flop toggles its own state every time it receives a
pulse from the previous stage, creating a ripple counter). The count is
shown in binary on uo_out[3:0], where uo_out[0] is the least significant
bit and uo_out[3] is the most significant bit.

An AND gate continuously checks bits 3 and 2 of the count (uo_out[3] and
uo_out[2]). These two bits are only both high at the same time when the
count is 12 or greater (binary 1100 through 1111), so this single gate
acts as a threshold alarm: uo_out[7] goes high once the simulated pulse
count reaches 12, representing a simplified tachycardia (high heart rate)
warning.

The chip's built-in reset (RST_N) clears the entire design, including the
counter, back to zero.


## How to test

1. Start the simulation. The counter may power on with an arbitrary
   initial value (this is expected flip-flop startup behavior).
2. Flip the Pulse switch (ui_in[0]) from off to on, then back to off.
   This is one simulated pulse. Repeat this on-off cycle to register
   more pulses.
3. After each on-flip, observe uo_out[3:0] — the binary count should
   advance by one with every pulse (wrapping back to 0 after 15).
4. Continue pulsing until the count reaches 12 (binary 1100) and confirm
   uo_out[7], the alarm output, goes high, and confirm it turns back off
   once the count drops back below 12 (after wraparound).

Note: in this simulation, the counter's initial power-on value may be
arbitrary rather than zero, which is normal flip-flop startup behavior;
the counter still increments correctly from whatever value it starts at.
## External hardware

None — this project uses only the chip's onboard input and output pins. No external sensors, displays, or PMODs required.
