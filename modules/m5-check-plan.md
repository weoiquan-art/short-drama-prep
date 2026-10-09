# M5 检查与制作计划

连续性与矛盾审计；分批制作、候选选择与剪辑计划。模块正文逐字取自 toolkit 原文（[存档](../references/cinematic-prompt-toolkit-v1.0.0.md)），只把标题降了一级；"本 Skill 的处理"是本仓库加的。

> 本 Skill 的处理（非 toolkit 原文）：T22 只做计划部分；看过成片之后的候选记录（CANDIDATE RECORD 里的优点与未解决问题）写进 video-exp。成片的失败修复（toolkit T21）在 video-exp。

## T20｜连续性与矛盾审计

**用途**：检查现有提示词，不重新创作整片。**输入**：资产表、镜头表、待检查文本。

**给助手的任务**：找能定位的冲突，给最小修改。检查标识、比例、身体朝向、道具、日夜、光源、剧情先后、时长、声音和观众信息。不要为满足清单而加约束。

**输出骨架（审计表）**：

```text
ISSUE | EXACT LOCATION | CONFLICTING CLAIMS | VISIBLE CONSEQUENCE | PATCH

STATE CHECK: previous ending → next beginning.
REFERENCE CHECK: unique ID → one entity; all used references available.
TIMING CHECK: shot count, continuous boundaries, total duration.
SPATIAL CHECK: world map, camera side, eyelines, scale.
CAUSAL CHECK: an event happens once and before its reaction.
KNOWLEDGE CHECK: reveal not spoiled in an earlier frame.
RESULT: {issues found / no demonstrated conflict}; unverified items: {list}.
```

**调用示例**：`T20：检查这组分镜，重点看左右手、衣服湿度、画幅和时间，不改我的故事。`

## T22｜分批制作、候选选择与剪辑计划

**用途**：把文本方案变成可管理的制作清单。**输入**：镜头表、已有素材、目标时长；可选预算／工具限制。

**给助手的任务**：按人物、地点和难度组织批次，优先明确高风险镜头如何评审。列出备用剪辑方式和接点；不自动生成、不杜撰费用、成功率或平台限制。

**输出骨架（制作计划）**：

```text
BATCH | SHOTS | REQUIRED ASSETS | DEPENDENCIES | REVIEW CRITERIA
CANDIDATE RECORD: {shot ID, take ID, observed strengths, unresolved issues}.
KEEP CRITERIA: {identity, readable action, continuity, usable timing}.
EDIT HANDOFF: {first/last usable frame state, movement, audio bed}.
OPTIONAL HANDLES: {short lead-in/out allowance if feasible}.
FALLBACK COVERAGE: {reaction, insert or alternate framing preserving intent}.
FINAL REVIEW: {story clarity, timing, aspect ratio, audio continuity}.
UNKNOWN LIMITS: {not yet supplied}; do not treat assumptions as platform facts.
```

**调用示例**：`T22：这是一组 8 镜短片，帮我规划先做哪些镜头、怎样挑候选和衔接，只做文字计划。`
