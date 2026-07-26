# Seedance 2.0 电影运镜提示词库

用途：作为后续写入 Codex skill、AI 视频分镜提示包、Seedance 2.0 运镜词典的基础素材。

版本：v1.1  
日期：2026-07-04  
适用模型：Seedance 2.0 / Seedance 2.0 Fast  
适用场景：文生视频、图生视频、视频参考生成、分镜逐镜头提示词

---

## 1. 使用原则

Seedance 2.0 适合生成 4-15 秒的音视频片段，因此单条提示词最好只控制一个核心运镜，不要在同一条里堆叠过多镜头运动。

推荐结构：

```text
{时长}秒电影感单镜头，无剪切。{主体}在{场景}中{动作}。
Camera movement: {明确运镜英文关键词 + 中文说明}。
Shot & lens: {景别、镜头焦段、构图}。
Lighting & color: {光线、色彩}。
Mood: {情绪}。
Audio: {可选环境声/音乐/动作声}。
Style: cinematic realism, natural motion, coherent physics, high detail。
Avoid: random cuts, extra camera movement, text, watermark, distorted face, unstable anatomy。
```

图生视频补充结构：

```text
保持参考图中的人物身份、服装、发型、道具和场景布局一致。仅让摄影机执行{运镜}，主体动作保持自然连续。
```

提示词写法要点：

| 原则 | 说明 |
|---|---|
| 一个镜头一个主运镜 | 比如只写 slow pan right，不要同时写 pan、orbit、zoom、crane |
| 先写主体动作，再写相机动作 | 模型更容易保持叙事因果 |
| 运镜用中英双写 | 中文表达意图，英文关键词锁定摄影术语 |
| 明确速度 | slow / gentle / steady / fast / sudden |
| 明确起点和终点 | from wide shot to close-up / from left to right / reveal the doorway |
| 加入“single continuous shot” | 减少随机切镜 |
| 明确不要什么 | no random cuts, no shaky camera unless handheld |

---

### 1a. 对话镜头的前景层次规则

对话场景不要只写“两个人站着说话”。优先从当前场景中选择一个有叙事关系的物体作为前景、中景或遮挡层，让画面在不拖慢节奏的情况下更丰富。

可用前景类型：

| 前景类型 | 适用对话 | 提示词写法 |
|---|---|---|
| 门框、窗棂、屏风、帘子 | 偷听、隔阂、秘密、身份压迫 | foreground doorframe/window lattice partially frames the speakers |
| 桌案、茶杯、账本、信件、药碗 | 审问、谈判、家庭冲突、证据揭示 | foreground table objects create depth, focus remains on speaking character |
| 肩膀、后脑、袖口、手部 | 对峙、审讯、权力关系、情绪压迫 | over-the-shoulder foreground, opposite character stays sharp |
| 烛火、灯笼、窗光、影子 | 古装夜戏、压抑密谈、危险临近 | foreground candle/lamp flicker, soft occlusion, motivated light |
| 货架、树枝、人群缝隙 | 街市、祠堂、院落、围观场面 | foreground crowd/object layers, no random obstruction |

使用限制：
- 前景必须来自剧本场景已有物件或合理空间，不为“高级感”硬塞无关物。
- 前景遮挡通常控制在画面的 10%-35%；悬念揭示可更高，但落幅必须看清主体。
- 对话的主信息仍然落在说话人的眼神、手部、道具反应或对方表情上。
- 若使用浅景深，写明 focus remains on speaking character 或 rack focus to key object，避免模型把前景误当主体。

---

### 1b. 运镜选择与去推镜化规则

推镜头只在“观众必须靠近某个情绪、证据或关系落点”时使用。若只是想让画面动起来，优先选择固定镜头、横移、摇镜、过肩构图、前景遮挡、跟拍、拉镜或焦点转移。

硬性限制：
- 同一场连续分镜不得连续使用推镜头。
- 每 8-10 个镜头中，CM-02 推镜头最多 1-2 个；除非剧本明确是心理逼近或危险压迫段落。
- 如果一个镜头的终点没有明确落在“表情变化、证据物件、权力关系、身份揭示”之一，禁止使用推镜头。
- 推镜不能替代演员反应。推进过程中必须有眼神、呼吸、手部、转头、道具触碰或对方反应的变化。

非推镜优先替代：

| 叙事任务 | 优先运镜 | 避免误用 |
|---|---|---|
| 让观众观察尴尬或压抑对话 | CM-01 固定镜头 + 前景物件 | 不要用慢推替代沉默 |
| 揭示桌上证据、门外人物、窗外动静 | CM-06 摇镜/俯仰 + 焦点转移 | 不要每个揭示都推近 |
| 展示人物穿过院落、街市、走廊 | CM-04 横移 / CM-10 稳定器跟拍 | 不要正面推着人走 |
| 制造跟随和紧迫 | CM-05 跟拍 / CM-09 手持 | 不要用推镜表现追逐 |
| 表现人物被空间吞没 | CM-03 拉镜 / CM-16 俯拍上升 | 不要反向用推镜放大情绪 |
| 强化权力压迫 | CM-17 仰拍运动 / 过肩前景 | 不要只把脸推大 |
| 关系失衡或对峙 | CM-08 环绕 / CM-11 轨道 / 过肩构图 | 不要连用双方互推 |
| 突发信息或节奏跳变 | CM-12 甩镜 / CM-13 变焦 | 不要用慢推处理突然反应 |

---

## 2. 运镜速查表

