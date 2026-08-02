# 忧郁蓝调简笔画风格

## 风格定位

以冷灰蓝纸面、笨拙铅笔线和克制彩铅色块构成的二维简笔画动画。画面简单、纯净、低对比且略带忧郁，但不刻意营造黑暗、压抑或戏剧化的夜景。

## 稳定的视觉语言

- 使用二维极简简笔画与大面积干净留白。每幅画面只保留说明当前事件所必需的人物、物体和环境线索，不用装饰性背景填满空间。
- 人物可采用偏大的圆形或椭圆头部、细长弯曲的四肢和有意不准确的头身比。五官使用小点、短线和简单弧线；造型可以笨拙，但身份、视线、姿态和动作结果必须清楚。
- 使用轻微抖动、粗细不均、局部断续的铅笔轮廓；保留少量重复描线、不完全闭合、纸面摩擦和轻微擦改痕迹。线条不应变成干净的数字矢量描边。
- 填色使用克制的彩铅平涂和轻微干粉彩，保留可见粗纸纹理、纸色透出、局部涂色不均和边缘小幅偏移。不使用光滑渐变或写实体积塑形。
- 以冷淡灰蓝纸面为基底，使用低饱和海军蓝或炭蓝轮廓、页岩蓝、雾青、旧蓝灰、雾蓝绿和烟熏靛蓝阴影。整体低饱和、低对比、哑光，排除米黄、橙、金和大面积暖棕偏色。
- 光线保持平缓、漫反射和方向克制，只用很软的烟蓝阴影区分层次。不把画面变成黑暗夜景，不使用戏剧化边缘光、聚光或高反差明暗。
- 情绪保持安静、内省、克制和轻微哀愁，呈现成熟的编辑插画气质；不走儿童涂鸦、幼儿绘本、卖萌卡通或狂躁表现主义路线。

## 通用画面风格 Prompt

先用一句话写清当前可识别的具体场景、主体动作和动作结果，再追加下面的风格段。替换方括号内容，不把任何示例场景当作固定模板。

```text
A quiet minimalist 2D editorial illustration of [a concrete subject performing a clearly visible action in a recognizable setting]. Intentionally clumsy hand-drawn simple-line style, naive but mature proportions, slightly oversized round or oval heads, thin bent limbs, tiny dot eyes, and clearly readable poses. Slightly wobbly uneven pencil outlines with occasional broken lines, repeated strokes, imperfect contours, and subtle erasure marks. Restrained colored-pencil fills, a touch of dry pastel, visible coarse paper texture, flat 2D shapes, and large clean negative space. Use a cool pale gray-blue paper background, muted navy and charcoal-blue outlines, desaturated slate blue, dusty teal, weathered blue-gray, foggy blue-green, and very soft smoky indigo shadows. Low saturation, low contrast, matte, quiet, introspective, and gently sorrowful. Keep only the people, objects, and environmental cues required to understand the event. Soft diffuse lighting, not a dark night scene and not dramatic lighting. No warm beige, orange, golden, or dominant brown cast. No decorative clutter, floating symbols, abstract metaphors, dense marks, realistic anatomy, photorealism, 3D rendering, anime features, children's-book cuteness, text, logo, or watermark.
```

## 参考图重着色 Prompt

已有构图和造型正确、只需转换为该风格的参考图时，使用下列结构。在开头明确列出必须保持的主体、位置、姿势、道具和构图，不用“same”笼统代指。

```text
Edit the provided reference image as a strict style-preserving recolor. Keep [explicitly list the subject, pose, composition, objects, and spatial relationships that must remain unchanged]. Preserve the clumsy hand-drawn simple-line style: slightly wobbly uneven pencil outlines, naive but mature proportions, tiny dot eyes, restrained colored-pencil fills, subtle dry pastel, visible coarse paper texture, flat 2D shapes, and an intentionally imperfect appearance. Change the entire palette into a melancholic blue-toned atmosphere. Use a cool pale gray-blue paper background, muted navy and charcoal-blue outlines, desaturated slate-blue clothing and objects, dusty teal details, cold weathered blue-gray materials, foggy blue-green foliage, and very soft smoky indigo shadows. Keep the contrast low, matte, quiet, introspective, and gently sorrowful. Remove warm beige, orange, golden, and dominant brown casts. Do not turn it into a dark night scene, do not add dramatic lighting, and do not add objects, decorations, symbols, dense marks, extra background details, realistic anatomy, photorealism, 3D rendering, anime features, text, logo, or watermark.
```

## 撰写图像 Prompt

1. 优先写一个现实中可以直接发生的具体事件，再写风格。说清谁在什么环境里对什么做了什么，以及画面定格时的可见结果。
2. 构图尽量简单，但不把“简单”理解成抽象。使用少量真实可识别的人物、家具、建筑、道路或自然物交代场景，不用漂浮图形、线团、波纹或概念形变承担主要表达。
3. 生成人物参考图时，默认使用一张无遮挡、全身可见的单人物图固定轮廓、简单五官、发型、头身关系和服装色块，同时保留笨拙比例与不完美线条。背景可以保留简洁纸面或低对比环境；只有剧情需要时才补背面、侧面或标志性道具视图。
4. 忧郁蓝调不等于把所有区域压成同一种深蓝。通过冷淡灰蓝底色、海军蓝轮廓、页岩蓝主色、雾青局部区分物体，再用少量烟熏靛蓝表示阴影。
5. 检查画面是否仍然明亮可读、低对比且具有纸面手作感。如果变成黑暗夜景、蓝色滤镜下的精致商业插画或只有单一深蓝色块，应重新生成。

## 撰写视频 Prompt

1. 为每个镜头设计具体可见的人物行动、物体运动和结果。不用吹气、飘浮气泡、线团、钩子、波纹、情绪颜色变形或空间坍缩代替具体事件。
2. 人物动作可以有轻微迟疑、僵硬和笨拙的重量转移，但要写清起点、方向、路径、速度、接触反馈和终点。
3. 用轻微线条沸腾、轮廓逐帧重画、铅笔深浅变化和色块小幅漂移保持手绘感。这些变化只是辅助，不让全画面同频抖动，也不取代主体动作。
4. 构图优先简洁清楚，通过主体位置、道具和少量环境线索交代空间。多人场景必须明确每个人的初始位置、面朝方向、动作顺序和最终位置。
5. 运镜必须明确说明摄影机起点、屏幕运动方向、与主体的相对位置、运动幅度和终点。风格不预设固定运镜，也不为了“忧郁”而默认所有镜头缓慢推近。
6. 不在卡片、墙面、报告、气泡或漂浮标签上要求模型生成小字。只有用户明确要求画内文字时才加入，否则用简单可识别的图形、物体和动作结果表达。

## 明确排除

- 暖黄、橙金、暖棕统治的温暖怀旧配色，以及单一深蓝滤镜。
- 黑暗夜景、高反差聚光、戏剧化边缘光和强烈电影阴影。
- 干净矢量线、光滑数字渐变、精致商业插画、写实人体、照片质感和三维渲染。
- 日系动漫五官、儿童绘本、幼儿涂鸦、卖萌卡通和狂躁混乱的表现。
- 装饰性细节堆积、浮动文字、抽象符号和以隐喻取代具体叙事。
