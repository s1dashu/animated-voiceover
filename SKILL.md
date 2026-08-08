---
name: director
description: 导演并制作多类型视频，从创意、研究、剧本、视觉开发、人物与声音设计、分镜和生成 Prompt，一直推进到素材生成、任务追踪与交付。适用于 Storytime Animation、Animated Explainer 与开发中的 Visual Journalism，以及为未来微电影、短片、短剧、音乐视频等独立 Mode 建立制作方法。Storytime 与 Explainer 已完成实际作品验证，Visual Journalism 尚在实作验证中；尚未建立专属 Mode 的类型不得冒充已支持流程。
---

# director

`director` 是视频创作与制作的顶层导演 skill，不以动画、旁白或任何单一题材定义自身。它负责先判断作品类型和创作目标，再把任务路由到经过验证的 Mode、style、共享资产与执行工具。

## 核心架构

把每支视频拆成三层选择：

1. **Mode** 决定内容目标、叙事方式、素材结构、声音角色、写作重点和制作流程。
2. **Mode 专属 style 与共享资产** 决定视觉语言，并在需要时提供可跨 Mode 复用的人物参考与音色。
3. **Tool** 决定如何在用户选定的 CLI 平台上查询模型、上传素材、生成、跟踪、下载和拼接。

三者不互相替代。先选择 Mode，再从该 Mode 的 `styles/` 中选择 style 并确认共享资产，最后选择执行 CLI。

## Mode 选择与路由

用户已指定 Mode 时直接使用。未指定时，根据视频的核心驱动力推荐；无法判断时再询问作品主要由个人经历、知识解释、现实证据，还是人物行动与戏剧冲突驱动。不要因为当前已实现的 Mode 以旁白驱动为主，就把所有视频默认解释成动画解说。

- **[Storytime Animation](modes/storytime-animation/workflow.md)**（`storytime-animation`）：由第一人称讲述者与个人经历驱动，用动画重现自己、身边人或明确改编的故事。已完成首支五片段作品的生成与质量验证。
- **[Animated Explainer](modes/animated-explainer/workflow.md)**（`animated-explainer`）：使用旁白和动画，在一支短片中讲清楚一个概念、理论、人物思想、历史事件或知识主题。这就是重构前已经完成多期实作验证的原有工作流。
- **[Visual Journalism](modes/visual-journalism/workflow.md)**（`visual-journalism`）：研究并解释财经、时政、产业或其他现实议题，以证据、现实素材和论点驱动叙事，混合纪录片实拍、档案材料、地图、解释性动画与动态图表。当前已建立首轮候选工作流，尚未完成端到端实作验证。
选定 Mode 后，在任何采集、研究、写作、分镜或素材规划之前完整读取对应 `workflow.md` 及其指定的专属文档。不把 Animated Explainer 的旁白结构、字数、分镜、封面或纯动画切片流程默认套用到其他 Mode。

## 当前能力与扩展边界

当前只有上方列出的三个 Mode 属于已进入实现的制作能力，其中 Storytime Animation 与 Animated Explainer 已完成作品验证，Visual Journalism 仍是候选工作流。微电影、短片、短剧、音乐视频及其他类型属于 `director` 的计划扩展范围，但只有建立独立 Mode、完成真实作品验证并得到用户确认后，才能标记为可用或已验证。

用户要求尚未建立专属 Mode 的视频类型时，明确说明当前缺少该类型的专属工作流；可以与用户共同定义目标、输入、叙事结构、素材策略、质量门槛和验证作品，但不得静默套用 Animated Explainer 或 Storytime Animation。新增 Mode 应放入 `modes/<mode>/`，把类型专属流程、style 和 Prompt 方法留在该 Mode 内；只有真正跨类型复用的能力才提升到 `references/`。

声音是各 Mode 的创作选择，不是 `director` 的身份边界。未来 Mode 可以由对白、同期声、音乐、纯画面或多种声音结构驱动；只有当前 Mode 明确要求统一旁白或声音身份时，才进入音色锚点流程。

## Mode 专属 style 与共享参考资产

