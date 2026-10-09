# M4 声音与转场

对白、声音与口型时间表；转场、动作匹配与声音桥。模块正文逐字取自 toolkit 原文（[存档](../references/cinematic-prompt-toolkit-v1.0.0.md)），只把标题降了一级；"本 Skill 的处理"是本仓库加的。

## T18｜对白、声音与口型时间表

**用途**：自然对话、现场声、旋律与动作同步。**输入**：原台词、角色、语言、时间窗口；可选真实音频参考。

**给助手的任务**：保留用户台词，区分说话、停顿、动作与声音。估算而不伪称实测；若没有旋律文件，不能声称逐音匹配。声音参考的旋律、节奏与音色分开指定。

**输出骨架（声音计划）**：

```text
VOICE: {speaker, language, delivery and room-sized volume}.
TIMELINE
{start–end}: {speaker} says "{exact supplied line}".
{start–end}: {pause / listening response / physical action}.
AMBIENCE: {source, distance, continuity across cuts}.
AUDIO REFERENCE: {actual source, if supplied}; use {melody/rhythm/etc.},
with voice identity treated separately according to the user's request.
SYNC: {gesture, mouth movement or sound cue and its trigger}.
TIME BUDGET: {speech estimate + pauses + actions + optional melody}.
If over budget: {extend, split, or propose a shorter version for review}.
```

**调用示例**：`T18：两人分别说“修好了？”“还差一分钟。”，给 8 秒，保留一段不尴尬的停顿和钟声。`

## T19｜转场、动作匹配与声音桥

**用途**：连接场景或时代。**输入**：前镜尾帧、后镜首帧、转场意义、哪些元素可变化。

**给助手的任务**：选择一种主要连接机制。说明画面切点、可匹配的形状或方向、声音起止和新的时空信息。不能只写“无缝电影转场”。

**输出骨架（转场计划）**：

```text
OUTGOING SHOT: {ending pose, object position, direction, sound}.
INCOMING SHOT: {opening pose, matching element, new world state}.
LINK TYPE: {match cut / occlusion / sound bridge / other justified choice}.
CUT TRIGGER: {one observable event}.
VISUAL MATCH: {screen position, size, direction or shape}.
AUDIO HANDOFF: {outgoing sound fade/continue}; {incoming sound onset}.
TIME/PLACE CHANGE: {what changes and how the viewer understands it}.
CONTINUITY EXCEPTION: {any deliberate mismatch}.
Do not require the video generator to perform an unspecified morph.
```

**调用示例**：`T19：旧怀表秒针跳动接到现代车站时钟，用形状匹配和声音桥，明确剪切时刻。`
