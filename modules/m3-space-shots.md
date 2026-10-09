# M3 空间与分镜

空间地图与机位表、分镜草图、镜头表与时长预算、分镜静帧。模块正文逐字取自 toolkit 原文（[存档](../references/cinematic-prompt-toolkit-v1.0.0.md)），只把标题降了一级；"本 Skill 的处理"是本仓库加的。

> 本 Skill 的处理（非 toolkit 原文）：T14 的镜头表和 T15 的首帧交给提示词 Skill 写视频提示词——真人／写实交 jin-realism-video-prompt，Q 版 Chibi 交 chibi-，其他交通用视频 Skill。toolkit 的 T16、T17（视频提示词模板）不在本 Skill。

## T09｜空间地图与正反拍

**用途**：防止方向翻转与空间跳变。**输入**：地点、人物位置、运动方向、必要机位。

**给助手的任务**：建立世界坐标和镜头坐标的映射，输出文字地图、机位表，以及可选俯视图提示词。相机转向可以改变画面左右，不能改变世界地标。

**输出骨架（布局方案／图像提示词）**：

```text
WORLD MAP
Origin: {fixed point}; forward axis: {direction}; height reference: {floor}.
Fixed landmarks: {positions}; people: {start positions and orientations}.
Travel paths: {start → destination}; forbidden crossings: {if relevant}.
CAMERA MAP
For each shot: {camera side, height, aim, near-to-far layers,
screen-left/right result, eyeline target}.

Optional layout image:
Draw a simple overhead production plan of {location}, showing
{landmarks, people, routes and camera positions}. Use clear spacing.
Annotations are allowed for this planning diagram, not for final footage.
The diagram controls geography, not the final film's visual style.
```

**调用示例**：`T09：两人隔着修钟店柜台说话，规划南侧主机位和两个过肩反拍，不越轴。`

## T11｜分镜草图与复杂动作调度

**用途**：验证跳跃、交接、遮挡、车辆运动等关系。**输入**：场景地图、动作、关键时刻、身份参考。

**给助手的任务**：选最需要澄清的关键时刻，输出草图提示词。每格注明时间角色：首帧、途中姿势或尾帧。需要多格时分别描述，不能同时要求一张图处于多个状态。

**输出骨架（草图提示词）**：

```text
Draw a production storyboard sketch for {shot ID}.
Temporal role: {first frame / key intermediate instant / final frame}.
Camera: {position, height, direction and approximate framing}.
Near-to-far layers: {foreground, subject, destination, background}.
Freeze the action at {one exact physical moment}.
Show {body orientation}, {support/contact point} and {travel direction}.
Keep {essential landmarks} readable; omit decorative detail.
Use simple monochrome contours. Arrows or planning labels may be used
only if requested; they are not elements of the final filmed scene.
Reference scope: blocking and composition only.
```

**调用示例**：`T11：画出“左手递怀表，另一人的右手尚未碰到”的接触前关键帧提示词。`

## T14｜镜头表与时长预算

**用途**：把场景变成可执行分镜。**输入**：场景卡、目标片长、必保留动作／台词、资产清单。

**给助手的任务**：按照剧情信息拆镜，给每镜一个主要职责。编号、累计时间、镜数一致；明确镜头内部是否允许切镜。对话和复杂动作先做时长估算，超时就调整方案。

**输出骨架（分镜表）**：

```text
SHOT | START–END | PURPOSE | ASSETS | FIRST FRAME | ACTION
     | CAMERA | PERFORMANCE | LAST FRAME | SOUND | STATE CHANGE

TIMING CHECK
Sum of shot durations: {total}.
Dialogue estimate: {word count / assumed pace + pauses}.
Physical action allowance: {time and basis}.
Transitions: {hard cuts or overlaps; how overlaps affect total}.
Open assumptions: {uncertain durations or missing inputs}.
```

**调用示例**：`T14：把修钟店归还怀表的一场戏拆成 24 秒，4 镜，无台词，最后停在门外的选择。`

## T15｜单个分镜静帧

**用途**：为某一镜生成首帧／关键帧提示词。**输入**：镜头卡、人物与地点资料、当前道具状态。

**给助手的任务**：输出一个瞬间的图像提示词。优先交代空间关系与身体姿势，保留实际存在的参考。镜头计划中的未来动作，不应在首帧提前完成。

**输出骨架（图像提示词）**：

```text
Film still for {shot ID}, representing {temporal role}.
In {location}, {character} stands/sits at {world position}, facing
{direction}, with gaze directed toward {target}.
At this instant, {single frozen action}; {prop} is {exact state}.
Camera is {height and position}, looking toward {target}; framing is
{shot size}, with {foreground/midground/background arrangement}.
Identity follows {available identity source}; location follows
{available location source}, with this shot's own camera.
Lighting: {source and visible effect}; texture: {project treatment}.
Aspect ratio: {ratio}; keep {important feature} readable.
```

**调用示例**：`T15：SHOT_003 首帧，她已转头看门口，怀表仍在左手，尚未迈步。`
