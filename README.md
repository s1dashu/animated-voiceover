<h1 align="center">Animated Voiceover</h1>

<p align="center">
  <strong>把复杂思想变成有电影感的 AI 动画科普视频。</strong>
</p>

<p align="center">
  从资料研究和旁白文案，到多镜头提示词、音色一致性、质量检查与成片拼接。
</p>

<p align="center">
  <a href="./SKILL.md"><img alt="Codex 技能" src="https://img.shields.io/badge/Codex-%E6%8A%80%E8%83%BD-111111?style=for-the-badge&logo=openai&logoColor=white"></a>
  <a href="#核心能力"><img alt="AI 视频工作流" src="https://img.shields.io/badge/AI%20%E8%A7%86%E9%A2%91-%E5%B7%A5%E4%BD%9C%E6%B5%81-7C3AED?style=for-the-badge"></a>
  <a href="#工具支持"><img alt="Seedance 2.0" src="https://img.shields.io/badge/Seedance-2.0-2563EB?style=for-the-badge"></a>
  <a href="#核心流程"><img alt="15 秒片段" src="https://img.shields.io/badge/%E7%89%87%E6%AE%B5-15%20%E7%A7%92-0EA5E9?style=for-the-badge"></a>
  <a href="#工具支持"><img alt="LibTV CLI" src="https://img.shields.io/badge/CLI-LibTV-F97316?style=for-the-badge"></a>
  <a href="./LICENSE"><img alt="MIT 许可证" src="https://img.shields.io/badge/%E8%AE%B8%E5%8F%AF%E8%AF%81-MIT-2EA44F?style=for-the-badge"></a>
</p>

<p align="center">
  <a href="#视频效果参考">效果参考</a> ·
  <a href="#内置风格">内置风格</a> ·
  <a href="#核心能力">核心能力</a> ·
  <a href="#安装">安装</a> ·
  <a href="#使用方式">使用方式</a>
</p>

`animated-voiceover` 是一项开源 Codex skill，用于创作哲学、心理、历史、经济、金融、科技及相关知识领域的 AI 动画解说视频。

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
    <td align="center"><sub><b>哲学科普</b>——电影感人物叙事</sub></td>
    <td align="center"><sub><b>心理科普</b>——将抽象概念转化为画面</sub></td>
  </tr>
</table>

## 核心能力

- 研究并组织知识类选题。
- 编写清晰的旁白，并拆分为均衡的 15 秒片段。
- 从可扩展的风格目录中选择视觉语言，并据此编写内容专属的图像与视频提示词。
- 规划人物参考和多镜头导演方案。
- 编写素材职责清楚、可以直接用于 Seedance 的视频提示词。
- 使用已经确认的首个片段作为后续片段的统一音色锚点。
- 在拼接前检查旁白、音色、人物身份、镜头运动、实际画幅和音频质量。

## 内置风格

每种内置风格都有一份独立的通用指导，分别说明图像 Prompt 与视频 Prompt 应该如何体现该风格。它们定义稳定的视觉与运动语言，但不提供需要原样复制的固定 Prompt、场景或运镜模板。先结合当前内容编写专属图像 Prompt，生成并确认参考图，再为每个片段重新设计动作和镜头；也可以提供自定义风格说明或自己的参考图。

| 风格 | 视觉特征 | 指导 |
| --- | --- | --- |
| 电影感 3D 动画 | 哑光手绘材质、低饱和色彩、电影化空间与光影 | [查看图像与视频指导](./styles/cinematic-3d-animation.md) |
| 黏土定格动画 | 手工黏土偶、微缩布景、指纹和逐帧运动质感 | [查看图像与视频指导](./styles/clay-stop-motion.md) |
| 笨拙感手绘简笔画动画 | 歪斜简笔线条、大面积留白、粗纸逐帧重画感 | [查看图像与视频指导](./styles/clumsy-hand-drawn-animation.md) |

## 核心流程

1. 编写并确认完整旁白讲稿。
2. 选择内置或自定义视觉风格，为当前内容编写图像 Prompt，生成并确认风格参考图和人物参考图。
3. 结合所选风格的视频指导，为全部片段分别设计动作、镜头和视频提示词。
4. 先生成并确认片段 1，再剥离其音频作为音色参考。
5. 并行生成后续片段，逐片质检后拼接成片。

当前已经验证的生产节奏使用 15 秒片段，每段中文旁白约 60 个汉字，通常规划 5 个镜头。

## 工具支持

当前正式维护和实际验证的执行路径使用 LibTV CLI。查阅目标平台最新官方文档和实时模型 schema 后，这套创作方法也可以适配 Higgsfield、即梦以及其他同类多模态 CLI。

## 安装

可以直接让 Codex 从本仓库安装：

> 从 `https://github.com/s1dashu/animated-voiceover` 安装 `$animated-voiceover` skill。

也可以将本仓库克隆或复制到 Codex 的 skills 目录。

## 使用方式

可以从这样的请求开始：

> 使用 `$animated-voiceover` 创作一支两分钟的动画科普视频，主题是：两分钟了解斯多葛主义哲学。

完整工作流请阅读 [SKILL.md](./SKILL.md)。旁白、导演、音频、封面和 LibTV 的详细规范位于 [references](./references)。

## 当前支持范围

- 已针对多个 15 秒片段组成的成片完成优化和实际验证。
- 尚未针对 Seedance 2.5 Pro 的 30 秒片段完成系统性优化。
- 当前版本唯一正式维护的执行路径是 LibTV CLI。

## 许可证

本仓库的原创内容采用 [MIT License](./LICENSE) 开源。第三方文档和外部链接内容仍遵循各自权利人的许可条款。

<p align="center">
  如果这套工作流帮助你做出了值得分享的作品，欢迎为仓库点一个 Star。
</p>