| ID | 运镜 | Seedance 关键词 | 常用情绪 |
|---|---|---|---|
| CM-01 | 固定镜头 | locked-off static shot | 克制、观察、压抑、冷静 |
| CM-02 | 推镜头 | slow dolly in / camera pushes in | 逼近、觉醒、紧张、亲密 |
| CM-03 | 拉镜头 | slow dolly out / camera pulls back | 孤独、失落、渺小、告别 |
| CM-04 | 横移 | lateral tracking shot / truck left-right | 流动、旁观、空间展示 |
| CM-05 | 跟拍 | follow shot / tracking behind subject | 代入、追随、逃亡、紧迫 |
| CM-06 | 摇镜头 | pan / tilt | 发现、转移注意、揭示信息 |
| CM-07 | 升降镜头 | crane up/down / boom shot | 庄严、压迫、开阔、坠落 |
| CM-08 | 环绕镜头 | orbit shot / 360 camera move | 眩晕、浪漫、对峙、失控 |
| CM-09 | 手持镜头 | handheld camera | 真实、混乱、不安、临场 |
| CM-10 | 稳定器跟拍 | steadicam / gimbal follow shot | 沉浸、顺滑、现代、行进 |
| CM-11 | 轨道镜头 | dolly track shot | 精准、优雅、仪式、秩序 |
| CM-12 | 甩镜头 | whip pan | 突然、惊讶、动作感、喜剧节奏 |
| CM-13 | 变焦 | optical zoom in/out | 窥视、突兀、荒诞、警觉 |
| CM-14 | 希区柯克变焦 | dolly zoom / vertigo effect | 恐惧、震惊、心理崩塌 |
| CM-15 | 主观镜头 | POV shot / first-person camera | 沉浸、危险、私密、紧张 |
| CM-16 | 鸟瞰/俯拍运动 | overhead shot / aerial top-down move | 命运感、秩序、孤立、宏观 |
| CM-17 | 仰拍运动 | low-angle moving shot | 权力、压迫、英雄感、威胁 |
| CM-18 | 长镜头运动 | long take / oner / continuous tracking shot | 真实、复杂、沉浸、压力累积 |

---

## 3. 逐项提示词

### CM-01 固定镜头 Locked-off Static Shot

使用情况：
对话、审视、压抑场景、喜剧节奏、人物独处、需要让观众观察细节的段落。

情绪与画面：
冷静、客观、克制、像旁观者。画面稳定，人物动作和空间变化成为重点。

Seedance 模板：

```text
{4-8}秒电影感单镜头，无剪切。{主体}在{场景}中{动作}。
Camera movement: locked-off static shot, 摄影机完全固定，没有推拉摇移。
Shot & lens: {中景/全景/近景}, {35mm/50mm}, balanced composition。
Lighting & color: {自然光/低调光/冷暖对比}。
Mood: {克制/压抑/安静/尴尬/冷峻}。
Audio: {环境声}。
Style: cinematic realism, natural motion, high detail。
Avoid: camera movement, random cuts, zooming, text, watermark。
```

示例：

```text
6秒电影感单镜头，无剪切。一个疲惫的中年女人坐在凌晨的厨房桌边，手指慢慢摩挲一只旧茶杯。
Camera movement: locked-off static shot, 摄影机完全固定，没有推拉摇移。
Shot & lens: medium shot, 50mm lens, centered composition with negative space。
Lighting & color: dim practical light, muted green and amber tones。
Mood: quiet despair, restrained sadness。
Audio: distant refrigerator hum, faint city ambience。
Style: cinematic realism, natural motion, coherent physics, high detail。
Avoid: camera movement, random cuts, zooming, text, watermark, distorted face。
```

---

### CM-02 推镜头 Slow Dolly In

使用情况：
人物意识到真相、情绪加深、危险逼近、重要物件被发现、关系变得亲密。

情绪与画面：
压迫感、亲密感、命运逼近、心理聚焦。观众被慢慢拉进角色内心。

推镜变体选择：

| 变体 | 适用情境 | Seedance 写法重点 | 避免 |
|---|---|---|---|
| 正轴推进 | 致命台词、真相抵达、角色决断 | camera slowly pushes straight toward the character, from medium shot to close-up | 起幅已经是特写；演员无反应 |
| 侧向推进 | 克制、隐忍、难以说出口的情绪 | camera pushes in from the side, profile remains readable, side light outlines the face | 推到最后变成普通正脸 |
| 横移推进 | 人物行进中情绪逼近、走廊/街道有纵深 | camera trucks sideways while gently pushing closer, foreground/background parallax | 背景空、没有前景层次 |
| 低机位推进 | 威胁、权力、强势登场 | low-angle camera pushes forward slightly upward, subject appears imposing | 过度仰拍导致脸变形 |
| 前景遮挡推进 | 偷听、秘密交易、身份揭示、危险窥视 | camera pushes past foreground obstruction, subject is gradually revealed | 前景无叙事意义或遮挡过多 |
| 斜线推进接揭示 | 察觉、转头、发现第二信息点 | diagonal push toward the character, then a gentle pan/reframe to the revealed object | 推进和摇动同时过猛 |
| 过肩推进 | 审问、对峙、谈判、表白前的心理距离 | over-the-shoulder foreground, camera pushes toward opposite character, focus stays on eyes/object | 前景肩膀过大、对面人物失焦 |

使用门槛：
- 必须写清起幅、落幅和情绪/信息落点。
- 推进路径要与主体动作配合：眼神变化、转头、停步、手指收紧、拿起道具等。
- 对话镜头若使用推镜，优先加入场景前景，例如门框、桌案、茶杯、账本、窗棂、肩膀，使推进有空间层次。
- 不要连续多镜使用 CM-02；下一镜优先换成固定、过肩、摇镜、横移、拉镜或反应特写。

Seedance 模板：

```text
{4-10}秒电影感单镜头，无剪切。{主体}在{场景}中{动作/表情变化}。
Camera movement: slow dolly in / camera pushes in, 摄影机按{正轴/侧向/横移/低机位/前景遮挡/斜线/过肩}路径从{景别A}推进到{景别B}，速度稳定。
Shot & lens: {35mm/50mm/85mm}, shallow depth of field, subject remains sharp。
Foreground/depth: {门框/桌案/茶杯/账本/窗棂/肩膀/人群等场景前景，可选但必须有叙事关系}。
Lighting & color: {光线描述}。
Mood: {紧张/亲密/觉醒/压迫}。
Audio: {呼吸声/低频氛围/环境声}。
Style: cinematic realism, smooth camera motion, natural motion。
Avoid: repeated push-in shots, random cuts, sudden zoom, shaky camera, meaningless foreground, text, watermark。
```

