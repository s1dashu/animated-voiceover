<h1 align="center">Animated Voiceover</h1>

<p align="center">
  <strong>把值得讲清楚的知识，变成让人愿意看完的 AI 动画视频。</strong>
</p>

<p align="center">
  一个面向 Codex 的开源创作 Skill，覆盖选题研究、旁白写作、视觉设计、多镜头导演、统一音色与成片制作。
</p>

<p align="center">
  <a href="./SKILL.md"><img alt="Codex Skill" src="https://img.shields.io/badge/Codex-Skill-111111?style=for-the-badge&logo=openai&logoColor=white"></a>
  <a href="#内置视觉风格"><img alt="六种内置视觉风格" src="https://img.shields.io/badge/%E5%86%85%E7%BD%AE%E9%A3%8E%E6%A0%BC-6%20%E7%A7%8D-7C3AED?style=for-the-badge"></a>
  <a href="#从一句话开始创作"><img alt="Seedance" src="https://img.shields.io/badge/Seedance-Ready-2563EB?style=for-the-badge"></a>
  <a href="#工具与适用范围"><img alt="LibTV CLI" src="https://img.shields.io/badge/CLI-LibTV-F97316?style=for-the-badge"></a>
  <a href="./LICENSE"><img alt="MIT 许可证" src="https://img.shields.io/badge/License-MIT-2EA44F?style=for-the-badge"></a>
</p>

<p align="center">
  <a href="#它能帮你做什么">核心能力</a> ·
  <a href="#视频效果参考">效果参考</a> ·
  <a href="#内置视觉风格">视觉风格</a> ·
  <a href="#安装">安装</a> ·
  <a href="#从一句话开始创作">开始创作</a>
</p>

`animated-voiceover` 专为哲学、心理、历史、经济、金融和科技等知识内容而设计。你只需要提出一个主题，它会与你一起把零散的想法发展成完整讲稿，再进一步完成视觉风格、人物参考、多镜头视频 Prompt、统一音色和成片制作方案。

它不只是“帮你写几段提示词”。它真正解决的是知识动画最难的三个问题：**怎么把复杂概念讲得清楚，怎么把抽象思想拍得好看，以及怎么让多个 AI 视频片段看起来属于同一支作品。**

## 它能帮你做什么

- **把复杂知识讲清楚。** 从主题研究、内容取舍到旁白结构，帮助你建立一条观众听得懂、愿意继续听的叙事线。
- **把抽象观点变成具体画面。** 不依赖漂浮符号和空洞意象，而是用人物、行动、场景和结果，让哲学与知识真正“发生”在镜头里。
- **把一篇讲稿变成可生成的动画方案。** 自动拆分叙事节奏，为每个片段设计多镜头调度，并输出可以直接进入 Seedance 制作的视频 Prompt。
- **让整支视频保持统一。** 通过视觉风格参考、人物参考与音色锚点，减少跨片段的人物漂移、画风跳变和声音不一致。
- **从创意一路走到成片。** 不止交付文案，还能继续完成参考素材规划、片段生成、任务追踪、视频拼接与带字封面设计。

## 视频效果参考

<table>
  <tr>
    <td width="50%">
      <img src="./assets/examples/video-effect-01.png" alt="动画哲学解说视频画面" width="100%">
    </td>
    <td width="50%">
      <img src="./assets/examples/video-effect-02.png" alt="动画心理解说视频画面" width="100%">
    </td>
  </tr>
  <tr>
    <td align="center"><sub><b>哲学科普</b>——让思想进入人物与故事</sub></td>
    <td align="center"><sub><b>心理科普</b>——用具体事件解释抽象概念</sub></td>
  </tr>
</table>

## 内置视觉风格

Skill 内置六套经过整理的视觉语言，从电影感 3D 到手绘蜡笔动画均可直接选择。每套风格不仅描述“画面长什么样”，也包含它在人物造型、材质、色彩、镜头运动和动画节奏上的创作方法。

这些风格是创作起点，不是套模板。Skill 会围绕每一期的内容重新设计场景、人物与镜头；你也可以提供自己的风格说明或参考图，创作完全不同的视觉方向。

