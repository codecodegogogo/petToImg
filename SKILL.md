---
name: Images of cats and dogs
description: 生成 Ian 风格的中文正文配图。用于用户要求为中文文章、帖子、博客、Notion 文档、工作流文档、方法论、流程、结构、状态、隐喻或观点生成“怪诞”“宠物主角”“手绘”“正文配图”“文章插图”“配图建议”“shot list”“去标题/改图”等任务；默认使用固定三只宠物“小黄、小狗儿、蒂娜”作为视觉主角，支持随机 1、2、3 只组合出现，并可根据宠物图片特征和画面动作添加少量短对话，保持纯白手绘、少量红橙蓝批注、简洁清爽但天马行空的视觉风格。
---

# Ian 宠物怪诞正文配图

## 核心定位

为中文文章设计和生成 16:9 横版正文配图。目标不是做商业插画、PPT 信息图、萌宠海报或可爱卡通，而是把文章里的关键判断、流程、结构、状态或隐喻，变成一张清爽、怪诞、有创意、可读但不说明书的手绘解释图。

固定视觉主角是三只宠物：小黄、小狗儿、蒂娜。它们来自本 skill 文件夹根目录：

```text
./
```

动物名字使用图片文件名。三只宠物必须参与画面的核心动作，不能只是站在旁边当装饰。生成时把宠物转译成 Ian 风格的手绘角色：保留能识别的体态、花色、耳朵、尾巴、姿势习惯和性格差异，但仍使用纯白背景、黑色手绘线稿、少量红橙蓝批注、大量留白和怪诞正文配图语法。

## 样貌一致硬规则

使用 Ian / ifan 风格时，三只宠物的样貌必须和用户提供的图片一致。根目录三张 PNG 是权威参考，不是可选灵感：

```text
小黄.png
小狗儿.png
蒂娜.png
```

生成前必须打开或读取这些图片，确认每只宠物的真实特征。不要只凭文字描述生成“类似的猫狗”。如果当前生图工具不能把参考图作为视觉输入，就必须明确说明只能生成草稿，不能声称样貌严格一致。

必须保持：

- 物种不能变：狗还是狗，猫还是猫。
- 体型比例不能变：小黄是修长大狗，小狗儿是更小更圆的橙黄小狗，蒂娜是黑猫。
- 毛色和花纹不能变：小黄浅黄，小狗儿橙黄且白胸白爪，蒂娜黑毛黄眼。
- 耳朵、尾巴、脸型和典型姿态要尽量贴近参考图。
- 只允许做 Ian 风格的线稿转译，不允许改成通用萌宠、毛绒玩具、贴纸、儿童卡通或新的虚构动物。

提示词里必须出现“match the provided reference images closely / preserve identity from the reference PNGs / do not invent a generic pet”。

## 固定宠物角色

### 小黄

参考图：`小黄.png`

小黄是浅黄大狗，体型修长，腿长，耳朵直立偏大，尾巴常向上卷起。整体气质机警、行动感强，像负责外场执行的人。

适合承担：巡逻、拉路径、开路、守门、快速搬运、发现断点、把东西叼走。

可用短对话：`我先探路` / `这边断了` / `跟上` / `别堵门`

### 小狗儿

参考图：`小狗儿.png`

小狗儿是橙黄小狗，体型更小更圆，白色胸口和白爪明显，一只耳朵常立起，另一只耳朵半垂，表情有点无辜。整体气质好奇、热心、略笨拙但认真。

适合承担：试探、蹲守、被卡住、举手提问、拖小物件、钻进入口、看错方向。

可用短对话：`我试试` / `等等我` / `这是入口吗` / `先别慌`

### 蒂娜

参考图：`蒂娜.png`

蒂娜是黑猫，黄眼睛，尖耳朵，身体线条细长，尾巴灵活。常见姿态有端坐、伏低、抬爪、警惕行走、蜷成一团。整体气质冷静、挑剔，像系统里的审稿人或守门员。

适合承担：观察、判断、按下开关、踩住关键点、钻进暗处、监督、冷静记录。

可用短对话：`不对` / `先看证据` / `这里有洞` / `我按住了`

## 先读这些参考

按任务需要读取，不要一次塞满上下文：

- `references/style-dna.md`：风格 DNA、颜色、文字、禁忌。
- `references/pet-protagonists.md`：如何使用宠物主角、随机组合出场、添加少量短对话。
- `references/pet-roster.md`：当前固定三只宠物的名字、参考图路径、识别特征、性格动作和可用短对话；根目录里的 `pet-roster.md` 是同一角色库的便携说明。
- `references/composition-patterns.md`：结构类型、原创隐喻方法和反复刻规则。
- `references/prompt-template.md`：单张生图提示词模板。
- `references/qa-checklist.md`：生成后检查和迭代规则。
- 根目录三张宠物图：只作为固定角色参考，不要把它们当作要拼贴进画面的素材。

