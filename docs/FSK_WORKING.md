# FSK Working Principle

## What is FSK?

FSK means Frequency Shift Keying. It is a digital modulation method where different frequencies represent digital bit values.

In this project:

```text
Bit 0 -> Frequency 1
Bit 1 -> Frequency 2
```

## Example: Character A

```text
A = ASCII decimal 65
65 = binary 01000001
```

With Frequency 1 = 2000 Hz and Frequency 2 = 4000 Hz:

| Bit | Frequency |
|---:|---:|
| 0 | 2000 Hz |
| 1 | 4000 Hz |
| 0 | 2000 Hz |
| 0 | 2000 Hz |
| 0 | 2000 Hz |
| 0 | 2000 Hz |
| 0 | 2000 Hz |
| 1 | 4000 Hz |

## Bit Duration

Each bit is transmitted for a fixed duration. Example:

```text
bit_duration = 0.05 s
```

This means every bit occupies 50 ms of waveform time.

## Frequency Selection Rule

The sampling rate must be higher than twice the highest frequency. For example, with Frequency 2 = 4000 Hz:

```text
Minimum theoretical sample rate > 8000 Hz
Recommended sample rate = 50000 Hz or higher
```

Using a higher sampling rate improves decoder stability.