示例：

```text
8秒电影感单镜头，无剪切。一名年轻侦探站在雨夜的档案室里，低头看见照片背面的血迹，眼神从疑惑变成震惊。
Camera movement: slow dolly in / camera pushes in, 前景遮挡推进，摄影机从档案架边缘的遮挡后缓慢推进到侦探手中照片与眼神之间，速度稳定。
Shot & lens: 50mm lens, medium shot to tight close-up, shallow depth of field。
Foreground/depth: foreground file shelves partially frame the character, focus remains on the photo and the detective's eyes。
Lighting & color: cold fluorescent light mixed with blue window light。
Mood: realization, dread, pressure closing in。
Audio: soft rain against glass, low suspense drone。
Style: cinematic realism, smooth camera motion, coherent physics, high detail。
Avoid: repeated push-in shots, random cuts, sudden zoom, shaky camera, meaningless foreground, text, watermark, distorted hands。
```

---

### 运镜替代矩阵（非推镜优先）

下表用于在分镜时主动丰富镜头语言，避免把所有情绪推进都写成 CM-02。

| ID | 核心叙事功能 | 适合加入的前景/空间层 | 优先使用时机 | 禁用或慎用 |
|---|---|---|---|---|
| CM-01 固定 | 让人物动作、对白和空间压力自己发声 | 桌案、门框、窗影、烛火、隔断 | 审问、沉默、尴尬、压抑对话 | 角色没有动作变化时会显拖 |
| CM-03 拉镜 | 从个人情绪退到环境处境 | 门口、长廊、院落纵深、空座位 | 告别、孤立、败局、场尾留白 | 需要揭示细节时不如摇镜/特写 |
| CM-04 横移 | 展示并列信息和空间流动 | 柱子、货架、人群、窗框形成视差 | 街市、走廊、祠堂、两组人对照 | 背景无层次时不要硬横移 |
| CM-05 跟拍 | 让观众跟角色一起进入未知 | 肩后、门洞、走廊转角 | 夜探、逃跑、赶路、进入新空间 | 安静对话不宜用 |
| CM-06 摇镜 | 把注意力从 A 交给 B | 前景物件到人物、人物视线到道具 | 发现线索、转移视线、揭示门外人 | 不要同时加推拉 |
| CM-07 升降 | 从局部到全局，或把命运压下来 | 建筑梁柱、台阶、院落层级 | 场面规模、祠堂/大厅、身份地位 | 小房间对话慎用 |
| CM-08 环绕 | 关系旋转、心理失衡、对峙互锁 | 两人中间的桌案、烛火、雨伞 | 情感高点、对峙逆转、被围困 | 普通对白慎用，容易过度炫技 |
| CM-09 手持 | 真实、混乱、不安 | 人群擦肩、门框快速掠过、手电光 | 争执、突发、追逃、危险现场 | 日常平稳戏慎用 |
| CM-10 稳定器跟拍 | 平滑穿行，交代路线和任务 | 门洞、走廊、办公桌、街边摊位 | 行进对话、角色执行任务、进入场面 | 情绪定点爆发不宜一直跟 |
| CM-11 轨道 | 精准、仪式、可控压迫 | 对称门框、桌案轴线、审判席 | 登场、审判、谈判、正式场合 | 生活化临场戏慎用 |
| CM-12 甩镜 | 快速转移信息和节奏突变 | 从道具/人物甩到新入场者 | 突然闯入、喜剧反应、危险出现 | 落点不清晰时禁用 |
| CM-13 变焦 | 人工窥视、监控感、突然聚焦 | 窗户、屏幕、远处人群 | 监视、警觉、荒诞、综艺感 | 古典电影质感慎用 |
| CM-14 希区柯克变焦 | 心理空间崩塌 | 走廊、楼梯、长桌、门洞 | 噩耗、身份暴露、恐惧失控 | 普通惊讶不要用 |
| CM-15 POV | 观众进入角色眼睛 | 手、袖口、门缝、手电、遮挡物 | 偷看、潜入、受伤、恐惧探索 | 群戏关系交代不宜用 |
| CM-16 俯拍 | 命运俯视和棋局空间 | 院落格局、街道线条、人群阵列 | 群体调度、孤立、宏观转场 | 情绪细节不足 |
| CM-17 仰拍 | 权力、威胁、英雄感 | 桌边、台阶、衣摆、武器/道具边缘 | 强势人物登场、压迫谈判 | 人设不强时会失真 |
| CM-18 长镜头 | 连续压力和复杂调度 | 门、走廊、桌椅、人群作为路径节点 | 追逐、赶场、群戏连锁反应 | 信息单一时不要硬做长镜头 |

选择口诀：
- 看人说话，先想固定/过肩/前景，不急着推。
- 看人移动，先想横移/跟拍/稳定器，不急着推。
- 看信息揭示，先想摇镜/焦点转移/遮挡揭示，不急着推。
- 看关系变化，先想过肩/轨道/环绕/拉镜，不急着推。
- 看心理崩塌，先确认是否值得使用 CM-14；不要用普通推镜替代强心理效果。

---

### CM-03 拉镜头 Slow Dolly Out

使用情况：
揭示环境、人物被世界吞没、分离告别、故事结尾留白、从私人情绪扩展到整体处境。

情绪与画面：
孤独、失落、渺小、疏离。画面从人物扩展到环境，强调人与空间的关系。

Seedance 模板：

