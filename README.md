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
    <td align="center"><sub><b>心理科普</b>——用具体事件讲清抽象思想</sub></td>
  </tr>
</table>

## 核心能力

- 研究并组织知识类选题。
- 编写清晰的旁白，并拆分为均衡的 15 秒片段。
- 从可扩展的风格目录中选择视觉语言，并据此编写内容专属的图像与视频提示词。
- 规划人物参考和多镜头导演方案。
- 编写素材职责清楚、可以直接用于 Seedance 的视频提示词。
- 从随 skill 分发的音色与图像参考库选择现成资产，或通过片段 1 新建本期音色锚点。
- 生成后默认只确认每个任务成功返回、节点与任务信息完整、资源可下载；仅在用户明确要求或平台出现异常时进行内容质检。
- 所有片段与最终成片统一平铺到当前作品的 `video/` 目录，不创建逐片子目录。

## 内置风格

每种内置风格都有一份独立的通用指导，分别说明图像 Prompt 与视频 Prompt 应该如何体现该风格。它们定义稳定的视觉与运动语言，但不提供需要原样复制的固定 Prompt、场景或运镜模板。先结合当前内容编写专属图像 Prompt，生成并确认参考图，再为每个片段重新设计动作和镜头；也可以提供自定义风格说明或自己的参考图。

下图只用于展示媒介、材质、线条、色彩和整体气质，不代表固定人物、场景或构图。点击图片可查看原图。

<table>
  <tr>
    <td width="50%" align="center">
      <a href="./assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v2.png"><img src="./assets/style-previews/cinematic-3d-animation-nietzsche-16x9-v2.png" alt="电影感 3D 动画效果图" height="220"></a><br>
      <b>电影感 3D 动画</b><br>
      <sub>哑光手绘材质、低饱和色彩、电影化空间与光影</sub><br>
      <a href="./styles/cinematic-3d-animation.md">查看图像与视频指导</a>
    </td>
    <td width="50%" align="center">
      <a href="./assets/style-previews/dopamine-cute-3d-animation-16x9-v2.png"><img src="./assets/style-previews/dopamine-cute-3d-animation-16x9-v2.png" alt="多巴胺萌趣 3D 动画效果图" height="220"></a><br>
      <b>多巴胺萌趣 3D 动画</b><br>
      <sub>Q 弹圆润角色、高明度多巴胺配色、丰富满画幅层次</sub><br>
      <a href="./styles/dopamine-cute-3d-animation.md">查看图像与视频指导</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="./assets/style-previews/clay-stop-motion.png"><img src="./assets/style-previews/clay-stop-motion.png" alt="黏土定格动画效果图" height="220"></a><br>
      <b>黏土定格动画</b><br>
      <sub>手工黏土偶、微缩布景、压痕与逐帧运动质感</sub><br>
      <a href="./styles/clay-stop-motion.md">查看图像与视频指导</a>
    </td>
    <td width="50%" align="center">
      <a href="./assets/style-previews/melancholic-blue-simple-line-animation.png"><img src="./assets/style-previews/melancholic-blue-simple-line-animation.png" alt="忧郁蓝调简笔画风格效果图" height="220"></a><br>
      <b>忧郁蓝调简笔画风格</b><br>
      <sub>冷灰蓝纸面、笨拙铅笔线、低对比与安静内省气质</sub><br>
      <a href="./styles/melancholic-blue-simple-line-animation.md">查看图像与视频指导</a>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <a href="./assets/style-previews/soft-colored-pencil-cute-animation.png"><img src="./assets/style-previews/soft-colored-pencil-cute-animation.png" alt="柔和彩铅萌趣动画效果图" height="220"></a><br>
      <b>柔和彩铅萌趣动画</b><br>
      <sub>柔软铅笔轮廓、松散彩铅与粗蜡笔平涂、温暖纸纹</sub><br>
      <a href="./styles/soft-colored-pencil-cute-animation.md">查看图像与视频指导</a>
    </td>
    <td width="50%" align="center">
      <a href="./assets/style-previews/clean-line-crayon-animation.png"><img src="./assets/style-previews/clean-line-crayon-animation.png" alt="清爽线描蜡笔动画效果图" height="220"></a><br>
      <b>清爽线描蜡笔动画</b><br>
      <sub>深色手绘线描、明快蜡笔色块、清爽有序的二维构图</sub><br>
      <a href="./styles/clean-line-crayon-animation.md">查看图像与视频指导</a>
    </td>
  </tr>
</table>

## 内置参考资产

Skill 随包提供 4 个标准化 WAV 音色和 2 张图像风格参考。开始新视频时会分别询问用户使用内置资产、自定义资产还是新建参考，不设置默认项。文件、描述、规格、哈希与使用边界统一登记在[内置参考资产库](./references/reference-asset-library.md)。

## 核心流程

1. 编写并确认完整旁白讲稿。
2. 选择内置图像参考、内置或自定义视觉风格，或新生成风格参考图；确认风格参考和人物参考图。
3. 结合所选风格的视频指导，为全部片段分别设计动作、镜头和视频提示词，并保存为当前作品的 Markdown 文档。
4. 选择内置音色或通过片段 1 新建音色；两条路线都先只生成并确认片段 1。
5. 并行生成后续片段，确认全部任务成功返回并下载到 `video/` 后拼接成片。

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

完整工作流请阅读 [SKILL.md](./SKILL.md)。细则分别由[内置参考资产库](./references/reference-asset-library.md)、[旁白讲稿指南](./references/narration-script-guide.md)、[视频提示词指南](./references/video-prompt-guide.md)、[音色参考指南](./references/voice-reference-guide.md)和[视频封面指南](./references/video-cover-image-guide.md)维护。

## 当前支持范围

- 已针对多个 15 秒片段组成的成片完成优化和实际验证。
- 尚未针对 Seedance 2.5 Pro 的 30 秒片段完成系统性优化。
- 当前版本唯一正式维护的执行路径是 LibTV CLI。

## 许可证

本仓库的原创内容采用 [MIT License](./LICENSE) 开源。第三方文档和外部链接内容仍遵循各自权利人的许可条款。

<p align="center">
  如果这套工作流帮助你做出了值得分享的作品，欢迎为仓库点一个 Star。
</p>
