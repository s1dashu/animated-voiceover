# 即梦 CLI 执行路径

## 支持状态与权威来源

本 skill 已完成即梦 CLI 的命令、输入模式、参数约束、异步任务与下载流程文档适配，尚未完成付费生成和完整作品的端到端实作验证。只在用户明确选择即梦，或宿主项目已有可用的即梦环境时进入本路径；不根据 LibTV 或 Higgsfield 命令猜测或直译参数。

权威来源按以下顺序使用：

1. [即梦 CLI 使用指南](https://bytedance.larkoffice.com/wiki/FVTwwm0bGiishxkKOoScdHR2nsg)；该页面可能要求字节／飞书账号权限。
2. 当前安装版本的 `dreamina --help`、`dreamina <command> --help` 与 `dreamina version`。
3. 生成命令自身列出的模型、参数组合和服务端实际返回。

本文命令快照核对于 2026-08-02；当时本机官方二进制为 commit `46b5b0e`，构建时间为 `2026-06-03T19:39:25Z`。版本号、模型名和约束会变化，正式调用前必须重新读取当前帮助。官方指南无法访问时，可以依据已安装官方 CLI 的当前帮助执行；CLI 不存在或帮助信息不足时停止。

## 安装、版本与登录

官方帮助没有公开安装或升级子命令，安装与更新只遵循上述官方指南，不在本 skill 固化未经验证的下载地址或包管理命令。

```bash
command -v dreamina
dreamina version
dreamina --help
```

CLI 使用 OAuth Device Flow：

```bash
dreamina login
dreamina login --headless
dreamina login checklogin --device_code=<device_code> --poll=30
```

- `dreamina login` 会输出 `verification_uri`、`user_code` 和 `device_code`，并等待授权完成。
- 无界面环境使用 `--headless`，再将该次输出的 `device_code` 传给 `login checklogin`；不得复用旧设备码。
- `dreamina logout` 只清除本地 OAuth 登录状态，不删除任务和配置。
- 登录失效时使用 `dreamina relogin` 或 `dreamina relogin --headless`，不在日志中保存令牌、设备码或其他认证材料。
- 正式生成前可用 `dreamina user_credit` 检查额度；所有生成操作都会消耗 credits。

## 会话与作品隔离

即梦用 session 组织生成历史。所有生成命令都接受 `--session=<id>`；`0` 是不可重命名、不可删除的默认会话。

```bash
dreamina session create "<作品名>"
dreamina session list -n 100
dreamina session search "<作品名>"
dreamina session rename <session_id> "<新名称>"
dreamina session delete <session_id>
```

正式作品优先创建独立 session，记录实际 `session_id`，并在每次生成时显式传入。名称为去除首尾空格后的 1–50 个字符。删除是服务端软删除，历史会移回默认 session，但仍属于外部状态变更；只有用户明确要求时才执行。

## 生成模式

| 任务 | 命令 | 本地素材与主要边界 |
| --- | --- | --- |
| 文生图 | `dreamina text2image` | 无输入素材；模型 `3.0`–`5.0`，具体组合以当前帮助为准 |
| 图生图 | `dreamina image2image` | `--images` 传 1–10 张本地图；当前支持 `2k`、`4k` |
| 图片放大 | `dreamina image_upscale` | 一张 `--image`；`2k` 可用于非 VIP，`4k`/`8k` 需要 VIP |
| 文生视频 | `dreamina text2video` | 无参考素材；适合纯文字视频 |
| 单图生视频 | `dreamina image2video` | 一张首帧图；比例由输入图推断 |
| 首尾帧视频 | `dreamina frames2video` | `--first` 与 `--last` 各一张；比例由首帧推断 |
| 智能多帧 | `dreamina multiframe2video` | 2–20 张图；只负责多帧叙事，不是全能参考 |
| 全能参考视频 | `dreamina multimodal2video` | 混合图片、视频、音频；本项目人物与音色参考的主要映射 |

生成命令会自动上传其本地输入文件。当前 CLI 没有独立素材上传、素材列表或可复用远程素材 ID 的公开命令；不能假设一次上传可供后续任务复用。每次任务记录本地源文件、素材顺序、完整命令和返回的 `submit_id`。

## Seedance 2.0 参数映射

### 纯文字、单图与首尾帧

```bash
dreamina text2video \
  --session=<session_id> \
  --prompt="<视频 Prompt>" \
  --model_version=seedance2.0fast \
  --duration=15 \
  --ratio=16:9 \
  --video_resolution=720p

dreamina image2video \
  --session=<session_id> \
  --image=./人物.png \
  --prompt="<视频 Prompt>" \
  --model_version=seedance2.0fast \
  --duration=15 \
  --video_resolution=720p

dreamina frames2video \
  --session=<session_id> \
  --first=./首帧.png \
  --last=./尾帧.png \
  --prompt="<视频 Prompt>" \
  --model_version=seedance2.0fast \
  --duration=15 \
  --video_resolution=720p
```

- 当前视频模型值为 `seedance2.0`、`seedance2.0fast`、`seedance2.0_vip`、`seedance2.0fast_vip`。
- Seedance 2.0 系列当前支持 4–15 秒。`text2video` 支持 `1:1`、`3:4`、`16:9`、`4:3`、`9:16`、`21:9`；单图和首尾帧模式不接受 `--ratio`。
- 只有 `seedance2.0_vip` 的当前帮助明确支持 `720p` 或 `1080p`；其余值只支持 `720p`。
- `text2video` 和 `frames2video` 的当前默认模型是 `seedance2.0fast`。正式任务仍显式传模型、时长、比例（命令支持时）和分辨率，不依赖默认值。

### 全能参考

人物参考、视频参考或音色锚点需要混合输入时使用 `multimodal2video`，它对应网页端“全能参考”（旧称 `ref2video`）：

```bash
dreamina multimodal2video \
  --session=<session_id> \
  --image ./人物1.png \
  --image ./人物2.png \
  --audio ./统一音色.wav \
  --prompt="<当前片段的准确旁白与完整分镜 Prompt>" \
  --model_version=seedance2.0fast \
  --duration=15 \
  --ratio=16:9 \
  --video_resolution=720p
```

当前硬约束：

- 至少提供一张图片或一段视频；不能只传音频。
- 图片最多 9 份、视频最多 3 份、音频最多 3 份；音频必须为 2–15 秒。
- `--image`、`--video`、`--audio` 均按素材职责顺序重复传入，不使用逗号拼成一个参数。
- 支持的模型、比例、时长和分辨率与上文 Seedance 2.0 约束一致。
- 当前帮助未公开 `modeType` 或与 LibTV `mixed2video` 等价的参数；使用本命令本身表示全能参考，不自行补造输入模式。
- 当前帮助也没有 `enableSound`、`generate_audio` 或等价声音开关。需要明确控制有声生成的宿主项目，在官方 CLI 提供可验证参数前不能宣称这一要求已满足；应停止并说明能力缺口。

当前片段的准确旁白只写在本次 Prompt 中。音频输入只承担音色参考职责，不复述样本原台词。不得为满足“至少有视觉输入”的校验连接无关图片或视频。

### 智能多帧

`multiframe2video` 不接受模型与分辨率覆盖。两张图可使用 `--prompt` 和 `--duration`；三张及以上图片必须为 N 张图提供 N−1 个 `--transition-prompt`，并可提供相同数量的 `--transition-duration`。每段时长为 0.5–8 秒，总时长至少 2 秒。它不替代全能参考，也不用于音色锚点。

## 异步任务、查询与下载

所有生成任务都是异步任务。`--poll=N` 只在提交后按 1 秒间隔短暂等待 N 秒；超时后仍使用返回的 `submit_id` 继续查询，不重复提交：

```bash
dreamina multimodal2video <其余参数> --poll=30
dreamina query_result --submit_id=<submit_id>
dreamina query_result --submit_id=<submit_id> --download_dir="<作品绝对路径>/video"
```

任务审计可使用：

```bash
dreamina list_task --limit=100 --offset=0
dreamina list_task --submit_id=<submit_id>
dreamina list_task --gen_status=success
dreamina list_task --gen_task_type=<实际任务类型>
```

- 记录提交时的完整参数、`session_id`、`submit_id`、当前返回的状态、结果媒体地址与错误原文。
- 只有成功终态才允许下载并进入下一步；失败、无历史或结果媒体缺失时保留原始输出并停止。
- 使用 `--download_dir` 让官方 CLI 下载结果。下载后检查目标文件存在且非空，再按宿主项目规则命名；不得把查询成功等同于文件已经落盘。
- 当前 CLI 没有视频拼接命令。若宿主项目要求所有平台内部生成与最终拼接都必须由所选 CLI 完成，即梦路径在拼接步骤停止；只有宿主项目另行允许本地拼接时，才转入已确认的本地拼接能力。

## 已知前置条件与失败条件

- 部分高内容安全风险模型首次使用前会返回 `AigcComplianceConfirmationRequired`。此时必须由用户在 Dreamina Web 完成官方授权，再重试原任务；不得绕过确认或静默换模型。
- 官方指南不可访问且当前机器没有官方 `dreamina`，或当前帮助无法确认所需参数时停止。
- 未登录、额度不足、目标 session 不可访问、素材数量／格式／时长不合规时停止。
- 需要纯音频参考但没有有效视觉输入时停止，不连接无关素材绕过校验。
- 项目要求显式声音开关、可复用远程素材节点或 CLI 内视频拼接时，当前版本能力不足，明确报告缺口。
- 不把 `--poll` 超时当成生成失败，也不因超时重新提交；继续查询同一 `submit_id`。
