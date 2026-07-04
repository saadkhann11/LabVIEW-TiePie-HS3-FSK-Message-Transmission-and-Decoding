# Hardware Connections

## Required Hardware

- TiePie HS3 instrument
- Computer running LabVIEW
- TiePie HS3 DLL/support files
- BNC/appropriate connection cable from generator output to CH1 input

## Direct Loopback Wiring

| Connection | Description |
|---|---|
| TiePie Generator OUT -> CH1 | Sends the generated FSK waveform directly into acquisition channel 1. |
| Common reference / ground | Ensures the generator and acquisition signal share the same reference. |

## Why Direct Loopback First?

Direct loopback is the most reliable way to verify the code. It removes microphone, speaker, amplifier, and environmental noise issues. Once the direct test works, the same FSK logic can be adapted to an acoustic or external transmission path.

## Recommended Initial Settings

| Setting | Recommended Value |
|---|---:|
| CH1 active | Enabled |
| CH1 coupling | DC |
| CH1 range | 2 V or suitable range |
| Generator amplitude | Around 1 V |
| Generator DC offset | 0 V |
| Trigger source | Gen |
| Sample frequency | Same as generation sampling rate |

## Safety Notes

- Do not exceed the input voltage rating of CH1.
- Start with a low amplitude signal.
- Verify a simple sine wave loopback before testing full FSK.
- Keep DLL and firmware files in the expected path for the LabVIEW Call Library Function Nodes.
