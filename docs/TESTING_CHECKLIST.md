# Testing Checklist

## Before Running

- [ ] TiePie HS3 is connected to the PC.
- [ ] TiePie drivers and support files are installed.
- [ ] `hs3.dll` path is correct for LabVIEW Call Library Function Nodes.
- [ ] Generator OUT is connected to CH1.
- [ ] CH1 coupling is set to DC.
- [ ] CH1 range is suitable for the generator amplitude.
- [ ] No other application is controlling the TiePie hardware.

## Basic Sine Test

- [ ] Configure generator in sine mode.
- [ ] Output a simple sine wave.
- [ ] Confirm clean sine wave appears on CH1 graph.
- [ ] Confirm amplitude and offset are reasonable.

## One Character FSK Test

- [ ] Set message to `A`.
- [ ] Use Frequency 1 = 2000 Hz.
- [ ] Use Frequency 2 = 4000 Hz.
- [ ] Use bit duration = 0.05 s.
- [ ] Use sampling rate = 50000 Hz.
- [ ] Confirm Expected Characters = 1.
- [ ] Confirm padded length is 32768 samples.
- [ ] Arm acquisition first.
- [ ] Start generation.
- [ ] Confirm Received Message shows `A`.

## Multi-Character Test

- [ ] Set message to `AB` or `ABCD`.
- [ ] Confirm Expected Characters updates automatically.
- [ ] Confirm No. of samples and Postsamples update from padded length.
- [ ] Confirm generator wait time updates from padded length.
- [ ] Confirm Received Message matches the input message.

## Final Validation

- [ ] Test at least three messages.
- [ ] Take screenshots of front panel input and received message.
- [ ] Record final settings in README or project report.
