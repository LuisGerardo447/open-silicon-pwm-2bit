<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

The 2-Bit Digital PWM Modulator is a combinational logic circuit that generates a digital pulse-width-modulation output based on two binary inputs: phase and duty cycle.

The circuit uses four input pins:

- `ui[0]`: Phase bit 0 (P0)
- `ui[1]`: Phase bit 1 (P1)
- `ui[2]`: Duty bit 0 (D0)
- `ui[3]`: Duty bit 1 (D1)

The circuit compares the 2-bit phase value against the 2-bit duty value.

**PWM = 1 when Phase < Duty.**

The PWM output is available on `uo[0]`, and its logical complement is available on `uo[1]`.

The supported duty-cycle settings are:

| Duty (D1 D0) | Duty cycle | Output over phases 0–3 |
|---|---|---|
| 00 | 0% | 0000 |
| 01 | 25% | 1000 |
| 10 | 50% | 1100 |
| 11 | 75% | 1110 |

This first version uses an externally supplied phase value. A periodic phase counter is necessary to generate a continuous PWM waveform.

## How to test

1. Open the Wokwi project.
2. Set inputs D1 and D0 to select the desired duty cycle.
3. Change P1 and P0 sequentially through 00, 01, 10 and 11.
4. Observe the PWM output on `uo[0]`.
5. Verify that `uo[1]` is always the inverse of `uo[0]`.

For example, when D1 D0 = 10 (50% duty cycle), the expected output sequence is 1100.

Repeat the procedure for all four duty-cycle configurations.

## External hardware

No additional hardware is required for combinational logic simulation in Wokwi.

For continuous PWM operation on physical hardware, an external 2-bit phase counter or equivalent controller is required.