## 工作流

### 1. 消化正文

先读用户给的正文、链接、Notion 页面、Markdown 文件或截图内容。提炼：

- 核心观点是什么
- 哪些段落承担认知转折
- 哪些内容适合用图解释
- 哪些地方只适合文字，不需要图

不要平均配图。优先选择“认知锚点”，例如：核心判断、两个断点、输入输出闭环、分流、前后对比、一鱼多吃、承接路径、常见坑、角色状态变化。

### 2. 选择宠物主角

先读取 `references/pet-protagonists.md`。如果 `references/pet-roster.md` 或根目录 `pet-roster.md` 存在，优先使用其中固定的三只宠物：小黄、小狗儿、蒂娜。

出图时按正文需要选择主角组合：

- 单只：适合一个明确动作、一个判断、一个状态。
- 双只：适合对比、协作、拉扯、输入输出、角色分工。
- 三只：适合系统分流、闭环、多阶段、共同搬运或集体误入一个结构。

不要为了“随机”牺牲表达。随机组合只决定谁出场，画面动作仍必须服务当前正文结构。连续多张图时，尽量轮换三只宠物，让它们都有出现机会。

### 3. 组合建议

- 小黄单独出场：适合推进、开路、寻找断点、承接路径。
- 小狗儿单独出场：适合试错、卡住、提问、误入入口。
- 蒂娜单独出场：适合判断、审核、观察、按住关键点。
- 小黄 + 小狗儿：适合执行与试探，一个往前拉，一个在入口处犹豫。
- 小黄 + 蒂娜：适合推进与审核，一个负责开路，一个负责踩住判断开关。
- 小狗儿 + 蒂娜：适合疑问与纠偏，一个试探，一个冷静判断。
- 小黄 + 小狗儿 + 蒂娜：适合系统分流、闭环、多阶段协作、共同搬运一个抽象物。

### 4. 先出配图策略

如果用户只是说“分析怎么配图 / 思考哪些地方需要配图”，先给 shot list。每张图写清楚：

- 放在哪个段落后
- 图的主题
- 核心意思
- 结构类型
- 宠物主角组合与动作
- 可选短对话
- 建议元素
- 建议中文标注词

默认 4-8 张。文章很短时 1-3 张；长文也不要轻易超过 9 张。够用就好，避免把正文做成画册。

### 5. 单张生成

如果用户明确要求“生成 / 输出 / 做图 / 帮我生成”，不要停下来等确认；用内置 `image_gen` 每张单独生成。不要把多张图拼在一张里。

每张图只讲一个核心结构。提示词必须包含：

- 16:9 横版中文正文配图
- 纯白背景
- 黑色手绘线稿
- 少量红色/橙色/蓝色中文手写批注
- 大量留白
- 宠物主角作为核心动作主体
- 严格参考根目录 PNG，保持宠物样貌和用户提供图片一致，不要只画成类似的猫狗
- 保留宠物可识别特征，但不要画成照片、萌宠海报或儿童卡通
- 可根据宠物图片特征和当前动作添加 0-3 个很短的中文对话气泡
- 禁止 PPT、商业插画、幼稚可爱、复杂架构、左上角类型标题

不要复刻过往案例。案例只提供风格密度和主角参与方式，不能直接复用旧构图，除非用户明确要求复刻某张图。每次都要从当前文章重新发明一个奇怪但成立的隐喻。

## 生图提示词结构

每张图可以按下面结构写提示词：

