# LibTV CLI 执行路径

## 支持状态

LibTV CLI 是本 skill 当前唯一正式维护、实际验证最充分的图片、音频和视频生成路径。当用户没有指定工具且本地没有可用的多模态 CLI 时，优先建议安装 LibTV CLI；不未经用户同意擅自安装。

## 执行前置条件

1. 确认 `libtv` 已安装且可执行。
2. 确认已登录。
3. 确认当前工作区与画布绑定正确。
4. 解析并记录目标 `projectUuid`。
5. 实时查询目标模型、schema、输入模式、素材数量、文件格式、时长、画幅、分辨率和声音能力。

缺少任一前置条件时明确报错并停止，不静默切换其他工具。

## 模型与参数

- 仅在 LibTV 中，将 `GPT-Image-2` 解析为 `Lib Image`、`Nano Banana Pro` 解析为 `General image Pro`、`Midjourney` 解析为 `悠船`；其他 CLI 不得沿用。
- 给 `libtv node ... -s "model=..."` 传模型时，逐字使用 `libtv model search` 返回的 `matches[].modelName`，包括空格、大小写与标点；不改用 `modelKey`。
- 当前已验证的 Seedance 默认选择是 Seedance 2.0 Pro；LibTV 中对应 Seedance 2.0 VIP（`star-video2`）。正式调用仍以实时搜索与 schema 为准。
- 每次创建或重生成节点都显式传入实际 `duration`、`ratio`、`resolution`、`enableSound`、`count` 和 `modeType`，不继承旧画布、复制节点或模型默认值。
- 使用 Seedance 2.0 系列时，用户未明确要求高分辨率则显式使用 `720p`。用户要求 `1080p`、`4K` 或其他档位时，先以实时 schema 确认支持；不支持时停止，不静默降级。
- 时长、画幅、分辨率、声音开关、数量和 `modeType` 只通过 CLI 参数传递，不写进创作 Prompt。

## 参考素材与音色

- 平台内部的素材上传、节点连接、任务运行与生成结果下载全部通过官方 `libtv` 命令完成，不自行构造 HTTP 请求。
- LibTV 节点只在所属画布内有效。跨画布复用时，先通过 CLI 下载标准化本地文件，再通过 CLI 上传到目标画布。
- 音频只承担音色参考时，即使只连接一份音频，也一般显式使用实时 schema 支持的 `mixed2video`，不仅因只有音频就改用 `audio2video`。
- 平台要求有效视觉输入时，只连接当前片段真实需要的人物或视频参考，不为通过校验接入无关素材。

## 可追溯性与落盘

- 解析画布后，正式创建节点、生成、上传和下载命令都显式传入 `-p <projectUuid>`。
- 每次命令返回后核对实际 `projectUuid`、节点 ID、任务 ID、终态和资源 URL，并保留 stderr 与失败状态。
- 当前作品的独立视频片段和最终成片统一下载到 `<作品目录>/video/`，文件直接平铺并用补零编号排序，例如 `片段01.mp4`、`片段02.mp4`。
- 任一任务未返回成功终态，或节点 ID、任务 ID、资源 URL 缺失时，停止后续批量生成或拼接。
