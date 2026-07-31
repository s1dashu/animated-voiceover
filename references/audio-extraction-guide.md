# Audio Extraction and Format Conversion Guide

## Target Format

Convert the approved Clip 1 into a pure-audio file validated with LibTV and Seedance:

- Container: WAV
- Codec: 16-bit little-endian PCM (`pcm_s16le`)
- Sample rate: 48 kHz
- Channels: stereo

Seedance previously rejected an uploaded M4A node. Do not use M4A until it has been revalidated. After conversion, upload the WAV through LibTV CLI. Do not attach the whole video as the voice reference for later clips.

## Windows

Install FFmpeg from PowerShell:

```powershell
winget install --id Gyan.FFmpeg -e
```

Reopen PowerShell, then extract and convert the audio:

```powershell
ffmpeg -hide_banner -n -i ".\clip-01.mp4" -map 0:a:0 -vn -c:a pcm_s16le -ar 48000 -ac 2 ".\clip-01-voice-reference.wav"
```

`-map 0:a:0` requires the first audio stream to exist and fails clearly if the input has no audio. `-n` stops when the destination already exists instead of overwriting it silently.

## macOS

Use the built-in `afconvert`:

```bash
afconvert "./clip-01.mp4" -o "./clip-01-voice-reference.wav" -f WAVE -d LEI16@48000 -c 2
```

Alternatively, install FFmpeg and use the same conversion settings as on Windows:

```bash
brew install ffmpeg
ffmpeg -hide_banner -n -i "./clip-01.mp4" -map 0:a:0 -vn -c:a pcm_s16le -ar 48000 -ac 2 "./clip-01-voice-reference.wav"
```

## Linux

Install FFmpeg with the package manager for the current distribution, then run:

```bash
ffmpeg -hide_banner -n -i "./clip-01.mp4" -map 0:a:0 -vn -c:a pcm_s16le -ar 48000 -ac 2 "./clip-01-voice-reference.wav"
```

## Validate the Output

Inspect the actual stream before upload:

```bash
ffprobe -v error -select_streams a:0 -show_entries stream=codec_name,sample_rate,channels,bits_per_sample -of default=noprint_wrappers=1 "./clip-01-voice-reference.wav"
```

Expected fields:

```text
codec_name=pcm_s16le
sample_rate=48000
channels=2
bits_per_sample=16
```

If any field differs, stop and convert the file again. Never disguise an incompatible format by changing only its extension.
