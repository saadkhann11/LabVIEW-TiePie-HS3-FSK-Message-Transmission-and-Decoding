# Troubleshooting

| Problem | Likely Reason | Fix |
|---|---|---|
| Decoder works with generated waveform directly but not through hardware | Hardware path or acquisition timing issue | Verify direct sine loopback first |
| Only noise appears on CH1 | Generator not outputting, wrong mode, wrong range, or wrong trigger | Use sine mode test before FSK |
| Clean sine appears but FSK decodes wrong | Acquisition is not aligned with waveform start | Arm acquisition before generation and use Gen trigger |
| One character works but two characters fail | Record length, postsamples, wait time, or expected characters not updated | Recalculate all values from current message length |
| Random message appears during sine test | Decoder is being applied to a plain sine wave | Ignore decoded message during sine-only testing |
| FSK signal repeats and decoder captures from middle | Generator running continuously | Use one-shot timing and stop generator after calculated wait time |
| DLL call fails | DLL path or function prototype problem | Confirm `hs3.dll` is in expected location and Call Library Function Node settings are correct |
| Waveform clips | U16 scaling or generator amplitude too high | Keep U16 scaling headroom and reduce amplitude |
| Bit errors at higher frequencies | Sampling rate too low or bit duration too short | Increase sampling rate or bit duration |
| CH1 graph looks flat | Output disabled or range too large | Enable generator output and reduce CH1 range |

## Debugging Order

1. Test hardware with a simple sine wave.
2. Confirm CH1 receives the sine correctly.
3. Generate FSK for one character only.
4. Decode only the useful samples.
5. Test two characters.
6. Test longer messages.
7. Only then test alternate frequencies, bit durations, or acoustic paths.
