# 多巴胺萌趣 3D 动画

## 模型偏好

- 生成采用本风格的图像时，优先使用 Nano Banana Pro；已确认它更容易同时实现 Q 弹角色、鲜明多巴胺配色、丰富满画幅内容与清楚的构图层级。风格仍由本文件的文字规则定义，不生成独立画风参考图。
- 模型名称与调用参数仍以当前平台的实时 schema 为准。首选模型不可用时应明确告知用户并重新确认，不静默替换。

## 稳定的视觉语言

- 使用明快、精致的风格化 3D 动画渲染。角色采用超级变形比例、圆润大头、短小四肢、饱满脸颊和柔软回弹的体块，呈现棉花糖、软胶或果冻般的 Q 弹感，但避免廉价塑料玩具质感。
- 使用大胆、鲜明、发光般愉悦的多巴胺配色，可按内容组合亮粉、橘红、柠檬黄、青蓝、钴蓝、青柠绿和紫罗兰；保持高明度与清楚色块，不用灰暗、浑浊或大面积低饱和配色。
- 让主体、道具、建筑、动植物和装饰覆盖前景、中景与背景，使画面丰富并铺满画幅；不限制焦点数量，通过大形体层级、分组、引导线、清楚轮廓和受控重复建立明确的观看顺序与可读结构。
- 使用圆角、豆形、泡泡形和柔和曲线统一造型语言，以哑光黏土、柔润软胶和半透明果冻材质建立触感；使用明亮柔和的电影化照明、干净接触阴影和适度景深保持空间层次。
- 萌感来自多样的圆润轮廓、弹性姿态、角色互动和充满活力的动作结果，不把所有角色做成同一个模具的换色版本。

## 撰写图像 Prompt

1. 先根据当前内容定义主体、动作、环境和叙事关系，再加入本风格的造型、材质、配色与构图密度；不得把某个城市、游乐园、海底场景或固定吉祥物当作默认内容。
2. 明确各视觉焦点的优先级、环境元素如何分组，以及视线按什么顺序移动。要求前景、中景和背景都有内容，但不能让装饰遮挡主体动作或破坏轮廓。
3. 生成人物参考图时，默认用一张无遮挡、全身可见的单人物图锁定体块轮廓、五官位置、头身比例、服装色块与材质；背景可以使用简洁明快的色彩。背面、侧面和多视图只在真实镜头需要时补充。不同人物应在轮廓与形状语言上明显可区分。
4. 动画视频不生成风格或场景参考图；在每个片段的视频 Prompt 中根据具体场景写清多个角色、丰富环境、远近层次和高明度色彩关系，并检验“内容很多但结构清晰”是否同时成立。

### 通用风格 Prompt

将方括号内容替换为当前作品专属的主体、动作、环境和叙事关系，并根据内容调整具体色彩比例与材质：

```text
[CURRENT SUBJECTS, ACTIONS, ENVIRONMENT, AND STORY RELATIONSHIPS]. Premium stylized dopamine-color 3D animation, ultra-cute super-deformed characters with large expressive eyes, round cheeks, tiny limbs, soft marshmallow bodies, buoyant jelly-like poses and irresistibly squishy rounded forms. Bold luminous colors using a content-appropriate combination of vivid fuchsia, tangerine, lemon yellow, aqua cyan, cobalt blue, lime green and violet. Velvety matte clay and soft silicone surfaces with selective translucent gummy details, bright joyful cinematic lighting, clean contact shadows and playful depth. Fill the entire frame with abundant characters, props and environmental details across foreground, middle ground and background, while keeping the composition instantly readable through a clear hierarchy of focal points, large simple shape organization, clearly grouped elements, clean silhouettes, controlled repetition and an obvious viewing order. Rich, energetic and full of delightful discoveries, but never chaotic. No empty background, no photorealism, no cheap plastic toy look, no muddy or gloomy colors, no text, no typography, no logo, no watermark.
```

## 撰写视频 Prompt

1. 让角色动作具有明显的压缩、伸展、回弹、重心转移和接触反馈，但只在动作需要时使用，不让所有主体持续同频弹跳。
2. 让丰富环境参与运动，例如道具传递、装饰摆动、交通移动、气泡或彩屑穿行；按镜头区分主要动作与辅助动作，避免满画幅内容互相争抢注意力。
3. 根据叙事选择跟随、横移、俯拍、推拉、复合运镜、快速切换或分层视差。像 3D 动画电影分镜一样写清摄影机起点、角色与环境调度、每阶段移动方向、空间轨迹、焦点转换、阶段衔接和最终构图，不因元素密集而无目的扫过整个画面。
4. 保持高明度色块、圆润材质和清楚轮廓的一致性；不同镜头可以改变场景、主体数量、景别和主色，不机械复刻其他片段的构图。

## 明确排除

- 写实真人比例、照片级皮肤、硬表面游戏 CG 和廉价光滑塑料玩具。
- 只有柔和粉彩而缺少鲜明对比的普通儿童 3D 插画。
- 用无序装饰堆砌代替构图层级，或为了画面简洁而留下大面积空背景。
- 固定吉祥物换色、所有角色同脸同体型，以及无法辨认主体动作的过密画面。
