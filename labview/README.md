# LabVIEW Source Files

Place the project LabVIEW source files in this folder before uploading the final repository.

Expected files:

```text
TiePie_acq_gen.vi
Waveform Gen.vi
Decode.vi
```

## VI Roles

| VI | Role |
|---|---|
| `TiePie_acq_gen.vi` | Main VI. Controls message input, generation, acquisition, decoding, and display. |
| `Waveform Gen.vi` | SubVI that converts text to bits and generates the FSK waveform. |
| `Decode.vi` | SubVI that decodes acquired CH1 waveform data back into text. |

Keep the VI names consistent because the documentation refers to these names.