每个 style 默认只属于一个 Mode，并与该 Mode 的内容目标、素材结构和 Prompt 方法一起验证。不向用户展示其他 Mode 的 style，也不在未验证时默认跨 Mode 混用。只有一个 style 已经通过多个 Mode 的实际作品验证并得到用户确认后，才将它提升为明确的跨 Mode 共享 style。

**Storytime Animation**

- [清爽白色圆身 Storytime 动画](modes/storytime-animation/styles/clean-white-character-storytime-animation.md)

**Animated Explainer**

- [电影感 3D 动画](modes/animated-explainer/styles/cinematic-3d-animation.md)
- [黏土定格动画](modes/animated-explainer/styles/clay-stop-motion.md)
- [忧郁蓝调简笔画风格](modes/animated-explainer/styles/melancholic-blue-simple-line-animation.md)
- [柔和彩铅萌趣动画](modes/animated-explainer/styles/soft-colored-pencil-cute-animation.md)
- [清爽线描蜡笔动画](modes/animated-explainer/styles/clean-line-crayon-animation.md)
- [多巴胺萌趣 3D 动画](modes/animated-explainer/styles/dopamine-cute-3d-animation.md)

**Visual Journalism**

- [现代编辑部 Visual Journalism](modes/visual-journalism/styles/modern-editorial-visual-journalism.md)（首轮候选，待样片验证）

用户未指定 style 时，只展示当前 Mode 的内置或候选选项并等待选择，不设置静默默认值；自定义文字 style 与该 Mode 的内置 style 具有同等优先级。style 只定义跨作品稳定的媒介、材质、线条、造型、色彩和运动语言，不是固定 Prompt、场景或镜头模板。候选 style 必须明确验证状态，样片经用户确认后才可标记为已验证。

共享 references 只维护跨 Mode 能复用的能力：

- [人物参考图指南](references/character-reference-image-guide.md)：当 Mode 需要稳定的生成人物时读取。
- [Storytime 人物形象库](modes/storytime-animation/characters/character-library.md)：仅供 Storytime 选择、保存或改编经过用户确认的常用讲述者形象；不作为其他 Mode 的默认共享人物库。
- [内置音色库](references/reference-asset-library.md)：选择随 skill 分发的音色时读取。
- [音色参考与音频转换指南](references/voice-reference-guide.md)：当 Mode 使用旁白、对白或稳定声音身份时读取。
- [共享视频生成 Prompt 指南](references/video-generation-prompt-guide.md)：编写生成片段 Prompt 时读取；它不取代 Mode 专属的内容与视觉方法。
- [Seedance 2.0 官方提示词指南](references/official-seedance-2.0-prompt-guide.md)：使用 Seedance 时读取。
- [Seedance 社区导演与连续性笔记](references/community-directing-notes.md)：处理循环动作、重复运镜或切镜僵硬时补充读取。

当 Mode 需要人物参考时，只为必须稳定识别的人物生成参考图，不为一次性群演生成。人物参考只承担身份、相貌、比例、服装与材质职责。对当前已实现的动画 Mode，不生成或连接统一场景图、画风参考图或风格参考图；场景与画风由所选 style 和每个片段的具体文字 Prompt 直接定义。

内置音色的唯一正式媒体源为顶级目录 `voices/`，权威清单为[内置音色库](references/reference-asset-library.md)。宿主项目可以额外登记私有人物与音色，但不得扫描历史作品冒充正式资产库。`repository-assets/` 只保存 README 封面、效果示例和 style 预览等仓库展示素材，不属于 skill 执行资产，也不得被工作流当作生成输入。

## 执行工具路由

Mode 和执行工具相互独立：Mode 决定制作什么，工具文档决定如何在用户选定的平台上生成、管理和下载媒体。任意 Mode 都可在平台能力足够时选择任意已适配 CLI。

1. 用户已指定 CLI 时，完整读取对应工具文档并使用该路径。
2. 用户未指定时，先检查宿主项目已配置的媒体 CLI；有可用工具时向用户说明选择。
3. 没有任何可用 CLI 时，优先建议安装 LibTV CLI，但不未经用户同意自动安装。
4. 当前工具缺少必要能力、登录或最新文档时停止，不猜测命令，不静默切换其他平台。