```text
{5-12}秒电影感单镜头，无剪切。{主体}在{场景}中{动作}。
Camera movement: slow dolly out, 摄影机从{近景/中景}缓慢后退到{全景/远景}，逐渐揭示周围环境。
Shot & lens: {24mm/35mm}, expanding composition, subject becomes smaller in frame。
Lighting & color: {光线描述}。
Mood: {孤独/失落/告别/无力}。
Audio: {环境声/音乐渐弱}。
Style: cinematic realism, smooth camera motion, natural motion。
Avoid: random cuts, zooming instead of dolly, text, watermark。
```

示例：

```text
10秒电影感单镜头，无剪切。一个少年独自站在空荡的火车站月台上，手里攥着一张揉皱的车票。
Camera movement: slow dolly out, 摄影机从medium close-up缓慢后退到wide shot，逐渐揭示空无一人的长月台。
Shot & lens: 35mm lens, expanding composition, subject becomes small in the frame。
Lighting & color: pale sodium lights, cool blue shadows。
Mood: loneliness, farewell, quiet helplessness。
Audio: distant train rumble, soft wind。
Style: cinematic realism, smooth camera motion, coherent physics, high detail。
Avoid: random cuts, zooming instead of dolly, text, watermark, extra people。
```

---

### CM-04 横移 Lateral Tracking / Truck Shot

使用情况：
人物行走、展示空间关系、横向揭示多个信息点、对比两组人物、制造“旁观生活”的流动感。

情绪与画面：
流畅、观察、生活感、空间感。观众像在旁边同步移动。

Seedance 模板：

```text
{5-10}秒电影感单镜头，无剪切。{主体}在{场景}中从{位置A}移动到{位置B}。
Camera movement: lateral tracking shot / truck {left/right}, 摄影机与主体平行横移，保持稳定距离。
Shot & lens: {全景/中景}, {24mm/35mm}, side profile composition。
Lighting & color: {光线描述}。
Mood: {流动/旁观/轻盈/紧张}。
Audio: {脚步声/街道声/环境声}。
Style: cinematic realism, smooth side tracking, natural motion。
Avoid: random cuts, camera shake, sudden zoom, text, watermark。
```

示例：

```text
7秒电影感单镜头，无剪切。一个穿黑色风衣的女人沿着夜市摊位快速行走，霓虹灯在她脸上流动。
Camera movement: lateral tracking shot / truck right, 摄影机与主体平行横移，保持稳定距离。
Shot & lens: medium full shot, 35mm lens, side profile composition。
Lighting & color: colorful neon lights, wet pavement reflections。
Mood: urban tension, purposeful movement。
Audio: layered street ambience, footsteps, distant vendors。
Style: cinematic realism, smooth side tracking, coherent physics, high detail。
Avoid: random cuts, camera shake, sudden zoom, text, watermark。
```

---

### CM-05 跟拍 Follow Shot / Tracking Behind Subject

使用情况：
逃亡、追逐、进入未知空间、角色穿过复杂环境、观众需要跟角色同步体验。

情绪与画面：
代入、紧迫、陪伴、探索。观众像跟在角色身后。

Seedance 模板：

```text
{6-12}秒电影感单镜头，无剪切。{主体}穿过{场景}，正在{动作}。
Camera movement: follow shot / tracking behind subject, 摄影机从主体身后跟拍，距离稳定，轻微自然起伏。
Shot & lens: {24mm/35mm}, over-the-shoulder or rear tracking composition。
Lighting & color: {光线描述}。
Mood: {紧迫/探索/危险/沉浸}。
Audio: {脚步/呼吸/环境声}。
Style: cinematic realism, immersive camera movement, natural motion。
Avoid: random cuts, losing the subject, excessive shake, text, watermark。
```

示例：

```text
9秒电影感单镜头，无剪切。一名护士推开医院地下走廊的门，急促地向深处奔跑，灯管一盏盏闪烁。
Camera movement: follow shot / tracking behind subject, 摄影机从主体身后跟拍，距离稳定，轻微自然起伏。
Shot & lens: 24mm lens, over-the-shoulder rear tracking composition。
Lighting & color: flickering fluorescent lights, cold green-white palette。
Mood: urgency, fear, immersive suspense。
Audio: fast footsteps, breath, buzzing lights。
Style: cinematic realism, immersive camera movement, coherent physics, high detail。
Avoid: random cuts, losing the subject, excessive shake, text, watermark。
```

---

### CM-06 摇镜头 Pan / Tilt

使用情况：
跟随角色视线、从一个信息点转到另一个信息点、揭示门后/窗外/高处/低处的关键内容。

情绪与画面：
发现、观察、悬念、注意力转移。镜头像人的视线一样转过去。

Seedance 模板：

```text
{4-8}秒电影感单镜头，无剪切。{主体/物件A}位于画面{位置}，随后揭示{主体/物件B}。
Camera movement: slow pan {left/right} / slow tilt {up/down}, 摄影机原地缓慢摇动，从{A}转向{B}。
Shot & lens: {35mm/50mm}, controlled composition, reveal at the end。
Lighting & color: {光线描述}。
Mood: {发现/悬疑/庄严/不安}。
Audio: {环境声/提示音}。
Style: cinematic realism, smooth camera rotation, natural motion。
Avoid: random cuts, dolly movement, excessive speed, text, watermark。
```

示例：

```text
6秒电影感单镜头，无剪切。画面开始在一只掉在地上的红色高跟鞋上，随后揭示黑暗走廊尽头半开的房门。
Camera movement: slow pan right, 摄影机原地缓慢向右摇动，从红色高跟鞋转向半开的房门。
Shot & lens: 50mm lens, low angle composition, reveal at the end。
Lighting & color: dim tungsten light, deep shadows。
Mood: suspense, unease, discovery。
Audio: faint floor creak, distant dripping water。
Style: cinematic realism, smooth camera rotation, coherent physics, high detail。
Avoid: random cuts, dolly movement, excessive speed, text, watermark。
```

---

### CM-07 升降镜头 Crane / Boom Up Down

