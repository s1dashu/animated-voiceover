<h1 align="center">director</h1>

<p align="center">
  <a href="./README.md">English</a> · <strong>简体中文</strong>
</p>

<p align="center">
  <strong>从第一个想法开始，导演并制作一支完整视频。</strong>
</p>

<p align="center">
  <img src="./repository-assets/repository-covers/director-cover.png" alt="director：用于导演和制作多类型视频的多 Mode Agent Skill" width="100%">
</p>

<p align="center">
  <a href="./SKILL.md"><img alt="Agent Skill" src="https://img.shields.io/badge/Agent-Skill-111111"></a>
  <a href="#它能帮你做什么"><img alt="Animated Explainer：已通过实际生产验证" src="https://img.shields.io/badge/Explainer-validated-2EA44F"></a>
  <a href="./LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/license-MIT-2EA44F"></a>
</p>

<p align="center">
  <a href="#它能帮你做什么">核心能力</a> ·
  <a href="#视频效果参考">效果参考</a> ·
  <a href="#内置视觉风格">视觉风格</a> ·
  <a href="#安装">安装</a> ·
  <a href="#从一句话开始创作">开始创作</a>
</p>

`director` 是一个用于导演和制作完整视频的 Agent Skill，覆盖从创意、脚本到镜头设计、素材生成和最终交付的完整流程。

- **Animated Explainer（动画解说）**——通过清晰的旁白和动画场景，解释概念、思想、历史事件或知识主题。
- **Storytime Animation（故事动画）**——把第一人称经历制作成动画故事，结合面向观众的讲述与事件重现。
- **Visual Journalism（视觉新闻）**——围绕时事、财经、产业等现实议题，以证据驱动叙事，结合纪录片实拍、解释性动画、地图、图表和动态图形。

## 它能帮你做什么

- **选择正确的导演语法。** 根据作品由个人经历、知识解释、现实证据还是戏剧行动驱动，选择对应工作流。
- **把复杂知识讲清楚。** 从主题研究、内容取舍到旁白结构，帮助你建立一条观众听得懂、愿意继续听的叙事线。
- **把文字变成可生产的导演方案。** 将叙事拆成可执行单元，设计镜头、表演与调度，并按照当前 Mode 输出可生成的 Prompt。
- **让整支视频保持统一。** 通过文字 style、必要的人物参考与音色锚点，减少跨片段的人物漂移、画风跳变和声音不一致。
- **从创意一路走到可剪辑片段。** 不止交付文案，还能继续完成参考素材规划、片段生成和任务追踪，再把全部素材交给剪辑工具完成最终拼接与轻量修整。

## 视频效果参考

<table>
  <tr>
    <td width="50%">
      <img src="./repository-assets/examples/video-effect-01.webp" alt="动画哲学解说视频画面" width="100%">
    </td>
    <td width="50%">
      <img src="./repository-assets/examples/video-effect-02.webp" alt="动画心理解说视频画面" width="100%">
    </td>
  </tr>
  <tr>
    <td align="center"><sub><b>哲学科普</b>——让思想进入人物与故事</sub></td>
    <td align="center"><sub><b>心理科普</b>——用具体事件解释抽象概念</sub></td>
  </tr>
</table>

## 内置视觉风格

Skill 当前内置六套已经 Animated Explainer 验证的视觉语言，以及一套 Storytime Animation 专属风格。每个 Mode 管理自己已验证的 style，不向用户暴露未验证组合；只有 style 在多个 Mode 的真实作品中验证成功后，才提升为跨 Mode 共享。

这些风格是创作起点，不是套模板。Skill 会围绕每一期的内容重新设计场景、人物与镜头；你也可以为当前 Mode 提供自己的文字风格说明。视觉 style 不依赖图片参考资产。

