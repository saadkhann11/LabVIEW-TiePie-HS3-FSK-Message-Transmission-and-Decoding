# Acquisition and Decoding

## Acquisition Chain

```text
TiePie CH1
    -> Record length configuration
    -> Trigger setup
    -> Sample frequency setup
    -> ADC_Start
    -> ADC_Ready wait
    -> Get CH1 voltage array
    -> Decode.vi
```

## Recommended Acquisition Settings

| Setting | Recommended Value |
|---|---|
| Active channel | CH1 |
| Record length | Padded waveform length |
| Postsamples | Same as record length |
| Trigger source | Gen |
| Coupling | DC |
| Sample frequency | Same as waveform generation rate |

## Why Record Length Matters

If record length is too short, the acquired waveform is incomplete. If it is too long or starts at the wrong time, padding or silence may be decoded as data. The safest approach is to use the generated padded waveform length and decode only the useful message sample region.

## Decoder Steps

1. Remove DC offset from CH1 waveform.
2. Calculate samples per bit.
3. Slice the waveform into bit windows.
4. Compare energy at Frequency 1 and Frequency 2.
5. Decide bit value for each window.
6. Group bits into 8-bit ASCII bytes.
7. Convert bytes to text.

## Frequency-Energy Method

For each bit window:

```text
E0 = Sum(signal × sin_ref_f1)^2 + Sum(signal × cos_ref_f1)^2
E1 = Sum(signal × sin_ref_f2)^2 + Sum(signal × cos_ref_f2)^2
```

Decision rule:

```text
If E1 > E0, decoded bit = 1
Else, decoded bit = 0
```

This method is phase-independent because both sine and cosine references are used.