使用情况：
展示场面规模、人物地位变化、仪式感、压迫感、从细节上升到全局，或从宏观下降到人物。

情绪与画面：
上升时开阔、庄严、释放；下降时压迫、命运落下、逼近角色。

Seedance 模板：

```text
{6-12}秒电影感单镜头，无剪切。{主体}位于{场景}中，正在{动作}。
Camera movement: crane {up/down} / boom {up/down}, 摄影机垂直{上升/下降}，从{景别A}过渡到{景别B}。
Shot & lens: {24mm/35mm}, vertical reveal, stable motion。
Lighting & color: {光线描述}。
Mood: {庄严/开阔/压迫/坠落感}。
Audio: {环境声/低频音乐}。
Style: cinematic realism, smooth vertical camera motion, high detail。
Avoid: random cuts, orbiting, sudden zoom, text, watermark。
```

示例：

```text
10秒电影感单镜头，无剪切。一名新郎独自站在空旷礼堂中央，手里拿着没有送出的戒指。
Camera movement: crane up, 摄影机从medium shot缓慢上升到high wide shot，逐渐揭示整座空礼堂。
Shot & lens: 24mm lens, vertical reveal, stable motion。
Lighting & color: soft morning light through stained glass, pale gold and blue。
Mood: solemn loneliness, emotional emptiness。
Audio: faint room tone, distant church bell。
Style: cinematic realism, smooth vertical camera motion, coherent physics, high detail。
Avoid: random cuts, orbiting, sudden zoom, text, watermark, extra guests。
```

---

### CM-08 环绕镜头 Orbit Shot

使用情况：
爱情高点、心理眩晕、人物被包围、决斗对峙、角色关系发生逆转。

情绪与画面：
浪漫、眩晕、失控、命运感。背景旋转，主体成为情绪中心。

Seedance 模板：

```text
{5-10}秒电影感单镜头，无剪切。{主体}站在{场景}中，正在{动作/对视/沉默}。
Camera movement: slow orbit shot, 摄影机围绕主体{180/360}度缓慢环绕，主体始终保持画面中心。
Shot & lens: {35mm/50mm}, stable orbit, shallow depth of field。
Lighting & color: {光线描述}。
Mood: {浪漫/眩晕/失控/对峙}。
Audio: {音乐/环境声/呼吸声}。
Style: cinematic realism, smooth circular camera motion, natural motion。
Avoid: random cuts, changing subject identity, excessive blur, text, watermark。
```

示例：

```text
8秒电影感单镜头，无剪切。两个多年未见的恋人在雨后的街口相对而立，谁也没有先开口。
Camera movement: slow orbit shot, 摄影机围绕两人180度缓慢环绕，两人始终保持画面中心。
Shot & lens: 50mm lens, stable orbit, shallow depth of field。
Lighting & color: soft streetlights reflected on wet asphalt, warm and cool contrast。
Mood: unresolved romance, emotional dizziness。
Audio: light rain dripping, quiet city ambience。
Style: cinematic realism, smooth circular camera motion, coherent physics, high detail。
Avoid: random cuts, changing faces, excessive blur, text, watermark。
```

---

### CM-09 手持镜头 Handheld Camera

使用情况：
战争、灾难、争吵、逃亡、纪录感场面、角色心理不稳、突发事件现场。

情绪与画面：
真实、粗粝、不安、混乱、临场感。抖动要有控制，不等于画面失控。

Seedance 模板：

```text
{5-10}秒电影感单镜头，无剪切。{主体}在{场景}中{动作}。
Camera movement: handheld camera, 轻微不稳定的手持摄影，跟随主体动作，有真实临场感。
Shot & lens: {24mm/35mm}, close and immersive framing。
Lighting & color: {自然光/低照度/混乱光源}。
Mood: {恐慌/争执/危险/纪录感}。
Audio: {呼吸/喊声/环境噪声}。
Style: cinematic realism, documentary feeling, natural motion。
Avoid: excessive shake, random cuts, smooth gimbal look, text, watermark。
```

示例：

```text
7秒电影感单镜头，无剪切。一名记者穿过混乱的街头抗议现场，回头躲避飞来的碎玻璃。
Camera movement: handheld camera, 轻微不稳定的手持摄影，跟随主体动作，有真实临场感。
Shot & lens: 24mm lens, close and immersive framing。
Lighting & color: harsh streetlights, smoke, red and blue emergency flashes。
Mood: panic, danger, documentary realism。
Audio: shouting crowd, sirens, running footsteps。
Style: cinematic realism, documentary feeling, coherent physics, high detail。
Avoid: excessive shake, random cuts, smooth gimbal look, text, watermark。
```

---

### CM-10 稳定器跟拍 Steadicam / Gimbal Follow

使用情况：
角色穿越空间、城市行走、舞会/宴会/办公区调度、优雅连续运动、沉浸式探索。

情绪与画面：
顺滑、轻盈、现代、沉浸。比手持更稳定，比固定镜头更有流动性。

Seedance 模板：

```text
{6-12}秒电影感单镜头，无剪切。{主体}在{场景}中{行走/穿行/进入空间}。
Camera movement: steadicam / gimbal follow shot, 摄影机平稳跟随主体，运动顺滑，无明显抖动。
Shot & lens: {24mm/35mm}, medium full shot, immersive depth。
Lighting & color: {光线描述}。
Mood: {沉浸/优雅/轻盈/现代/紧张}。
Audio: {环境声/脚步声/音乐}。
Style: cinematic realism, smooth stabilized camera, natural motion。
Avoid: handheld shake, random cuts, sudden zoom, text, watermark。
```

示例：

