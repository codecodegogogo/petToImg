# 宠物主角替换规则

使用固定三只宠物主角时，读取本文件。目标不是把宠物画成真实照片，也不是做萌宠头像，而是把三只宠物转译成 Ian 风格正文配图里的动作主角。

如果 `references/pet-roster.md` 存在，先读取它；其中的图片文件名就是动物名字，并且已经记录固定参考图、识别特征、性格动作和可用短对话。当前固定宠物资产位于本 skill 文件夹根目录：

```text
../
```

## 建立角色库

若没有固定 roster，先观察用户提供的每只宠物参考图，提炼稳定特征：

- 临时角色名：使用图片文件名，或使用用户给的名字。
- 物种与体型：猫、狗或其他；胖瘦、高矮、长短腿、脸型。
- 关键识别点：毛色、花纹、耳朵、尾巴、鼻口、眼神、特殊姿势、项圈或其他固定物。
- 性格动作：谨慎、莽撞、发呆、监督、搬运、钻洞、占位、拆台、记录等。
- 禁止误画点：容易混淆的花纹、不能丢的颜色、不要添加的服装或道具。

把这些信息写入本次任务上下文；除非用户要求，不要把大段分析输出给用户。

## 视觉一致性优先级

宠物参考图优先级高于风格化。Ian / ifan 风格只能改变线条、留白、批注和怪诞动作，不能改变宠物身份。

执行顺序：

1. 先查看根目录 PNG。
2. 提取每只宠物的真实外形：体型、毛色、耳朵、尾巴、脸型、眼睛、典型姿态。
3. 再决定构图和动作。
4. 生图提示词必须要求 match the provided reference images closely。
5. 如果无法附带参考图，说明只能做草稿，不要承诺样貌一致。

## 转译原则

- 保留宠物的可识别轮廓和 2-4 个关键特征，并尽量与参考 PNG 的样貌一致。
- 使用黑色手绘线稿为主，毛色和花纹只做简化表达；可用少量灰黑块面、短线或留白区分。
- 保持白底、大量留白、红橙蓝短批注。
- 允许宠物有轻微荒诞动作，但不要过度拟人化：可以搬、推、卡住、叼、钻、踩、拉线、守门、分拣；不要穿复杂服装、做夸张表情包、拿商业海报道具。
- 宠物必须参与核心隐喻动作。去掉宠物后图仍完全成立，说明宠物只是装饰，要重写提示词。

## 随机组合规则

每张图从三只宠物中选择 1-3 只出场：

- 单只：一个动作主体，适合“判断、卡点、承接、状态变化”。
- 双只：两个动作主体，适合“对比、协作、拉扯、输入输出、前后变化”。
- 三只：群体动作，适合“分流、闭环、多阶段、系统局部、一鱼多吃”。

随机组合要服从表达：先判断结构需要几只，再从三只中轮换选择。连续多张图避免总是同一只做主角。若用户指定某只必须出现，优先服从用户指定。

## 对话规则

可以根据图片内容、宠物性格和当前正文隐喻添加少量对话。对话不是默认必须有，只在能增强结构理解、角色分工或怪诞感时使用。

- 每张图最多 1-3 个短气泡。
- 每个气泡 2-8 个中文字符。
- 气泡文字要像手写批注的一部分，不能喧宾夺主。
- 对话应来自角色动作：小黄推进、小狗儿试探、蒂娜判断。
- 不要写大段台词、解释正文、网络梗、卖萌口癖。
- 如果中文生成容易出错，减少气泡数量或改成更短的词。

## Shot List 写法

使用宠物时，shot list 里写“宠物主角组合与动作”：

```text
宠物主角组合：小黄 + 蒂娜
动作：小黄在前面拉一条橙色路径线，蒂娜踩住一个黑色判断开关，表示推进和审核同时发生。
可选对话：小黄“跟上”，蒂娜“不对”。
```

## 生图提示词补充

在 `references/prompt-template.md` 的角色段落中替换为：

```text
Recurring protagonist characters required:
Use the provided pet references as the recurring protagonists. Convert the selected pet(s) into sparse Ian-style hand-drawn article-illustration characters, preserving each pet's recognizable silhouette, fur pattern, ears, tail, posture, and temperament. The pet(s) must perform the core conceptual action, not decorate the scene. Keep them deadpan, slightly absurd, clean, and not cute-poster-like. Do not make them realistic photos, plush toys, children's cartoon mascots, stickers, or commercial pet illustrations.

Selected pet combination:
{小黄 / 小狗儿 / 蒂娜 / 小黄+小狗儿 / 小黄+蒂娜 / 小狗儿+蒂娜 / 小黄+小狗儿+蒂娜}

Reference traits to preserve:
{每只宠物 2-4 个关键识别特征，优先来自 references/pet-roster.md}

Optional tiny dialogue bubbles:
{0-3 个短中文气泡；没有必要就写 none}
```

如果 image generation 支持附带参考图，把三只宠物图作为参考输入；如果不能附带参考图，就把 `references/pet-roster.md` 里的识别特征写进提示词。

## QA 加项

使用宠物时额外检查：

- 三只宠物至少能从体态、花纹或姿势上区分。
- 宠物没有变成通用猫狗、毛绒玩具或儿童卡通。
- 宠物在做核心动作，而不是站在旁边。
- 多张图之间主角组合有变化。
- 对话气泡少而短，不抢正文标注的位置。
- 图仍然是正文配图，不是宠物写真或萌宠海报。