当前工具文档：

- **[LibTV CLI](tools/libtv-cli.md)**：当前正式维护且验证最充分的执行路径。
- **[Higgsfield CLI](tools/higgsfield-cli.md)**：已完成安装、认证、workspace、实时 schema、素材、Seedance 2.0、任务跟踪与结果边界的文档适配，尚未完成付费生成和完整作品的端到端实作验证。
- **[即梦 CLI](tools/jimeng-cli.md)**：已完成 OAuth、session、生成模式、Seedance 2.0 全能参考、异步查询与 CLI 下载的文档适配，尚未完成付费生成和完整作品的端到端实作验证。

工具专属命令、模型别名、输入模式、参数映射、任务跟踪和下载规则只在对应 `tools/` 文档中维护，不在 Mode、style 或共享 references 中复制。

## 全 Mode 共享的片段规则

- Animated Explainer 和 Storytime Animation 使用 15 秒中文口播片段时，默认约 60 个汉字；英文 Storytime 默认目标 30 个实际朗读单词，通常保持 28–32 个且超过 32 个必须先缩短确认，Animated Explainer 以约 32 个英文单词作为可调整目标。两者都以语义自然完整、实际能够说完为先。Visual Journalism 不继承固定字数目标，按证据密度、图表阅读时间和目标音色实测。
- 任何 Mode 编写多镜头视频 Prompt 时，相邻镜头默认直接硬切，不写擦除、形变、融化或其他装饰性转场。只有连续性本身是创作重点的特殊长镜头，尤其长时间动作、追逐或打斗编排，才设计不中断的连续调度。

## 旁白驱动动画的共享生产流程

以下流程当前适用于 Animated Explainer 和 Storytime Animation；各 Mode 的采集、研究、结构、写作、视觉职责和质量门槛以对应 Mode 文件为准。

1. **按 Mode 完成讲稿。** 完整执行对应 Mode 的前期与写作流程，并遵循上方共享片段规则。将讲稿和拆分结果交给用户审阅；确认后立即保存为作品文档目录中的独立 `旁白.md`。
2. **规划必要人物参考。** 完整读取人物指南，允许 Animated Explainer 没有关键人物；Storytime Animation 的讲述者默认是关键人物。按实际需要生成、确认并记录人物映射。
3. **逐片段编写并保存 Prompt。** 完整读取当前 Mode 的专属 Prompt 指南（如果已有）、所选 style、共享视频 Prompt 指南和目标模型官方指南。每完成一个片段，立即保存为作品文档目录中的独立 Markdown 文件。
4. **选择音色路线并只生成片段 1。** 正式生成前，读取内置音色库，明确询问用户使用已有音色还是通过片段 1 新建音色。已有音色从片段 1 起连接；新建音色的片段 1 不连接音频参考。两条路线都只先生成片段 1，交给用户确认。
5. **锁定统一音色锚点。** 已有音色路线继续复用同一份标准化音频；新建音色路线按音色指南从已确认片段 1 建立独立音频素材。
6. **并行生成后续片段。** 从片段 2 开始全部使用已锁定的同一音色锚点；当前片段的准确旁白仍只由当前 Prompt 决定。
7. **确认返回并交付剪辑。** 使用选定工具文档完成任务跟踪与下载。默认只确认成功终态、可追溯 ID 和资源完整性，不播放、不抽帧、不听写；用户明确要求或返回异常时才做针对性内容检查。全部片段生成后，提示用户在剪辑工具中手动拼接并轻量修剪局部废帧、片尾画面或声音毛刺。只有用户明确要求时，才由 Agent 执行自动拼接。

需要封面时读取当前 Mode 的封面指南。目前只有 [Animated Explainer 封面指南](modes/animated-explainer/video-cover-image-guide.md) 已建立专属流程；不将它默认套用到其他 Mode。

## 任务路由