<table>
  <tr>
    <td width="50%" align="center" valign="top">
      <a href="./repository-assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v3.webp"><img src="./repository-assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v3.webp" alt="电影感 3D 动画效果图" height="220"></a><br>
      <b>电影感 3D 动画</b><br>
      <sub>手绘质感、克制色彩与富有叙事感的电影光影</sub><br>
      <a href="./modes/animated-explainer/styles/cinematic-3d-animation.md">查看风格详情</a>
    </td>
    <td width="50%" align="center" valign="top">
      <a href="./repository-assets/style-previews/clay-stop-motion.webp"><img src="./repository-assets/style-previews/clay-stop-motion.webp" alt="黏土定格动画效果图" height="220"></a><br>
      <b>黏土定格动画</b><br>
      <sub>手工黏土偶、微缩布景与真实可触的逐帧质感</sub><br>
      <a href="./modes/animated-explainer/styles/clay-stop-motion.md">查看风格详情</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center" valign="top">
      <a href="./repository-assets/style-previews/melancholic-blue-simple-line-animation.webp"><img src="./repository-assets/style-previews/melancholic-blue-simple-line-animation.webp" alt="忧郁蓝调简笔画风格效果图" height="220"></a><br>
      <b>忧郁蓝调简笔画</b><br>
      <sub>冷灰蓝纸面、笨拙铅笔线与安静内省的情绪</sub><br>
      <a href="./modes/animated-explainer/styles/melancholic-blue-simple-line-animation.md">查看风格详情</a>
    </td>
    <td width="50%" align="center" valign="top">
      <a href="./repository-assets/style-previews/soft-colored-pencil-cute-animation.webp"><img src="./repository-assets/style-previews/soft-colored-pencil-cute-animation.webp" alt="柔和彩铅萌趣动画效果图" height="220"></a><br>
      <b>柔和彩铅萌趣动画</b><br>
      <sub>柔软轮廓、温暖纸纹与轻松亲切的可爱表达</sub><br>
      <a href="./modes/animated-explainer/styles/soft-colored-pencil-cute-animation.md">查看风格详情</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center" valign="top">
      <a href="./repository-assets/style-previews/clean-line-crayon-animation.webp"><img src="./repository-assets/style-previews/clean-line-crayon-animation.webp" alt="清爽线描蜡笔动画效果图" height="220"></a><br>
      <b>清爽线描蜡笔动画</b><br>
      <sub>明快色块、清楚线描与清爽有序的二维世界</sub><br>
      <a href="./modes/animated-explainer/styles/clean-line-crayon-animation.md">查看风格详情</a>
    </td>
    <td width="50%" align="center" valign="top">
      <a href="./repository-assets/style-previews/dopamine-cute-3d-animation-16x9-v2.webp"><img src="./repository-assets/style-previews/dopamine-cute-3d-animation-16x9-v2.webp" alt="多巴胺萌趣 3D 动画效果图" height="220"></a><br>
      <b>多巴胺萌趣 3D 动画</b><br>
      <sub>Q 弹角色、明亮配色与充满活力的画面层次</sub><br>
      <a href="./modes/animated-explainer/styles/dopamine-cute-3d-animation.md">查看风格详情</a>
    </td>
  </tr>
</table>

Storytime Animation 拥有自己的[清爽白色圆身 Storytime 动画](./modes/storytime-animation/styles/clean-white-character-storytime-animation.md)：白色圆身二维人物、利落黑色粗线、有限平涂色块、清楚的喜剧表演，以及比人物更具体的环境。

## 不只是画风，还有可复用的声音

除了七套由文字 Prompt 定义的视觉风格，Skill 还随包提供多种标准化中文与英文音色。

你可以直接选用现成音色，也可以从第一个片段开始创造本期专属声音。Skill 会先与你确认选择，不会擅自替你决定风格或音色。

完整音色清单见[内置音色库](./references/reference-asset-library.md)。

## 已完成生产验证的工作流

Storytime Animation 增加第一人称故事采集、Storytime 专属[人物形象库](./modes/storytime-animation/characters/character-library.md)、对话式人物共创、讲述者表演，以及面向观众讲述与事件重现之间的灵活切换。Animated Explainer 则保留引入 Mode 架构前已经验证的原有工作流。