<table>
  <tr>
    <td width="50%" align="center">
      <a href="./assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v2.png"><img src="./assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v2.png" alt="电影感 3D 动画效果图" height="220"></a><br>
      <b>电影感 3D 动画</b><br>
      <sub>手绘质感、克制色彩与富有叙事感的电影光影</sub><br>
      <a href="./styles/cinematic-3d-animation.md">查看风格详情</a>
    </td>
    <td width="50%" align="center">
      <a href="./assets/style-previews/clay-stop-motion.png"><img src="./assets/style-previews/clay-stop-motion.png" alt="黏土定格动画效果图" height="220"></a><br>
      <b>黏土定格动画</b><br>
      <sub>手工黏土偶、微缩布景与真实可触的逐帧质感</sub><br>
      <a href="./styles/clay-stop-motion.md">查看风格详情</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="./assets/style-previews/melancholic-blue-simple-line-animation.png"><img src="./assets/style-previews/melancholic-blue-simple-line-animation.png" alt="忧郁蓝调简笔画风格效果图" height="220"></a><br>
      <b>忧郁蓝调简笔画</b><br>
      <sub>冷灰蓝纸面、笨拙铅笔线与安静内省的情绪</sub><br>
      <a href="./styles/melancholic-blue-simple-line-animation.md">查看风格详情</a>
    </td>
    <td width="50%" align="center">
      <a href="./assets/style-previews/soft-colored-pencil-cute-animation.png"><img src="./assets/style-previews/soft-colored-pencil-cute-animation.png" alt="柔和彩铅萌趣动画效果图" height="220"></a><br>
      <b>柔和彩铅萌趣动画</b><br>
      <sub>柔软轮廓、温暖纸纹与轻松亲切的可爱表达</sub><br>
      <a href="./styles/soft-colored-pencil-cute-animation.md">查看风格详情</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="./assets/style-previews/clean-line-crayon-animation.png"><img src="./assets/style-previews/clean-line-crayon-animation.png" alt="清爽线描蜡笔动画效果图" height="220"></a><br>
      <b>清爽线描蜡笔动画</b><br>
      <sub>明快色块、清楚线描与清爽有序的二维世界</sub><br>
      <a href="./styles/clean-line-crayon-animation.md">查看风格详情</a>
    </td>
    <td width="50%" align="center">
      <a href="./assets/style-previews/dopamine-cute-3d-animation-16x9-v2.png"><img src="./assets/style-previews/dopamine-cute-3d-animation-16x9-v2.png" alt="多巴胺萌趣 3D 动画效果图" height="220"></a><br>
      <b>多巴胺萌趣 3D 动画</b><br>
      <sub>Q 弹角色、明亮配色与充满活力的画面层次</sub><br>
      <a href="./styles/dopamine-cute-3d-animation.md">查看风格详情</a>
    </td>
  </tr>
</table>

## 不只是画风，还有可复用的声音与参考资产

除了六套视觉风格，Skill 还随包提供经过整理的图像参考和多种标准化中文音色，包括沉静青年男声、明亮活力男声、温柔成年女声与灵动年轻女声。

你可以直接选用现成资产，快速建立统一的作品气质；也可以从第一个片段开始创造本期专属声音。Skill 会先与你确认选择，不会擅自替你决定风格或音色。

完整资产清单见[内置参考资产库](./references/reference-asset-library.md)。

## 一套为知识动画设计的完整工作流

1. **确定讲什么。** 围绕主题、受众和时长研究资料，完成一篇结构清楚的旁白讲稿。
2. **确定长什么样。** 选择内置风格、自定义风格或参考图，建立统一的视觉方向和人物形象。
3. **把文字导演成画面。** 将讲稿拆成节奏均衡的片段，为每段设计具体事件、多镜头调度和可直接生成的视频 Prompt。
4. **先验证，再批量制作。** 先完成第一个片段，确认画面与声音方向，再锁定音色和参考素材，继续生成其余内容。
5. **组合为完整作品。** 汇总全部片段并完成拼接；需要发布包装时，还可以继续制作带字封面。

目前经过实际验证的创作节奏是：将 1–5 分钟视频拆成 15 秒片段，每段中文旁白约 60 个汉字，并用约 5 个镜头保持画面变化与叙事密度。这些参数会服务于内容，而不是反过来限制创作。

## 安装

直接告诉 Codex：

> 从 `https://github.com/s1dashu/animated-voiceover` 安装 `$animated-voiceover` skill。

也可以将本仓库克隆或复制到 Codex 的 skills 目录。

## 从一句话开始创作

安装后，你可以这样开始：

> 使用 `$animated-voiceover` 创作一支两分钟的动画科普视频，主题是：两分钟了解斯多葛主义。

也可以带上自己的要求：

> 使用 `$animated-voiceover` 把“为什么人会拖延”做成一支 90 秒心理科普动画。希望语气温柔，使用手绘风格，先和我确认讲稿与视觉方案。

Skill 会引导你完成必要选择，你不需要提前了解 Seedance Prompt、音色锚点或多模态素材连接方式。

## 工具与适用范围

当前正式维护并经过实际制作验证的媒体执行路径是 [LibTV CLI](https://libtv.ai/)。这套关于讲稿结构、视觉一致性、人物参考、多镜头导演和音色管理的方法并不依赖单一平台；在查阅目标平台的最新官方文档后，也可以适配 Higgsfield、即梦及其他支持多模态生成的 CLI。

目前的工作流主要针对由多个 15 秒片段组成的 1–5 分钟视频。Seedance 2.5 Pro 的 30 秒片段尚未完成系统性验证，因此没有被宣传为当前版本的默认能力。

想了解完整执行规则，可以阅读 [SKILL.md](./SKILL.md)。旁白、视频 Prompt、音色参考与封面制作方法分别收录在 [`references/`](./references/) 中。

## 许可证

本仓库的原创内容采用 [MIT License](./LICENSE) 开源。第三方文档和外部链接内容仍遵循各自权利人的许可条款。

<p align="center">
  <strong>如果你也想把知识做得更好看，欢迎试用、分享，并为这个项目点一个 Star。</strong>
</p>
