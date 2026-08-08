# Higgsfield CLI 执行路径

## 支持状态与权威来源

本 skill 已完成 Higgsfield CLI 的安装、认证、workspace、实时模型 schema、素材上传、生成、任务跟踪和 Seedance 2.0 参数映射，尚未完成付费生成和完整作品的端到端实作验证。只在用户明确选择 Higgsfield，或宿主项目已有可用环境时进入本路径；不根据 LibTV 或即梦命令猜测或直译参数。

权威来源：

- [Higgsfield CLI 官方仓库](https://github.com/higgsfield-ai/cli)
- [官方模型参数表](https://github.com/higgsfield-ai/cli/blob/main/MODELS.md)
- [最新正式版本](https://github.com/higgsfield-ai/cli/releases/latest)
- 当前安装版本的 `higgsfield --help`、`higgsfield <command> --help`、`higgsfield model get <job_type>` 与服务端返回

本文命令快照核对于 2026-08-02，最新 release 为 `v1.1.20`（2026-07-27 发布）。仓库文档只是快照；模型参数与枚举以正式执行时 `model list/get` 的实时输出为准。

## 安装、更新与命令名

macOS/Linux：

```bash
curl -fsSL https://raw.githubusercontent.com/higgsfield-ai/cli/main/install.sh | sh
brew install higgsfield-ai/tap/higgsfield
```

跨平台 npm：

```bash
npm install -g @higgsfield/cli
```

也可从 release 下载对应系统与架构的压缩包。安装属于用户环境变更；只有用户明确要求时执行。curl 安装器默认安装主命令 `higgsfield` 和别名 `higgs`；只有 `hf` 未被其他工具占用时才创建 `hf`，因此文档与自动化统一使用 `higgsfield`。

```bash
command -v higgsfield
higgsfield version
higgsfield --help
```

更新必须沿用原安装方式：重新运行官方安装脚本、`brew update && brew upgrade higgsfield`，或 `npm install -g @higgsfield/cli@latest`。需要复现时按官方文档固定 tag/version，不把“最新”当成可复现版本。

## 认证、账户与 workspace

```bash
higgsfield auth login
higgsfield account status
higgsfield workspace list
higgsfield workspace set <workspace_id>
higgsfield workspace status
```

- `auth login` 使用浏览器 OAuth 2.0 PKCE。`auth logout` 删除本地 access token。
- `auth token` 会把当前 access token 打印到终端；正常工作流不调用、不记录，也不把它放入命令、Prompt 或日志。
- `account status` 用于确认账户、方案与 credits；生成前确认额度满足任务。
- workspace 决定后续请求的计费与资源上下文。正式作品显式记录 `workspace_id`，并用 `workspace status` 复核；不要依赖可能被其他任务改写的旧选择。
- `workspace unset` 会返回私人账户上下文，只在用户明确要求改变计费上下文时执行。

## 实时模型与参数 schema

先发现当前 catalog，再读取目标模型的真实参数：

```bash
higgsfield model list --video
higgsfield model list --image
higgsfield model get seedance_2_0
higgsfield model get seedance_2_0 --json
```

模型生成统一使用 `job_type`，不是 UI 展示名：

```bash
higgsfield generate create <job_type> --<param> <value>
```

每次正式生成和重生成前都重新执行 `model get <job_type>`，确认必填项、默认值、枚举、素材数量和组合约束。本文只维护已经核对的映射，不用静态表覆盖实时 schema。

## 素材上传与引用

独立上传并取得媒体 ID：

```bash
higgsfield upload create ./人物.png --json
higgsfield upload create ./音色.wav --json
higgsfield upload list --image --size 50 --json
higgsfield upload list --audio --size 50 --json
```

生成命令的媒体参数接受 upload UUID、已有 job ID 或本地路径；传本地路径时 CLI 会自动上传：

- `--image-references`，短别名 `--image`
- `--video-references`，短别名 `--video`
- `--audio-references`，短别名 `--audio`
- `--start-image`
- `--end-image`

正式批量任务优先显式上传并记录返回 ID，避免同一人物或音色在每个片段被重复上传且难以追踪。每份素材记录本地源文件、类型、上传 ID、workspace 和用途；不得把一个 workspace 的 ID 假定为另一 workspace 可用。

## Seedance 2.0 映射

当前官方 job types 为 `seedance_2_0` 与 `seedance_2_0_mini`。完整模型示例：

```bash
higgsfield generate create seedance_2_0 \
  --prompt "<当前片段的准确旁白与完整分镜 Prompt>" \
  --image <人物1_upload_id> \
  --audio <统一音色_upload_id> \
  --aspect_ratio 16:9 \
  --duration 15 \
  --resolution 720p \
  --mode std \
  --bitrate_mode standard \
  --genre auto \
  --generate_audio true \
  --wait \
  --json
```

`seedance_2_0` 在 v1.1.20 文档中的参数为：

- `--aspect_ratio`：`auto`、`16:9`、`9:16`、`4:3`、`3:4`、`1:1`、`21:9`；默认 `16:9`。
- `--duration`：整数；具体允许范围以实时 schema 与服务端校验为准，不能只凭本文推断。
- `--resolution`：`480p`、`720p`、`1080p`、`4k`；默认 `720p`。
- `--mode`：`std` 或 `fast`；默认 `std`。`fast` 只支持 `480p`/`720p`，`1080p`/`4k` 必须使用 `std`。
- `--bitrate_mode`：`standard` 或 `high`；默认 `standard`。
- `--genre`：`auto`、`action`、`horror`、`comedy`、`noir`、`drama`、`epic`；默认 `auto`。
- `--generate_audio`：布尔值；默认 `true`。正式任务仍显式传值，不依赖默认。
- 图片参考（含首尾帧）最多 9 份，视频最多 3 份，音频最多 3 份；图片、视频、音频合计最多 12 份。
- 只要使用音频参考，就必须同时提供至少一份图片、视频、首帧或尾帧；不得连接无关视觉素材绕过校验。

`seedance_2_0_mini` 当前只支持 `480p`/`720p`，没有 `--mode` 参数，其余参考数量边界相同。模型选择必须由用户要求、成本与实时能力决定，不静默从完整模型降级到 Mini。

Higgsfield 没有暴露 LibTV 的 `modeType` 名称。图片、视频与音频参考直接映射到模型媒体参数；不要自行添加 `mixed2video`、`audio2video` 等不存在的 flag。当前片段的准确旁白只来自本次 Prompt，音频参考只承担音色职责。

## 创建、等待与任务审计

不等待的提交会返回 job ID；后续只查询同一任务，不因本地等待超时而重复生成：

```bash
higgsfield generate create seedance_2_0 <参数> --json
higgsfield generate get <job_id> --json
higgsfield generate wait <job_id> --timeout 20m --interval 5s --json
higgsfield generate list --video --size 50 --json
```

也可在创建时使用 `--wait`；官方默认最长等待 10 分钟、轮询间隔 3 秒，可通过 `--wait-timeout` 和 `--wait-interval` 调整。`generate wait` 对应参数名为 `--timeout` 和 `--interval`，两组名称不要混用。

记录 CLI 版本、workspace、job type、完整参数、上传 ID、job ID、服务端原始状态、结果 URL 和错误输出。只有成功终态且结果 URL 存在时才进入交付；保留服务端原始状态字符串，不自行归一化成虚构状态。

## 结果下载与拼接边界

当前官方 CLI 会在 `--wait`、`generate wait` 或 `generate get` 中返回结果 URL，但 v1.1.20 没有通用 `download` 命令。由此产生两个明确边界：

1. 如果宿主项目允许根据 CLI 返回的已认证结果 URL 使用普通下载工具落盘，可以在核对 URL 与 job ID 后下载，并验证文件存在且非空；下载步骤不是 Higgsfield CLI 原生命令，必须在项目记录中如实标注。
2. 如果宿主项目要求生成平台结果必须由所选官方 CLI 下载，则 Higgsfield 路径在获得结果 URL 后停止，不能宣称已完成落盘。

Higgsfield 提供 `explainer_video` assembler，但它要求至少两组“视频 job + 可选音频 job”，主要服务于官方 Seed Audio + Gemini Omni 的 explainer 流程。当前本 skill 的旁白动画使用 Seedance 直接生成片内声音，不使用 Seed Audio，也没有独立 audio job 与每个片段配对，因此不得把 `explainer_video` 当成通用视频拼接器。`video_explainer` 是另一个服务端整片工作流，同样不替代本 skill 已确认的逐片段 Prompt、人物参考和音色路线。

当前 CLI 没有已验证的通用视频串接命令。宿主项目要求由所选 CLI 完成最终拼接时，Higgsfield 路径在拼接步骤停止；只有项目另行允许本地拼接时，才转入已确认的本地能力。

## 失败条件

- 未安装、版本无法确认、OAuth 失效、credits 不足或 workspace 不正确时停止。
- `model get` 无法返回目标 job type 或所需参数、模型已下线、枚举不支持用户要求时停止，不静默换模型或降级。
- 音频参考缺少有效视觉输入，或任一素材数量超过实时 schema 时停止。
- 等待超时不等于任务失败；继续查询同一 job ID。服务端失败、结果 URL 缺失或 URL 无法取得媒体时保留原始日志并停止。
- 宿主项目要求 CLI 原生下载或通用片段拼接时，当前版本能力不足，明确报告缺口。
- 报错时附上 `higgsfield version`、脱敏后的完整命令、workspace、job ID、状态与 stderr；绝不附 access token。