1. **确定讲什么。** 围绕主题、受众和时长研究资料，完成一篇结构清楚的旁白讲稿。
2. **确定长什么样。** 选择由文字 Prompt 定义的内置或自定义风格，并只为必须稳定辨认的人物建立参考图。
3. **把文字导演成画面。** 将讲稿拆成节奏均衡的片段，为每段设计具体事件、多镜头调度和可直接生成的视频 Prompt。
4. **先验证，再批量制作。** 先完成第一个片段，确认画面与声音方向，再锁定音色和必要人物参考，继续生成其余内容。
5. **在剪辑工具中收尾。** 下载全部生成片段后，由用户手动排序和拼接，轻量修剪边缘废帧、片尾极短声音毛刺，并检查节奏与切点。只有用户明确要求时才自动拼接。

目前经过实际验证的创作节奏是：将 1–5 分钟视频拆成 15 秒片段。Animated Explainer 通常以约 60 个汉字或约 32 个英文单词、约 5 镜为起点；英文 Storytime 以 30 个实际朗读单词为目标，通常保持 28–32 词，并使用 3–5 镜，约 4 镜是当前稳定起点。

## 安装

将本仓库克隆或复制到你的 Agent 可以读取的 skills 目录。

如果你使用 Codex，也可以直接告诉它：

> 从 `https://github.com/s1dashu/director` 安装 `director` skill。

在 Codex 中，显式调用 skill 时需要使用 `$` 前缀，所以写作 `$director`。Skill 本身的名称仍然只是 `director`；其他 Agent 使用各自运行环境的调用约定。

### 从 `animated-voiceover` 迁移

本项目由 `animated-voiceover` 原地重命名为 `director`。GitHub 会保留仓库历史、Stars、Issues，并把旧仓库地址重定向到新地址；但用户本地复制安装的 skill 目录不会自动改名。

- 将已有 Git remote 更新为 `https://github.com/s1dashu/director.git`。
- 安装 `director` 后删除本地旧 `animated-voiceover` skill 目录，避免 Agent 同时发现两份不同版本的工作流。
- Codex 中把 `$animated-voiceover` 改为 `$director`；其他 Agent 使用各自的 skill 调用方式。

## 从一句话开始创作

安装后，你可以这样开始：

> 使用 `director` skill 创作一支两分钟的动画科普视频，主题是：两分钟了解斯多葛主义。

也可以带上自己的要求：

> 使用 `director` skill 把“为什么人会拖延”做成一支 90 秒心理科普动画。希望语气温柔，使用手绘风格，先和我确认讲稿与视觉方案。

Skill 会引导你完成必要选择，你不需要提前了解 Seedance Prompt、音色锚点或多模态素材连接方式。

## 工具与适用范围

当前正式维护并经过实际制作验证的媒体执行路径是 [LibTV CLI](https://libtv.ai/)。这套关于讲稿结构、视觉一致性、人物参考、多镜头导演和音色管理的方法并不依赖单一平台；在查阅目标平台的最新官方文档后，也可以适配 Higgsfield、即梦及其他支持多模态生成的 CLI。

目前的工作流主要针对由多个 15 秒片段组成的 1–5 分钟视频。Seedance 2.5 Pro 的 30 秒片段尚未完成系统性验证，因此没有被宣传为当前版本的默认能力。

想了解完整执行规则，可以阅读 [SKILL.md](./SKILL.md)。旁白、视频 Prompt、音色参考与封面制作方法分别收录在 [`references/`](./references/) 中。

## 许可证

本仓库的原创内容采用 [MIT License](./LICENSE) 开源。第三方文档和外部链接内容仍遵循各自权利人的许可条款。

<p align="center">
  <strong>如果你也想和 Agent 一起导演出更好的视频，欢迎试用、分享，并为这个项目点一个 Star。</strong>
</p>
