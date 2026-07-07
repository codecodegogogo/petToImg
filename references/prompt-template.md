# 生图提示词模板

每张图单独生成。根据正文内容替换变量，不要把多张图拼在一起。

用户要求生成 Ian 风格中文正文配图时，先读 `references/pet-protagonists.md` 和 `references/pet-roster.md`，再使用这个模板。每张图根据正文结构选择 1-3 只宠物组合，不要把三只宠物机械塞进每一张图。可以根据宠物图片特征和画面动作加入 0-3 个很短的中文对话气泡。

```text
Generate one standalone 16:9 horizontal Chinese article illustration.

Visual DNA:
Pure white background. Minimalist black hand-drawn line art. Slightly wobbly pen lines. Lots of empty white space. Sparse red/orange/blue handwritten Chinese annotations. Clean absurd product-sketch feeling. No gradients, no shadows, no paper texture, no complex background, no commercial vector style, no PPT infographic look, no cute mascot poster, no children's illustration, no realistic UI.

Recurring protagonist characters required:
Use the three provided pet reference PNGs as the recurring protagonists: 小黄, 小狗儿, 蒂娜. Match the provided reference images closely and preserve identity from the reference PNGs. Convert the selected pet(s) into sparse Ian-style hand-drawn article-illustration characters, preserving each pet's recognizable silhouette, body proportions, fur color and pattern, ears, tail, face, posture, and temperament. Do not invent a generic pet. The pet(s) must perform the core conceptual action, not decorate the scene. Keep them deadpan, slightly absurd, clean, and not cute-poster-like. Do not make them realistic photos, plush toys, children's cartoon mascots, stickers, or commercial pet illustrations.

Selected pet combination:
{小黄 / 小狗儿 / 蒂娜 / 小黄+小狗儿 / 小黄+蒂娜 / 小狗儿+蒂娜 / 小黄+小狗儿+蒂娜}

Reference image fidelity requirement:
{必须贴近根目录参考 PNG；不能只画成类似猫狗；如果无法附带参考图，只能声明为草稿}

Reference traits to preserve:
{每只出场宠物 2-4 个关键识别特征，优先来自 references/pet-roster.md}

Theme:
{正文配图主题}

Structure type:
{结构类型：Workflow / 系统局部 / 前后对比 / 角色状态 / 概念隐喻 / 方法分层 / 地图路线 / 小漫画分镜}

Core idea:
{这张图要表达的核心意思}

Composition:
{具体画面：宠物在哪里、正在做什么、主要物件是什么、信息如何流动；宠物必须承担核心动作}

Suggested elements:
{元素1} / {元素2} / {元素3} / {元素4}

Chinese handwritten labels:
{标注词1} / {标注词2} / {标注词3} / {标注词4} / {可选标注词5}

Dialogue bubbles if useful:
{宠物名：“短句” / 宠物名：“短句”；没有必要就 none。每个气泡 2-8 个中文字符，像手写批注的一部分，不要解释正文。}

Color use:
Black for main line art and simplified pet contours/patterns. Orange for main flow/path/arrows. Red only for key warnings/problems/results. Blue only for secondary notes or feedback/system state. Use pet fur colors only as very restrained recognition cues if necessary; do not turn the image into a colorful pet poster.

Constraints:
One image explains only one core structure. Keep the main subject around 40%-60% of the canvas. Preserve at least 35% blank white space. Use at most 5-8 short handwritten Chinese labels, including any dialogue bubbles. Do not write a title in the top-left corner. Do not write the structure type on the image. Do not make it a formal diagram, course slide, dense explainer, pet portrait, sticker sheet, or cute mascot poster. Do not copy prior examples or reuse known case compositions unless explicitly requested; invent a fresh visual metaphor for this specific article. It should be clear but not instructional, interesting but not childish, strange but clean.
```

## 图像编辑提示

去掉左上角标题：

```text
Edit the provided image. Remove only the handwritten title "{要删除的文字}" and its underline from the top-left corner. Fill that area with the same clean white background, matching the surrounding blank paper. Preserve everything else exactly: characters, labels, paths, line style, composition, aspect ratio, and image quality. Do not add any new text or objects.
```

增强怪诞感：

```text
Regenerate this illustration with the same core meaning and simple layout, but make the pet protagonist more central to the conceptual action. The pet should be doing the strange work that explains the idea, not standing beside the diagram. Keep it clean, sparse, hand-drawn, and not cute.
```