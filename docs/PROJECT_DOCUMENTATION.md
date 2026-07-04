# Project Documentation

## Title

LabVIEW TiePie HS3 FSK Message Transmission and Decoding

## Purpose

This project demonstrates digital message transmission using frequency shift keying. A text message is encoded into binary bits, each bit is represented by one of two sine-wave frequencies, the resulting waveform is transmitted using the TiePie HS3 generator, and the same signal is acquired on CH1 and decoded back into text.

## Scope

The implemented and documented setup uses a direct hardware loopback path:

```text
TiePie HS3 Generator OUT -> TiePie HS3 CH1
```

This loopback path is recommended because it validates the LabVIEW encoding, waveform generation, TiePie generator configuration, acquisition timing, and decoder logic without acoustic noise or extra external hardware.

## Implemented Behavior

1. User enters a transmission message.
2. Message is converted to ASCII bytes.
3. Each byte is converted into 8 bits.
4. Each bit is mapped to either Frequency 1 or Frequency 2.
5. The complete FSK waveform is built from sine-wave segments.
6. The waveform is converted from DBL values into U16 samples for TiePie arbitrary waveform memory.
7. The waveform is padded to the next power-of-two length.
8. TiePie generator outputs the waveform.
9. TiePie CH1 acquires the signal.
10. Decoder checks each bit window and compares frequency energy.
11. Bits are reconstructed into bytes and converted into a received text message.

## Main VI and SubVI Roles

| File | Role |
|---|---|
| `TiePie_acq_gen.vi` | Main controller VI for front panel, generator, acquisition, and decoder integration. |
| `Waveform Gen.vi` | Converts message to bits and builds the FSK waveform. |
| `Decode.vi` | Converts acquired waveform back into decoded text. |

## Reference Diagrams

See the `assets/` folder for clean diagrams:

- `overall_implementation_flow.png`
- `tiepie_loopback_connection.png`
- `labview_vi_architecture.png`
- `generation_chain.png`
- `acquisition_chain.png`
- `decoder_frequency_energy.png`
