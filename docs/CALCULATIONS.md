# Calculations

## Samples Per Bit

```text
samples_per_bit = sampling_rate × bit_duration
```

Example:

```text
sampling_rate = 50000 Hz
bit_duration = 0.05 s
samples_per_bit = 50000 × 0.05 = 2500 samples
```

## Useful Message Samples

```text
useful_samples = expected_characters × 8 × samples_per_bit
```

Example for `A`:

```text
expected_characters = 1
useful_samples = 1 × 8 × 2500 = 20000 samples
```

Example for `AB`:

```text
expected_characters = 2
useful_samples = 2 × 8 × 2500 = 40000 samples
```

## Padded Length

```text
padded_length = next_power_of_two(useful_samples)
```

Examples:

| Message | Useful Samples | Padded Length |
|---|---:|---:|
| A | 20000 | 32768 |
| AB | 40000 | 65536 |
| ABCD | 80000 | 131072 |

## Generator Wait Time

```text
wait_ms = 1000 × padded_length / sampling_rate
```

Example for `A`:

```text
wait_ms = 1000 × 32768 / 50000 = 655.36 ms
```

Example for `AB`:

```text
wait_ms = 1000 × 65536 / 50000 = 1310.72 ms
```

## U16 Conversion

```text
U16_value = 32768 + 30000 × sine_signal
```

Where:

- `32768` is the center value.
- `30000` gives safe headroom.
- `sine_signal` is normally between -1 and +1.

## Decoder Energy

```text
E0 = Sum(signal × sin_ref_f1)^2 + Sum(signal × cos_ref_f1)^2
E1 = Sum(signal × sin_ref_f2)^2 + Sum(signal × cos_ref_f2)^2
```

```text
E1 > E0 -> bit 1
E1 <= E0 -> bit 0
```
