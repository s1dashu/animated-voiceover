# Seedance 2.0 社区导演与连续性笔记

> 定位：GitHub 社区经验的可追踪摘要，不是官方文档。与 Doubao 官方指南、LibTV 实时 schema 或用户确认规则冲突时，以后三者为准。

## 来源快照

- [Emily2040/seedance-2.0](https://github.com/Emily2040/seedance-2.0/tree/6c51262377b96592b9f87a8c8b0219e6335378f7)，提交 `6c51262377b96592b9f87a8c8b0219e6335378f7`，重点参考：
  - `skills/seedance-prompt/SKILL.md`
  - `skills/seedance-camera/SKILL.md`
  - `skills/seedance-motion/SKILL.md`
  - `skills/seedance-sequence/SKILL.md`
  - `skills/seedance-prompt-short/SKILL.md`
- [dexhunter/seedance2-skill](https://github.com/dexhunter/seedance2-skill/tree/e06c7c63a766d623004a2807881c30685ce517af)，提交 `e06c7c63a766d623004a2807881c30685ce517af`，重点参考 `zh/SKILL.md`。
- [nolanx-ai/nolanx.ai](https://github.com/nolanx-ai/nolanx.ai/tree/595d86364377f654e24ddf2c9e875496d85e8246)，提交 `595d86364377f654e24ddf2c9e875496d85e8246`，重点参考 `skills/sd2-pe/SKILL.md`。

核验日期：2026-07-30。

## 本 skill 采用的经验

1. 把 Prompt 当作可直接执行的专业拍摄方案，而不是形容词堆叠。画面复杂度由内容决定，不用固定主体、动作、道具或焦点数量限制镜头。
2. 为每个镜头写清起始构图、主体调度、动作与运镜的全部阶段、方向、速度、衔接点和结束状态。运镜必须有终点，动作必须产生可见后果。
3. 允许电影式硬切。切镜可以主动改变景别、角度、运动方向、场景或叙事焦点；硬切本身不是连续性错误。
4. 跟踪“运镜阶段”和“动作阶段”。上一镜已经完成的推近、变焦、跟拍、聚焦或主体动作，不在下一镜从相似状态重新开始，除非这是明确设计的重复。
5. 每一镜结束后都应形成新的画面状态；下一镜从该状态之后的叙事动作继续，而不是回放已经完成的动作。动作有起因、落点和结果，循环而不改变状态会产生明显的 AI 生成感。
6. 精简 Prompt 时优先保留参考素材职责、初始构图、主体调度、动作过程、空间方向、可见终点和完整运镜路径；只删除重复风格形容词与空泛质量词，不删除决定镜头可复现性的动作或摄影信息。

## 本 skill 不采用的经验

- 不把精确秒数分镜设为默认。官方指南说明模型对精确时间约束的响应不稳定，本 skill 继续使用“镜头 1、镜头 2……”的事件顺序。
- 不复制社区技能中的模型调用、供应商、价格、分辨率或素材上限；这些能力只以 LibTV 实时 schema 为准。
- 不复制冗长负面词模板。只保留当前项目或用户明确要求的必要约束，不由 skill 擅自决定字幕、Logo、水印、背景音乐或口型策略。
- 不生成或连接独立场景／画风参考图。每个片段按自身场景需求直接写清地点、材质、色彩、光线和渲染方式；只保留能转化为可见画面的必要风格词，避免同义重复。
