# Waveform Generation

## Generation Chain

```text
Transmission Message
    -> ASCII bytes
    -> Bit array
    -> Frequency selection per bit
    -> Sine-wave bit segments
    -> Concatenated waveform
    -> U16 conversion
    -> Padding
    -> TiePie arbitrary memory
```

## Text to Bits

A string is converted into a byte array. Each byte is split into 8 bits.

Example:

```text
Transmission Message = "A"
String to byte array = [65]
65 in binary = 01000001
```

## Sine Segment Generation

For each bit:

| Bit | Frequency Used |
|---:|---:|
| 0 | Frequency 1 |
| 1 | Frequency 2 |

The signal generator creates a sine segment for one bit duration, then all bit segments are concatenated.

## U16 Conversion

TiePie arbitrary memory expects unsigned 16-bit samples. The DBL sine wave is converted using:

```text
U16_value = 32768 + 30000 × sine_signal
```

The center value `32768` represents zero output. The scale value `30000` leaves headroom so the waveform does not clip at the U16 limits.

## Padding

The waveform is padded to the next power of two using the center value 32768.

Example for one character:

```text
sampling_rate = 50000 Hz
bit_duration = 0.05 s
samples_per_bit = 2500
useful_samples = 1 × 8 × 2500 = 20000
next_power_of_two = 32768
padding_samples = 12768
```

## TiePie Generator Mode

The FSK waveform should use arbitrary waveform output mode, not normal fixed sine DDS mode. In linear arbitrary mode, the generator frequency setting acts as the playback sampling clock.
