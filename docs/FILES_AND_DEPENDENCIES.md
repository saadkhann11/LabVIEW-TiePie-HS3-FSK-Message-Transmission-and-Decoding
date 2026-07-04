# Files and Dependencies

## Project Source Files

| File | Required | Description |
|---|---|---|
| `TiePie_acq_gen.vi` | Yes | Main VI used to run the project. |
| `Waveform Gen.vi` | Yes | FSK waveform generation subVI. |
| `Decode.vi` | Yes | FSK decoding subVI. |

## TiePie Support Files

| File | Required | Notes |
|---|---|---|
| `hs3.dll` | Yes | Required by LabVIEW Call Library Function Nodes. |
| `hs3f8.hex` | Hardware dependent | TiePie support/firmware file. |
| `hs3f12.hex` | Hardware dependent | TiePie support/firmware file. |

## Reference Image

The `assets/project_file_list_screenshot.png` file shows the source and support files visible in the project folder.

## Redistribution Note

Do not upload vendor DLL/HEX files to a public repository unless redistribution is explicitly allowed. A safe practice is to document them in `vendor/README.md` and keep them local.