| 任务 | 必须完整读取 |
| --- | --- |
| 选择 Mode，或开始采集、研究、写作、分镜与制作 | 当前选定的 [Mode 文件](#mode-选择与路由) |
| 编写、改写或拆分 Animated Explainer 旁白 | [Animated Explainer 流程](modes/animated-explainer/workflow.md)和[旁白讲稿写作指南](modes/animated-explainer/narration-script-guide.md) |
| 采集、改编或编写第一人称故事 | [Storytime Animation 流程](modes/storytime-animation/workflow.md) |
| 研究现实议题，或编写 Visual Journalism 旁白与素材结构 | [Visual Journalism 流程](modes/visual-journalism/workflow.md)和[研究与证据指南](modes/visual-journalism/research-and-evidence-guide.md) |
| 编写、改写或排查 Visual Journalism 视频 Prompt | [Visual Journalism 流程](modes/visual-journalism/workflow.md)、[专属视频 Prompt 指南](modes/visual-journalism/video-prompt-guide.md)、所选 style、[共享视频生成 Prompt 指南](references/video-generation-prompt-guide.md)和目标模型官方指南 |
| 规划或生成人物参考 | [人物参考图指南](references/character-reference-image-guide.md)、当前 Mode 和所选 style；Storytime 另读[人物形象库](modes/storytime-animation/characters/character-library.md) |
| 编写、改写或排查视频生成 Prompt | 当前 Mode、[共享视频生成 Prompt 指南](references/video-generation-prompt-guide.md)和目标模型官方指南 |
| 选择、建立、转换或更换音色 | [内置音色库](references/reference-asset-library.md)和[音色参考与音频转换指南](references/voice-reference-guide.md) |
| 生成、比较、修改或质检 Animated Explainer 封面 | [Animated Explainer 封面指南](modes/animated-explainer/video-cover-image-guide.md) |
| 安装、选择或执行媒体 CLI | 选定的 [Tool 文件](#执行工具路由) |

Seedance 官方指南较长，定向排查时优先搜索：`基础公式`、`多模态参考`、`编辑视频`、`延长视频`、`定义主体`、`使用分镜时序`、`动作描述要求`、`运镜写法`、`特殊字符规范`、`音色参考不准`、`人物 ID 漂移`、`风格漂移`、`视频延长 vs 分段拼接`、`视频结尾有噪音`和`中文发音不准`。

## 共享质量门槛与失败条件

进入生成前，先通过当前 Mode 的专属质量门槛和共享视频 Prompt 检查。以下任一情况存在时，不得进入后续批量生成或最终交付：

- 当前 Mode 尚未选定，或未完整读取对应工作流。
- 用户要求的 Mode 尚未建立必要执行能力，但仍试图用另一 Mode 的流程伪装完成。
- 任一必须稳定识别的人物缺少已确认人物参考，或参考素材职责、编号与实际连接顺序不一致。
- 当前 Mode 需要统一音色，但片段 1 的音色尚未确认，或后续片段没有实际使用已锁定音色锚点。
- 选定 CLI 缺少登录、最新能力信息、必要模型能力或可追溯任务信息。
- 任一媒体任务未返回成功终态，或任务 ID、节点／项目 ID、资源 URL 等目标平台应提供的关键追踪信息缺失。

失败时保留 Mode、style、工具、模型、参数、素材映射、任务 ID、终态和 stderr 或等价日志。修正真实原因后重新执行，不静默换 Mode、style、模型或平台。

## 交付原则与信息优先级

默认使用用户当前使用的语言回复；用户明确指定其他输出语言时，遵循用户指定的语言。

创作草稿默认先在对话中使用普通 Markdown 段落展示，不放入 `text`、`plaintext` 或其他代码块。讲稿经用户确认后保存为独立 `旁白.md`；每个视频 Prompt 片段也分别保存为独立 Markdown 文件。这些文件与人物、素材等生产文档平铺在当前作品的同一文档目录，并向用户返回文件路径。

信息冲突时：内容与叙事方法以当前 Mode 为准；视觉语言以用户选择的 style 和已确认人物参考为准；模型提示能力以最新官方指南为准；平台命令、模型名、输入能力与参数以当前 CLI 和实时 schema 为准。
