# 音频剥离与格式转换指南

## 目标格式

将已确认的片段 1 转换为 LibTV 与 Seedance 已验证可用的纯音频：

- 容器：WAV
- 编码：16-bit little-endian PCM（`pcm_s16le`）
- 采样率：48kHz
- 声道：双声道

M4A 上传节点曾被 Seedance 拒绝；未重新验证前不要使用。转换完成后通过 LibTV CLI 上传 WAV，不直接把视频作为后续片段的音色参考。

## Windows

使用 PowerShell 安装 FFmpeg：

```powershell
winget install --id Gyan.FFmpeg -e
```

重新打开 PowerShell，用以下命令剥离并转换音频：

```powershell
ffmpeg -hide_banner -n -i ".\片段1.mp4" -map 0:a:0 -vn -c:a pcm_s16le -ar 48000 -ac 2 ".\片段1-音色参考.wav"
```

`-map 0:a:0` 要求输入文件存在第一条音轨；没有音轨时直接报错。`-n` 在目标文件已经存在时停止，避免静默覆盖。

## macOS

macOS 可以使用系统自带的 `afconvert`：

```bash
afconvert "./片段1.mp4" -o "./片段1-音色参考.wav" -f WAVE -d LEI16@48000 -c 2
```

也可以安装 FFmpeg，并使用与 Windows 相同的 FFmpeg 参数：

```bash
brew install ffmpeg
ffmpeg -hide_banner -n -i "./片段1.mp4" -map 0:a:0 -vn -c:a pcm_s16le -ar 48000 -ac 2 "./片段1-音色参考.wav"
```

## Linux

通过当前发行版的包管理器安装 FFmpeg，再运行：

```bash
ffmpeg -hide_banner -n -i "./片段1.mp4" -map 0:a:0 -vn -c:a pcm_s16le -ar 48000 -ac 2 "./片段1-音色参考.wav"
```

## 验证输出

上传前使用 `ffprobe` 检查实际音频规格：

```bash
ffprobe -v error -select_streams a:0 -show_entries stream=codec_name,sample_rate,channels,bits_per_sample -of default=noprint_wrappers=1 "./片段1-音色参考.wav"
```

预期输出包含：

```text
codec_name=pcm_s16le
sample_rate=48000
channels=2
bits_per_sample=16
```

任一字段不符时停止上传并重新转换，不修改扩展名伪装格式。
