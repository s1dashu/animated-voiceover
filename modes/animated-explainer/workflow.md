# Animated Explainer

## 核心目标

使用旁白和动画，在一支短片中讲清楚一个概念、理论、人物思想、历史事件或知识主题。

本 Mode 就是本 skill 在引入 Mode 体系之前已经使用并完成实作验证的动画解说工作流。Mode 重构只改变文档所在位置和路由方式，不改变原有创作方法，也不额外增加解释结构、研究模板或画面类型限制。

## 适用边界

在以下情况选择本 Mode：

- 视频的核心是解释一个概念、机制、理论、人物思想、历史因果或知识问题。
- 内容主要依靠完整旁白和原创动画成立。

如果内容以个人经历与第一人称讲述为主，使用 [Storytime Animation](../storytime-animation/workflow.md)。如果结论主要依赖时效性资料、现实影像、数据图表和多来源证据，使用 [Animated Report](../animated-report/workflow.md)。

## 必须读取

开始写作前完整读取：

- [旁白讲稿写作指南](narration-script-guide.md)

开始人物规划时完整读取：

- [人物参考图指南](../../references/character-reference-image-guide.md)
- 用户已选择的 [style](../../SKILL.md#共享-style-与参考资产)

开始视频 Prompt 时完整读取：

- [Animated Explainer 视频 Prompt 指南](video-prompt-guide.md)
- [共享视频生成 Prompt 指南](../../references/video-generation-prompt-guide.md)
- [Seedance 2.0 官方提示词指南](../../references/official-seedance-2.0-prompt-guide.md)

## 完整制作流程

1. **写作、拆分并保存讲稿。** 确认主题、目标观众和成片时长，完整执行旁白讲稿写作指南。先完成全文，再按语义拆成当前生产所需的视频片段；向用户展示完整讲稿和拆分结果，确认后保存为作品文档目录中的 `旁白.md`。
2. **规划关键人物并生成人物参考图。** 根据定稿讲稿和全部片段判断哪些人物需要稳定身份。允许没有关键人物；不为一次性群演生成参考图。按人物参考图指南建立人物清单、出现片段映射和确认状态。
3. **逐片段编写并保存视频 Prompt。** 完整读取 Animated Explainer 视频 Prompt 指南、所选 style、共享视频生成 Prompt 指南和目标模型官方指南。为每个片段重新设计具体场景、多镜头调度、动作和切换；每完成一个片段，就保存为独立 Markdown 文件。
4. **执行公共生成流程。** 返回主 `SKILL.md`，完成音色路线选择、片段 1 确认、统一音色锚点、后续片段生成、任务确认和下载；默认交给用户在剪辑工具中手动拼接与轻量修剪，只有用户明确要求时才自动拼接。
5. **按需制作封面。** 需要发布封面时，读取本 Mode 的[封面指南](video-cover-image-guide.md)。

## 当前状态

本 Mode 是 skill 当前唯一完成多期作品实作验证的模式。它继承重构前已经确认的旁白写作、片段拆分、人物参考、逐片段 Prompt、统一音色和生成流程；具体规则继续以对应指南和主 `SKILL.md` 为准。