```text
9秒电影感单镜头，无剪切。一名年轻律师穿过繁忙的开放式办公室，手里拿着即将决定案件走向的文件。
Camera movement: steadicam / gimbal follow shot, 摄影机平稳跟随主体，运动顺滑，无明显抖动。
Shot & lens: 35mm lens, medium full shot, immersive office depth。
Lighting & color: clean daylight, neutral corporate palette with subtle warm highlights。
Mood: focused, modern, quietly tense。
Audio: office ambience, keyboards, measured footsteps。
Style: cinematic realism, smooth stabilized camera, coherent physics, high detail。
Avoid: handheld shake, random cuts, sudden zoom, text, watermark。
```

---

### CM-11 轨道镜头 Dolly Track Shot

使用情况：
精准调度、经典电影感、重要人物登场、仪式化场面、空间线性推进。

情绪与画面：
稳定、优雅、可控、秩序感强。相比普通跟拍，运动路径更精准。

Seedance 模板：

```text
{6-12}秒电影感单镜头，无剪切。{主体}在{场景}中{动作}。
Camera movement: dolly track shot, 摄影机沿直线轨道平滑移动，从{位置A}到{位置B}。
Shot & lens: {35mm/50mm}, precise framing, controlled perspective。
Lighting & color: {光线描述}。
Mood: {优雅/仪式/命运感/秩序}。
Audio: {环境声/音乐}。
Style: cinematic realism, precise dolly movement, high detail。
Avoid: handheld shake, random cuts, curved orbit, text, watermark。
```

示例：

```text
8秒电影感单镜头，无剪切。一位年迈的法官穿过空旷法庭中央，缓慢走向审判席。
Camera movement: dolly track shot, 摄影机沿直线轨道平滑后退，保持人物正面构图。
Shot & lens: 50mm lens, precise symmetrical framing, controlled perspective。
Lighting & color: tall window daylight, dark wood tones, muted gold highlights。
Mood: solemn authority, ritual, moral weight。
Audio: quiet footsteps, faint room echo。
Style: cinematic realism, precise dolly movement, coherent physics, high detail。
Avoid: handheld shake, random cuts, curved orbit, text, watermark。
```

---

### CM-12 甩镜头 Whip Pan

使用情况：
动作切换、突然发现、喜剧反应、从一个角色快速转到另一个角色、制造冲击或节奏跳变。

情绪与画面：
急促、惊讶、混乱、能量强。通常中间有明显运动模糊，落点要清楚。

Seedance 模板：

```text
{4-6}秒电影感单镜头，无剪切。画面从{主体A/方向A}开始，快速转向{主体B/方向B}。
Camera movement: whip pan, 摄影机快速横甩，带自然 motion blur，最后稳定落在{主体B}。
Shot & lens: {24mm/35mm}, fast camera rotation, clear final framing。
Lighting & color: {光线描述}。
Mood: {惊讶/动作感/喜剧节奏/突发危险}。
Audio: {急促声效/转场声/环境声}。
Style: cinematic realism, dynamic motion blur, natural motion。
Avoid: random cuts, losing final subject, excessive blur after landing, text, watermark。
```

示例：

```text
5秒电影感单镜头，无剪切。画面从餐桌上一只被打翻的红酒杯开始，快速转向门口突然出现的陌生人。
Camera movement: whip pan, 摄影机快速向右横甩，带自然motion blur，最后稳定落在门口陌生人身上。
Shot & lens: 35mm lens, fast camera rotation, clear final medium shot。
Lighting & color: warm dinner light, sharp shadow at the doorway。
Mood: sudden shock, suspenseful interruption。
Audio: glass clink, quick air whoosh, room silence。
Style: cinematic realism, dynamic motion blur, coherent physics, high detail。
Avoid: random cuts, losing final subject, excessive blur after landing, text, watermark。
```

---

### CM-13 变焦 Optical Zoom

使用情况：
突然聚焦信息、监控/窥视感、复古纪录感、荒诞喜剧、人物警觉。

情绪与画面：
人工感、窥视感、突兀、警觉。注意区分 zoom 与 dolly：zoom 是机位不动，焦距改变。

Seedance 模板：

```text
{4-8}秒电影感单镜头，无剪切。{主体}在{场景}中{动作}。
Camera movement: optical zoom {in/out}, 摄影机位置不动，仅镜头焦距变化，从{景别A}变为{景别B}。
Shot & lens: visible lens zoom, {documentary/retro/surveillance} feeling。
Lighting & color: {光线描述}。
Mood: {窥视/警觉/荒诞/突然聚焦}。
Audio: {环境声/轻微机械感可选}。
Style: cinematic realism, controlled optical zoom, natural motion。
Avoid: dolly movement, random cuts, excessive shake, text, watermark。
```

示例：

```text
6秒电影感单镜头，无剪切。一个男人站在拥挤的机场大厅里，忽然抬头看向二楼玻璃栏杆。
Camera movement: optical zoom in, 摄影机位置不动，仅镜头焦距变化，从wide shot变为close-up。
Shot & lens: visible lens zoom, subtle surveillance feeling。
Lighting & color: cool airport lighting, polished floor reflections。
Mood: alertness, paranoia, sudden focus。
Audio: muffled airport announcements, rolling suitcase wheels。
Style: cinematic realism, controlled optical zoom, coherent physics, high detail。
Avoid: dolly movement, random cuts, excessive shake, text, watermark。
```

---

### CM-14 希区柯克变焦 Dolly Zoom / Vertigo Effect

使用情况：
人物震惊、恐惧、眩晕、心理崩塌、世界观突然改变、噩耗抵达。

情绪与画面：
空间扭曲、背景拉伸或压缩、强烈心理冲击。提示词要明确“摄影机移动 + 反向变焦”。

Seedance 模板：

```text
{5-8}秒电影感单镜头，无剪切。{主体}在{场景}中突然意识到{事件/真相}，表情发生变化。
Camera movement: dolly zoom / vertigo effect, 摄影机向{前/后}移动，同时镜头反向变焦，主体大小基本保持不变，背景产生空间扭曲。
Shot & lens: centered close-up or medium close-up, distorted background perspective。
Lighting & color: {光线描述}。
Mood: {恐惧/震惊/眩晕/心理崩塌}。
Audio: {低频下沉/耳鸣/环境声抽离}。
Style: cinematic realism, controlled vertigo effect, natural facial expression。
Avoid: random cuts, ordinary zoom only, excessive distortion of face, text, watermark。
```

