# Software Architecture

## Main VI

`TiePie_acq_gen.vi` coordinates the full project:

```text
Front panel controls
    -> Waveform generation subVI
    -> TiePie generator DLL calls
    -> TiePie acquisition DLL calls
    -> Decoder subVI
    -> Received message display
```

## SubVIs

### Waveform Gen.vi

Responsible for:

- Reading the transmission message
- Converting text to ASCII bytes
- Splitting bytes into bits
- Mapping bits to Frequency 1 or Frequency 2
- Generating one sine segment per bit
- Concatenating all segments
- Converting DBL waveform to U16 format
- Padding the waveform to a power-of-two length

### Decode.vi

Responsible for:

- Receiving CH1 voltage data
- Removing DC offset
- Splitting waveform into bit windows
- Comparing frequency energy at Frequency 1 and Frequency 2
- Reconstructing bits
- Grouping bits into bytes
- Converting ASCII bytes back into text

## Important Control Flow

The acquisition length must be known before generation begins. Therefore the pre-calculation logic updates:

- No. of samples
- Postsamples
- Expected Characters

before the acquisition is armed.

## One-Shot Timing Rule

For a stable test:

```text
Calculate waveform length -> Arm acquisition -> Start generator -> Wait calculated time -> Stop generator -> Read data -> Decode
```
