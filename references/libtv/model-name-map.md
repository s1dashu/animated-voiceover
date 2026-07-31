# LibTV Model Name Map

This file maps common user-facing model names to LibTV `modelName` and internal `modelKey` values.

## Rules

- This table is a snapshot returned by `libtv model search --type image|video|audio` on 2026-07-29, supplemented by names confirmed in real use.
- Pass LibTV `modelName`, not `modelKey`, to `libtv node ... -s model=...`.
- Use `modelKey` to identify a model precisely, query its schema, and trace logs.
- Some LibTV display names are localized. Entries marked `Resolve live by modelKey` intentionally omit the localized string so this English-only skill does not embed language-specific UI labels. Run live search and copy the exact returned `modelName`.
- `Seedance 2.0 Pro` and the full Seedance 2.0 model refer to LibTV `Seedance 2.0 VIP` / `star-video2`. Fast and Mini are separate models and must not be substituted silently.
- Catalog entries, display names, and schemas can change. Before production, run both `libtv model search` and `libtv model <modelName|modelKey>`. When live output differs, use the CLI result and update this file.

## Image Models

| Common name | LibTV `modelName` | `modelKey` |
| --- | --- | --- |
| GPT Image 2 | `Lib Image` | `lib-image-2` |
| Nano Banana Pro | `General image Pro` | `nebula-ultra` |
| Nano Banana 2 | `General image V2` | `nebula-2-flash` |
| Seedream 5.0 Pro | `Seedream 5.0 Pro` | `doubao-seedream-5-0-pro` |
| Midjourney V8.2 | Resolve live by `modelKey` | `mj-v8.2` |
| Midjourney V8.1 | Resolve live by `modelKey` | `mj-v8.1` |
| Midjourney V7 | Resolve live by `modelKey` | `mj-v7` |
| Midjourney Niji 7 | Resolve live by `modelKey` | `mj-niji7` |
| Seedream 4.6 | `Seedream 4.6` | `jimeng-4.6` |
| Seedream 5.0 Lite | `Seedream 5.0 Lite` | `seedream-5` |
| Seedream 4.5 | `Seedream 4.5` | `seedream-4.5` |
| Z-Image Turbo | `Z-image Turbo` | `z-image` |
| General Image | `General image` | `nebula-core` |
| Qwen Image | `Qwen Image` | `qwen` |
| Qwen Edit | `Qwen Edit` | `qwen-edit` |
| Seedream 4.0 | `Seedream 4.0` | `seedream-4` |

## Video Models

| Common name | LibTV `modelName` | `modelKey` |
| --- | --- | --- |
| Seedance 2.0 Pro / full | `Seedance 2.0 VIP` | `star-video2` |
| Seedance 2.0 Fast | `Seedance 2.0 Fast VIP` | `star-video2-fast` |
| Seedance 2.0 Mini | `Seedance 2.0 Mini` | `star-video2-mini` |
| Happy Horse 1.1 | `Happy Horse 1.1` | `happy-horse-1.1` |
| Happy Horse 1.0 | `Happy Horse 1.0` | `happy-horse-1` |
| Kling O3 | `Kling O3` | `kling-v3-omni` |
| Kling 3.0 Turbo | `Kling 3.0 Turbo` | `kling-v3-turbo` |
| Kling 3.0 | `Kling 3.0` | `kling-video-o3` |
| Wan 2.7 | `Wan 2.7` | `wanx2.7-video` |
| Kling O1 | `Kling O1` | `kling-video-o1` |
| Wan 2.6 | `Wan 2.6` | `wanxiang-v2-6` |
| Hailuo 2.3 Fast | `Hailuo 2.3 Fast` | `MiniMax-Hailuo-2.3-Fast` |
| Hailuo 2.3 | `Hailuo 2.3` | `MiniMax-Hailuo-2.3` |
| Seedance 1.5 Pro | `Seedance1.5 Pro` | `seedance-1.5-pro` |
| Seedance 1.0 Pro | `Seedance 1.0 Pro` | `doubao-seedance-pro` |
| Seedance 1.0 Lite | `Seedance 1.0 Lite` | `doubao-seedance-lite` |
| Kling 2.6 | `Kling 2.6` | `kling-v2-6` |
| Kling 3.0 Motion Transfer | Resolve live by `modelKey` | `kling-v3-motion-control` |
| Midjourney Video | `MJ Video` | `midjourney-video` |
| Hailuo 02 | `Hailuo 02` | `MiniMax-Hailuo-o2` |
| Vidu Q2 | `Vidu Q2` | `viduq2` |
| Vidu Q2 Pro | `Vidu Q2 Pro` | `viduq2-pro` |
| Vidu Q2 Turbo | `Vidu Q2 Turbo` | `viduq2-turbo` |
| Vidu Q3 Pro | `Vidu Q3 Pro` | `viduq3-pro` |
| OmniHuman 1.5 | `OmniHuman 1.5` | `omnihuman-1.5` |
| Kling 2.5 | `Kling 2.5` | `kling-v2-5-turbo-pro` |
| Kling 2.1 | `Kling 2.1` | `kling-2.1` |
| Wan 2.2 | `Wan 2.2` | `wanxiang-plus` |
| Wan 2.5 | `Wan 2.5` | `wanxiang-preview` |
| Pixverse V5.5 | `Pixverse V5.5` | `pixverse-v5.5` |
| Pixverse V5 | `Pixverse V5` | `pixverse-v5` |

## Audio Models

| Common name | LibTV `modelName` | `modelKey` |
| --- | --- | --- |
| Seed Audio 1.0 | `Seed Audio 1.0` | `seed-audio-1.0` |
| MiniMax Speech 2.8 HD | `Minimax-speech-2.8-hd` | `speech-2.8-hd` |
| MiniMax Speech 2.8 Turbo | `Minimax-speech-2.8-turbo` | `speech-2.8-turbo` |
| Eleven V3 | `Eleven V3` | `vocal-v3` |
| Eleven Music V3 | `Eleven Music V3` | `vocal-music` |
| Mureka V8 | `Mureka V8` | `mureka-8` |