示例：

```text
7秒电影感单镜头，无剪切。一名父亲站在学校走廊里，听见电话里传来的噩耗，脸上的血色慢慢褪去。
Camera movement: dolly zoom / vertigo effect, 摄影机向前移动，同时镜头反向变焦，主体大小基本保持不变，背景走廊被拉长扭曲。
Shot & lens: centered medium close-up, distorted background perspective。
Lighting & color: cold institutional light, desaturated colors。
Mood: shock, vertigo, psychological collapse。
Audio: faint phone voice, low-frequency drop, muffled hallway ambience。
Style: cinematic realism, controlled vertigo effect, coherent physics, natural facial expression。
Avoid: random cuts, ordinary zoom only, excessive distortion of face, text, watermark。
```

---

### CM-15 主观镜头 POV Shot

使用情况：
潜行、醉酒、受伤、恐惧、第一人称探索、角色视线就是观众视线的段落。

情绪与画面：
强代入、私密、危险、紧张。画面像角色亲眼所见。

Seedance 模板：

```text
{5-10}秒电影感单镜头，无剪切。以{角色}第一人称视角进入{场景}，看到{对象/事件}。
Camera movement: POV shot / first-person camera, 摄影机模拟角色视线和身体移动，轻微自然晃动。
Shot & lens: {24mm/28mm}, immersive first-person framing, optional visible hands。
Lighting & color: {光线描述}。
Mood: {恐惧/好奇/危险/亲密/眩晕}。
Audio: {呼吸声/心跳/环境声}。
Style: cinematic realism, immersive POV, natural motion。
Avoid: third-person view, random cuts, excessive shake, text, watermark。
```

示例：

```text
8秒电影感单镜头，无剪切。以一名受伤警察的第一人称视角穿过废弃公寓走廊，手电光扫过墙上的血迹。
Camera movement: POV shot / first-person camera, 摄影机模拟角色视线和身体移动，轻微自然晃动。
Shot & lens: 24mm lens, immersive first-person framing, one trembling hand holding a flashlight visible。
Lighting & color: narrow flashlight beam, deep shadows, cold blue-gray tones。
Mood: fear, danger, claustrophobic suspense。
Audio: heavy breathing, faint heartbeat, distant pipe noise。
Style: cinematic realism, immersive POV, coherent physics, high detail。
Avoid: third-person view, random cuts, excessive shake, text, watermark。
```

---

### CM-16 鸟瞰 / 俯拍运动 Overhead / Aerial Top-down Move

使用情况：
展示城市、战场、棋局式空间、人物被命运俯视、孤立无援、群体运动。

情绪与画面：
宏观、冷峻、命运感、秩序感。人物显得渺小，空间结构成为主角。

Seedance 模板：

```text
{6-12}秒电影感单镜头，无剪切。{主体/群体}位于{场景}中，正在{动作}。
Camera movement: overhead shot / aerial top-down move, 摄影机从高处俯拍并缓慢{前移/后退/上升/平移}。
Shot & lens: wide top-down composition, geometric layout, subject appears small。
Lighting & color: {光线描述}。
Mood: {命运感/孤立/宏观/冷峻/秩序}。
Audio: {环境声/远处声响/低频音乐}。
Style: cinematic realism, stable aerial movement, coherent spatial layout。
Avoid: random cuts, low angle, losing geometric composition, text, watermark。
```

示例：

```text
10秒电影感单镜头，无剪切。一个穿白色衬衫的男人独自穿过深夜的十字路口，四周空无一人。
Camera movement: overhead shot / aerial top-down move, 摄影机从高处垂直俯拍并缓慢上升。
Shot & lens: wide top-down composition, strong geometric crosswalk layout, subject appears small。
Lighting & color: cold streetlights, black asphalt, white road markings。
Mood: isolation, fate, quiet urban emptiness。
Audio: distant traffic hum, faint wind。
Style: cinematic realism, stable aerial movement, coherent spatial layout, high detail。
Avoid: random cuts, low angle, losing geometric composition, text, watermark。
```

---

### CM-17 仰拍运动 Low-angle Moving Shot

使用情况：
英雄登场、权力人物、威胁对象、巨大建筑/机器、让主体显得强大或压迫。

情绪与画面：
力量、崇高、压迫、危险。观众处在低位，主体具有支配感。

Seedance 模板：

```text
{5-10}秒电影感单镜头，无剪切。{主体}在{场景}中{动作/登场}。
Camera movement: low-angle moving shot, 摄影机位于低角度，随着主体缓慢{推进/后退/横移}。
Shot & lens: {24mm/35mm}, low-angle composition, subject appears powerful。
Lighting & color: {光线描述}。
Mood: {权力/威胁/英雄感/压迫}。
Audio: {脚步/低频音乐/环境声}。
Style: cinematic realism, stable low-angle movement, natural motion。
Avoid: eye-level framing, random cuts, excessive distortion, text, watermark。
```

示例：

```text
7秒电影感单镜头，无剪切。一名女将军从烟雾中走出，身后是燃烧后的战场残骸。
Camera movement: low-angle moving shot, 摄影机位于低角度，随着主体缓慢后退，保持仰拍构图。
Shot & lens: 35mm lens, low-angle composition, subject appears powerful and imposing。
Lighting & color: firelight against cool smoke, high contrast。
Mood: authority, threat, heroic pressure。
Audio: heavy footsteps, distant crackling fire, low percussion。
Style: cinematic realism, stable low-angle movement, coherent physics, high detail。
Avoid: eye-level framing, random cuts, excessive face distortion, text, watermark。
```

---

### CM-18 长镜头运动 Long Take / Oner

