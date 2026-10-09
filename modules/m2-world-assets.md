# M2 世界规则与资产

全片视觉规则，人物、道具、空景、群演、尺度的设定卡和图像提示词骨架。模块正文逐字取自 toolkit 原文（[存档](../references/cinematic-prompt-toolkit-v1.0.0.md)），只把标题降了一级；"本 Skill 的处理"是本仓库加的。

> 本 Skill 的处理（非 toolkit 原文）：T04、T05、T07、T10 和 T06、T08 的图像提示词，与 higgs-asset-prep 管的出图有重叠；先放这里，要不要合并由 JIN 定。

## T02｜世界设定与全片视觉规则

**用途**：统一系列镜头。**输入**：时代、类型、氛围、交付画幅；可选参考风格。

**给助手的任务**：把风格描述转成可见的材质、光线、颜色和摄影选择，区分全片固定规则与场景局部变化。解释命名风格怎样体现在画面中，不堆摄影器材名。

**输出骨架（视觉规则）**：

```text
WORLD: {era, place, social and material context}
REALISM: {grounded, theatrical, illustrated, or other chosen treatment}
PALETTE: {dominant family}, supported by {secondary family};
{accent} is reserved for {narrative purpose, if any}.
MATERIAL LANGUAGE: {surface wear, fabric, metals, architecture}
LIGHT LOGIC: {motivated sources and per-scene variation}
CAMERA LANGUAGE: {distance, stability, allowed motivated moves}
IMAGE TEXTURE: {contrast, highlight behavior, grain or clean texture}
DELIVERY: {chosen aspect ratio}; framing protects {essential content}.
FIXED / VARIABLE: {what travels across scenes / what changes locally}
```

**调用示例**：`T02：为一家雨夜修钟店建立暖室内、冷街道的视觉规则；不写品牌器材。`

## T03｜原创人物身份卡

**用途**：先定义“是谁”，暂不拍摄。**输入**：年龄范围、角色功能、个性与背景；如要匹配真人，提供实际参考。

**给助手的任务**：创建独特、可识别的人物，分开永久特征、时代造型和当前状态。原创人物标注为原创；真实人物的看不清特征保留不确定，不编造“精确匹配”。

**输出骨架（身份卡）**：

```text
CHARACTER ID: {id}
ORIGIN: {original design / supplied reference}
CORE IDENTITY: {age range, build, facial proportions, hairline}
RECOGNITION ANCHORS: {three to five stable visible features}
NATURAL VARIATION: {subtle asymmetry and texture}
PRESENCE: {posture and ordinary body rhythm}
STORY ROLE: {what this person wants and tends to hide}
FIXED FEATURES: {must survive changes of costume and location}
CHANGEABLE FEATURES: {styling, wardrobe, temporary condition}
REFERENCE STATUS: {available files or description-only}
```

**调用示例**：`T03：原创一位 48 岁的女修表师，沉静但固执，有辨识度，不要模特感。`

## T04｜角色参考图／三视图

**用途**：生成角色设定图的提示词。**输入**：T03 身份卡或人物描述、服装、参考素材；可选图板比例。

**给助手的任务**：输出三联参考图提示词。明确肖像、正面和背面的任务，保持身份和服装一致。画板太挤时，建议拆为肖像与全身两个资产，不把多个角度混成一个身体。

**输出骨架（图像提示词）**：

```text
Create a character reference board for {character}.
Use {actual reference if supplied} for {identity scope}.
Show three distinct panels: a readable head-and-shoulders portrait,
a full-length front view, and a full-length back view.
Preserve {recognition anchors} in every compatible view.
Wardrobe: {layered outfit, palette, material, fastenings, footwear}.
The two standing views share scale and a ground line.
Use a plain {neutral tone} background and broad diffuse lighting;
retain natural facial and fabric detail without dramatic cast shadows.
Posture is relaxed and informative. Keep the full silhouette and hands
inside the relevant panels. No written labels unless requested.
Board aspect ratio: {ratio}.
```

**调用示例**：`T04：把刚才的女修表师做成肖像、正面、背面参考图提示词，藏青工作围裙，头发有少量灰白。`

## T05｜同一人物跨时代／换职业造型

**用途**：保留身份，生成新造型。**输入**：已有身份卡、新时代／职业、哪些配饰必须保留。

**给助手的任务**：先列保留与替换项，再输出新的角色图提示词。服装应适合人物的经济条件、工作和行动，不把旧时代道具顺带继承。

**输出骨架（图像提示词）**：

