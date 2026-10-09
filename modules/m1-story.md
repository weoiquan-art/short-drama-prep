# M1 故事与场景

从一句想法到一场戏：项目简报、场景事件、表演任务。模块正文逐字取自 toolkit 原文（[存档](../references/cinematic-prompt-toolkit-v1.0.0.md)），只把标题降了一级；"本 Skill 的处理"是本仓库加的。

## T01｜项目简报与故事方向

**用途**：把一句想法变成可继续开发的项目。**输入**：主题、片长、类型、人物关系；可选结尾倾向。

**给助手的任务**：围绕我的主题提出一个主方向，说明人物关系、情绪起点与终点、外部事件、关键选择。只补充创作需要的设定；不要自动沿用爱情片或男女追逐结构。列出需要的新资产，但不开始制作它们。

**输出骨架（创作简报）**：

```text
PROJECT: {name}
AUDIENCE EXPERIENCE: {what the viewer should feel or discover}
PREMISE: {person} must {concrete action} before {consequence}.
RELATIONSHIP: {what connects the main characters}
OPENING STATE: {visible condition before the event}
DECISIVE CHOICE: {an action with a cost}
ENDING STATE: {what has changed}
SCOPE: {duration, locations, cast, visual complexity}
ASSETS TO DEFINE: {identities, locations, essential props}
ASSUMPTIONS: {new choices made for this brief}
```

**调用示例**：`T01：做一支 45 秒的亲情短片，父亲修好女儿小时候的录音机，结尾克制，只有一个室内场景。`

## T12｜场景事件设计

**用途**：决定一场戏为什么发生。**输入**：人物、地点、前情和结尾要求。

**给助手的任务**：写一个有因果的场景事件，不先堆镜头。分别说明人物目标、观众已知信息、行动怎样返回新信息，以及结尾变化。

**输出骨架（场景卡）**：

```text
SCENE: {id and setting}
ENTRY CONDITION: {what has just happened}
CHARACTER OBJECTIVE: {an achievable or fail-able result}
RESISTANCE: {external obstacle and internal hesitation}
ATTEMPT: {specific behavior}
NEW INFORMATION: {what the attempt reveals}
ADJUSTMENT: {how the character changes approach}
TURN: {action that changes the situation}
EXIT CONDITION: {new fact and emotional consequence}
AUDIENCE KNOWLEDGE: {known now / withheld until later}
ESSENTIAL VISIBLE EVIDENCE: {actions that must be filmed}
```

**调用示例**：`T12：女修表师想归还怀表，却不想让对方知道自己一直在等；场景结束时她主动走出店门。`

## T13｜表演任务与微反应

**用途**：把“紧张、喜欢、失望”转为可拍的动作。**输入**：场景事件、人物任务、景别与时长。

**给助手的任务**：给每人一个注意对象和一条行为变化。每镜最多突出少数可读反应，听者也有任务。不要把同一组眨眼、吞咽、颤抖套给所有人物。

**输出骨架（表演提示词）**：

```text
{Character} is trying to {task}, while hiding {private concern}.
Their attention stays on {specific person/object/off-screen point}.
Initially they {visible tactic}. When {trigger occurs}, they briefly
{one readable reaction}, then {adjusted behavior}.
The body rhythm is {tempo and weight}; the change is visible through
{gesture/posture/face appropriate to the shot size}.
The listener is occupied with {their own motivated task}.
End with {held action or gaze}, leaving {emotional implication} unstated.
```

**调用示例**：`T13：近景，4 秒；她发现来取表的人没有认出自己，用克制动作表现，不掉眼泪。`