使用情况：
复杂空间调度、群戏、追逐、连续危机、角色从一个空间进入另一个空间、需要真实时间压力的段落。

情绪与画面：
沉浸、真实、紧张累积、调度感强。长镜头的重点是连续性和空间逻辑。

Seedance 模板：

```text
{10-15}秒电影感长镜头，无剪切。{主体}从{空间A}移动到{空间B}，过程中发生{连续事件}。
Camera movement: long take / oner / continuous tracking shot, 摄影机连续跟随主体，穿过多个空间，保持动作和空间连续。
Shot & lens: {24mm/35mm}, dynamic composition, clear subject continuity。
Lighting & color: {光线描述}。
Mood: {紧张累积/沉浸/真实/复杂调度}。
Audio: {连续环境声/脚步声/对白/动作声}。
Style: cinematic realism, seamless continuous shot, coherent spatial layout, natural motion。
Avoid: random cuts, teleporting subject, broken spatial continuity, text, watermark。
```

示例：

```text
15秒电影感长镜头，无剪切。一名餐厅经理从后厨穿过狭窄走廊进入拥挤大厅，一边躲开服务员和托盘，一边赶向正在争吵的客人。
Camera movement: long take / oner / continuous tracking shot, 摄影机连续跟随主体，穿过后厨、走廊和大厅，保持动作和空间连续。
Shot & lens: 24mm lens, dynamic composition, clear subject continuity。
Lighting & color: warm kitchen light shifting into elegant dining room amber light。
Mood: escalating pressure, immersive workplace chaos。
Audio: sizzling pans, footsteps, fragments of argument, clinking plates。
Style: cinematic realism, seamless continuous shot, coherent spatial layout, natural motion, high detail。
Avoid: random cuts, teleporting subject, broken spatial continuity, text, watermark, distorted faces。
```

---

## 4. 情绪到运镜的快速映射

| 目标情绪 | 推荐运镜 | 提示词强化方式 |
|---|---|---|
| 紧张逼近 | 跟拍、低角度运动、前景遮挡揭示；必要时少量推镜 | pressure closing in, foreground occlusion, low-frequency drone |
| 孤独失落 | 拉镜头、俯拍上升、固定远景 | subject becomes smaller, negative space, quiet ambience |
| 真实混乱 | 手持、POV、跟拍 | handheld camera, documentary feeling, heavy breathing |
| 浪漫眩晕 | 环绕镜头、横移、固定近景；必要时侧向慢推 | slow orbit shot, shallow depth of field, soft light |
| 权力压迫 | 仰拍运动、轨道镜头、过肩前景；必要时低机位推镜 | low-angle moving shot, imposing, symmetrical framing |
| 宏大命运 | 升降镜头、鸟瞰、拉镜头 | crane up, aerial top-down, subject appears small |
| 突然惊讶 | 甩镜头、快速摇镜、变焦 | whip pan, motion blur, clear final framing |
| 心理崩塌 | 希区柯克变焦、手持近景 | dolly zoom, vertigo effect, muffled sound |
| 冷静观察 | 固定镜头、缓慢横移 | locked-off static shot, restrained mood |
| 沉浸行进 | 稳定器跟拍、长镜头 | gimbal follow shot, seamless continuous shot |

---

## 5. Skill 写入建议

建议在 skill 中拆成三层：

1. `camera_movement_dictionary`
   - 存放 CM-01 到 CM-18 的定义、适用场景、情绪效果、Seedance 关键词。

2. `seedance_prompt_builder`
   - 根据用户输入的主体、场景、动作、情绪、时长，自动套用对应运镜模板。

3. `shot_validation_rules`
   - 检查单条提示词是否违反“一镜一主运镜”。
   - 检查是否写明起点、终点、速度、景别和禁止项。
   - 检查是否出现随机切镜、多重运镜、身份漂移等风险。
   - 检查同一场是否推镜过密：连续推镜禁止，每 8-10 镜最多 1-2 个 CM-02；若超过，优先替换为固定、过肩、摇镜、横移、拉镜、跟拍或前景遮挡揭示。
   - 检查对话镜头是否有空间层次：可从门框、桌案、茶杯、账本、窗棂、肩膀、烛火等场景物体中选择前景，但不得加入剧本中不存在或不合理的摆件。

推荐输出字段：

```yaml
id: CM-06
name_cn: 摇镜头
name_en: slow pan / tilt
best_for:
  - 线索揭示
  - 视线转移
  - 空间信息交代
mood:
  - 悬疑
  - 发现
  - 不安
seedance_keywords:
  - slow pan right
  - slow tilt up
  - controlled reveal
avoid:
  - random cuts
  - dolly movement
  - excessive speed
```

---

## 6. 通用负面提示词

可按需追加到所有 Seedance 2.0 运镜提示词末尾：

```text
Avoid: random cuts, extra camera movement, inconsistent character identity, distorted face, distorted hands, broken anatomy, unnatural body motion, flickering, text, subtitles, watermark, logo, overexposed image, underexposed image, low resolution, broken spatial continuity。
```

若指定手持镜头，不要写 `no shaky camera`，改写为：

```text
Avoid: excessive shake, unreadable image, random cuts, losing the subject, text, watermark。
```

若指定甩镜头，不要完全禁止 motion blur，改写为：

```text
Avoid: excessive blur after landing, losing final subject, random cuts, text, watermark。
```

---

## 7. 参考依据

- Seedance 2.0 论文摘要说明：模型支持文本、图像、音频、视频四种输入模态，并支持直接生成 4-15 秒音视频内容，原生输出 480p 与 720p。参考：[Seedance 2.0: Advancing Video Generation for World Complexity](https://arxiv.org/abs/2604.14148)
- 本提示词库的运镜分类基于通用电影摄影术语与分镜执行经验整理；Seedance 2.0 未公开统一的官方“运镜提示词语法”，因此这里采用中英双写、单镜头、单主运镜、明确起止状态的稳健写法。