```text
Design a new {era / profession} wardrobe for the same {character}.
Keep {facial and body identity anchors} from {available identity source}.
Replace the previous styling with {new hairstyle, clothing layers,
materials, footwear and period-appropriate functional accessories}.
The silhouette communicates {social role and practical needs}.
Palette: {colors}; condition: {new, worn, repaired, weathered}.
Retain {explicitly retained personal item}; omit superseded accessories.
Present {requested views} under neutral reference lighting.
This is a costume variant of the existing identity, not a new person.
```

**调用示例**：`T05：同一位修表师改成近未来轨道站的机械工程师，保留脸和工作习惯，重新设计服装。`

## T06｜关键道具与状态卡

**用途**：创建反复出现、参与动作的物件。**输入**：道具功能、时代、材质、持有者、动作需求。

**给助手的任务**：分开物件永久结构与剧情状态，输出道具图提示词和状态表。关键手柄、开口、铰链、绳带等必须能支持剧情动作。

**输出骨架（图像提示词＋状态）**：

```text
Create an isolated reference of {prop}, intended for {story function}.
Show its silhouette, {working joint / opening / grip}, and material.
Scale: {approximate real-world size or comparison}.
Surface: {base material, wear pattern, distinctive mark}.
Include {additional informative view only if needed}.
Neutral background; clear diffuse light; one consistent object design.

STATE RECORD
Count: {n}; owner: {character or location}; held by: {hand or support}.
Orientation: {direction}; mechanism: {open/closed or other state}.
Changes at: {shot and triggering event}; next state: {result}.
```

**调用示例**：`T06：设计一枚银色怀表，背面有一处月牙形磕痕；后续要从左手交到右手。`

## T07｜空景母版

**用途**：建立新地点。**输入**：地点、时代、空间结构、日夜、天气；不要求人物先存在。

**给助手的任务**：输出不含主要人物的场景参考提示词。先定义可用空间，再定义材料、天气和光。景物可以有自然状态，但不要把多时刻运动写进单张图。

**输出骨架（图像提示词）**：

```text
Create an unoccupied location reference of {place} in {era/time}.
Layout: {main route or room axis}, bounded by {left/right or cardinal
landmarks}; {entrance} connects to {destination}.
Foreground: {anchor}; working midground: {clear action area};
background: {stable depth landmark}.
Materials and wear: {surfaces and their physical condition}.
Lighting comes from {world-space source}; {surfaces} receive its bounce.
Atmosphere: {weather, haze or clear air appropriate to the location}.
Choose a readable overview showing the paths and boundaries.
This plate defines location design; subsequent shots may use new cameras.
Aspect ratio: {ratio}.
```

**调用示例**：`T07：新建雨夜修钟店，后墙有旧钟，南侧临街，东侧门，柜台在中央偏西。`

## T08｜带群演的场景与注意力规则

**用途**：集市、车站、宴会、比赛等。**输入**：地点、人群类型、密度、主角通行路线和主识别色。

**给助手的任务**：分别输出环境参考图提示词和供后续视频使用的人群规则。为主要行动留可行空间；没有主角时也应像真实地点，而非等待主演出场的群众阵列。

**输出骨架（图像＋人群规则）**：

```text
Show {location} occupied by {background population} during {event}.
Distribute people into {groups and activities} at {density by zone}.
Preserve {route / sightline / activity space} for later blocking.
Wardrobe belongs to {era and social context}; individual silhouettes vary.
Reserve {optional color or shape} for the lead design.
Use {motivated lighting} with readable depth.

BACKGROUND MOTION RULES FOR VIDEO
Attention target: {event or work}; travel: {routes and directions}.
Stationary groups: {in-place actions}; mobile groups: {movement}.
Reaction to the lead: {none, subtle, or explicitly motivated}.
Density and passage must remain physically compatible.
```

**调用示例**：`T08：把旧车站变成清晨通勤场景，主角穿芥末黄大衣，留一条沿墙可通过的窄路线。`

## T10｜身高与物体尺度参考

**用途**：巨物、儿童与成人、机器人、车辆等比例关系。**输入**：两个以上对象的身高或尺寸及参考。

**给助手的任务**：先核对数值比例，再给出同平面比较图提示词。身体对齐点应服从实际比例；不确定时不要编造对齐到某个关节。

**输出骨架（图像提示词）**：

```text
Create a scale comparison reference of {A} and {B}.
Dimensions: A = {height}; B = {height}; ratio A:B = {calculated ratio}.
Place both upright on one ground line at the same distance from camera.
Use a near-orthographic front view to reduce perspective distortion.
Show complete silhouettes with adequate margin around the taller figure.
Preserve the supplied identity and body shapes without normalizing heights.
Use restrained line art or neutral shaded forms for clarity.
Include measurements only if requested.
This reference controls relative scale, not pose, lighting or render style.
```

**调用示例**：`T10：一个 1.65 米的维修员与 3.30 米机器人做身高关系图，严格两倍，背景白色。`