```text
Generate one standalone 16:9 horizontal Chinese article illustration.

Visual DNA:
Pure white background. Minimalist black hand-drawn line art. Slightly wobbly pen lines. Lots of empty white space. Sparse red/orange/blue handwritten Chinese annotations. Clean absurd product-sketch feeling. No gradients, no shadows, no paper texture, no complex background, no commercial vector style, no PPT infographic look, no cute mascot poster, no children's illustration, no realistic UI.

Recurring protagonist characters required:
Use the three provided pet references as the recurring protagonists: 小黄, 小狗儿, 蒂娜. Convert the selected pet(s) into sparse Ian-style hand-drawn article-illustration characters while matching the provided reference images closely. Preserve identity from the reference PNGs: silhouette, proportions, fur color and pattern, ears, tail, face, posture, and temperament. Do not invent a generic pet. The pet(s) must perform the core conceptual action, not decorate the scene. Keep them deadpan, slightly absurd, clean, and not cute-poster-like. Do not make them realistic photos, plush toys, children's cartoon mascots, stickers, or commercial pet illustrations.

Selected pet combination:
{小黄 / 小狗儿 / 蒂娜 / 小黄+小狗儿 / 小黄+蒂娜 / 小狗儿+蒂娜 / 小黄+小狗儿+蒂娜}

Reference traits to preserve:
{每只出场宠物 2-4 个关键识别特征}

Theme:
{正文配图主题}

Structure type:
{Workflow / 系统局部 / 前后对比 / 角色状态 / 概念隐喻 / 方法分层 / 地图路线 / 小漫画分镜}

Core idea:
{这张图要表达的核心意思}

Composition:
{宠物在哪里、正在做什么、主要物件是什么、信息如何流动；宠物必须承担核心动作}

Suggested elements:
{元素1} / {元素2} / {元素3} / {元素4}

Chinese handwritten labels:
{标注词1} / {标注词2} / {标注词3} / {标注词4}

Dialogue bubbles if useful:
{宠物名：“短句” / 宠物名：“短句”；没有必要就 none}

Color use:
Black for main line art and simplified pet contours/patterns. Orange for main flow/path/arrows. Red only for key warnings/problems/results. Blue only for secondary notes or feedback/system state. Use pet fur colors only as restrained recognition cues if necessary; do not turn the image into a colorful pet poster.

Constraints:
One image explains only one core structure. Keep the main subject around 40%-60% of the canvas. Preserve at least 35% blank white space. Use at most 5-8 short handwritten Chinese labels, including dialogue bubbles. Do not write a title in the top-left corner. Do not write the structure type on the image. Do not make it a formal diagram, course slide, dense explainer, pet portrait, sticker sheet, or cute mascot poster. Invent a fresh visual metaphor for this specific article.
```

## 对话规则

可以根据图片内容、宠物性格和当前正文隐喻添加少量对话。对话不是必需项，只在能增强画面时使用。

- 每张图最多 1-3 个小气泡。
- 每个气泡 2-8 个中文字符。
- 对话要服务结构表达，不要变成段落解释。
- 对话可以暴露角色性格：小黄负责推进，小狗儿负责试探，蒂娜负责判断。
- 不要写大段台词、网络梗、拟人剧情或可爱卖萌口癖。
- 对话气泡也算中文标注，总文字量仍需克制。

## 检查与迭代

生成后检查 `references/qa-checklist.md`。如果出现以下问题，优先重生成或局部编辑：

- 宠物只是装饰
- 宠物失去可识别特征，或过度拟人、过度可爱
- 对话太多、太长、像剧情台词，或盖过正文标注
- 画面太满
- 太像流程图/PPT
- 中文太多或错字严重
- 左上角出现“常见坑/流程图/系统架构图”等标题
- 画风太可爱、幼稚、死板
- 背景不是干净白底

## QA 必过项

- 是 16:9 横版。
- 背景是干净白底。
- 有宠物主角：小黄、小狗儿、蒂娜中的 1-3 只。
- 宠物主角承担核心动作，不只是装饰。
- 宠物样貌必须和根目录参考 PNG 一致；如果像通用猫狗或换了体型/毛色/耳朵/尾巴，直接判定失败。
- 没有复刻旧案例构图，而是为当前文章生成了新隐喻。
- 画面怪诞、有创意、有意思。
- 简洁清爽，主体不超过画面约 60%。
- 一张图只讲一个核心结构。
- 中文标注少、短、能读。
- 橙色只用于主路径或箭头。
- 红色只用于重点、问题、提醒或结果。
- 蓝色只用于补充说明、反馈或系统状态。
- 多只宠物同屏时能区分，不要变成通用猫狗。
- 对话气泡最多 1-3 个，每个 2-8 个中文字符，并且服务当前动作。

## 保存交付

如果用户在 workspace 内工作，把最终图复制到：

```text
assets/<article-slug>-illustrations/
```

按顺序命名：

```text
01-topic-name.png
02-topic-name.png
```

宠物参考图和角色库保存在本 skill 文件夹根目录：

```text
./
```

保留原始生成文件，不要覆盖已有资产，除非用户明确要求替换。

## 输出口径

生成前的策略输出要短而准。生成后的交付要包含：

- 生成了几张
- 每张图的用途
- 使用了哪些宠物主角组合
- 是否添加了对话，以及对话服务的画面动作
- 保存路径
- 哪些图最稳，哪些图是可选

不要长篇解释风格理论；让图自己说话。
