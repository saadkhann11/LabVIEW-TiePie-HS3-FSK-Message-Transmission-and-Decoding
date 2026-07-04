# GitHub Upload Guide

## Recommended Repository Name

```text
labview-tiepie-hs3-fsk-message-transmission
```

## Repository Description

```text
LabVIEW project for FSK message generation, TiePie HS3 arbitrary waveform transmission, CH1 acquisition, and frequency-energy based decoding back into text.
```

## Before Uploading

1. Copy your actual LabVIEW VIs into the `labview/` folder:

```text
TiePie_acq_gen.vi
Waveform Gen.vi
Decode.vi
```

2. Decide whether to upload vendor files.

Vendor files such as `hs3.dll`, `hs3f8.hex`, and `hs3f12.hex` may have redistribution restrictions. If you are unsure, do not upload them. Keep them local and explain the requirement in `vendor/README.md`.

3. Add screenshots if desired:

```text
assets/front_panel.png
assets/block_diagram.png
assets/test_result.png
```

## Upload Using GitHub Website

1. Create a new GitHub repository.
2. Use the recommended repository name.
3. Add the repository description.
4. Upload all files from this folder.
5. Commit changes.
6. Open README.md and verify diagrams display correctly.

## Upload Using Git Command Line

```bash
git init
git add .
git commit -m "Initial commit: LabVIEW TiePie HS3 FSK message transmission project"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/labview-tiepie-hs3-fsk-message-transmission.git
git push -u origin main
```

## Suggested GitHub Topics

```text
labview
fsk
tiepie
hs3
signal-processing
waveform-generator
data-acquisition
instrumentation
ascii
```
