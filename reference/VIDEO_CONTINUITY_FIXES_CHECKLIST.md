# 视频穿帮修复与 14 项连续性终审清单 (Continuity & Fixes Checklist)

本规约作为 `jmcai-shotlist-builder-beta` 的防穿帮终审工具箱。用于在最终交付工单或生成提示词前，排查所有跨镜头、跨片段的时空穿帮与逻辑破绽，并为常见的 AI 视频翻车提供即插即用的修复咒语。

---

## 一、 14 项连续性终审自检表 (Pre-Delivery Checklist)

在分镜工单输出或提交生成前，逐项核对以下 14 项指标。**只要有 1 项不符，立即修正：**

- [ ] **1. 人脸绝对一致**：同一角色在不同分镜中，脸型、骨相、眼珠颜色、发型长短完全一致。
- [ ] **2. 服装细节锁死**：服装款式、纽扣颜色、领口开合状态在相邻镜头中未发生突变。
- [ ] **3. 空间地理连续**：角色的左右站位、背后背景建筑与门窗光源位置逻辑自洽。
- [ ] **4. 道具状态流转合规**：道具的物理移动符合因果律（如：老紫砂在包袱内 $\rightarrow$ 露出一角 $\rightarrow$ 单手托起 $\rightarrow$ 稳稳捧直，绝不凭空瞬移）。
- [ ] **5. 杜绝幽灵多余人物**：画面中没有未在剧本中声明的模糊路人或突兀多余脸孔。
- [ ] **6. 画面零杂乱字幕**：提示词中显式禁止任何未经授权的英文字幕、乱码水印、片名字样。
- [ ] **7. 年龄与体态锁定**：角色体型比例与年龄感稳定，不忽大忽小、忽老忽少。
- [ ] **8. 物理真实动作**：手部持握、迈步动作符合人体解剖学，无反关节或手指黏连。
- [ ] **9. 运镜拒绝空洞**：严禁出现 `cinematic camera` 等泛词，必须有具体焦段与物理位移。
- [ ] **10. 灯光拒绝抽象**：严禁出现 `beautiful light`，必须有明确的主光与辅助光来源。
- [ ] **11. 导演风格不杂糅**：单场戏严格遵循单一导演/胶片视听基调，不胡乱拼贴冲突流派。
- [ ] **12. 色彩饱和度受控**：色调必须由具体的 2~3 种环境主色统领，不出现调色盘失控。
- [ ] **13. 尾态画面稳定定格**：每个片段结尾必须有明确的稳定终态帧（Afterimage），无悬空半截动作。
- [ ] **14. 逻辑零前后矛盾**：如前一秒是暴雨，后一秒地面绝不能干透无水渍。

---

## 二、 关键道具状态迁移追踪链 (Object Progression Chain)

对于短剧核心道具（如三亿紫砂小品壶、钛合金卫星电话），必须建立一条线性的物理迁移链，防止道具凭空消失或状态打架：

```text
[初始状态] 粗棉布包袱紧紧包裹，斜挎在林青柠身侧
    ↓ (H3-001 碰撞触发)
[解体状态] 崔秀雅跟班撞击，布料松脱滑开约一半，露出深红紫泥壶钮
    ↓ (H3-002 现世状态)
[持握状态] 林青柠单手稳稳托住壶底，壶身温润无损，段砂颗粒在晨光下显露
    ↓ (H3-003 收回状态)
[带走状态] 青柠将小壶重新捧于双手中，贴近胸前，转身迈步带出画外
```

---

## 三、 五大高频翻车模式的现成修复模板 (Failure Modes & Fixes)

当遇到模型生成翻车时，直接将以下针对性防崩修复句式追加进提示词：

### 翻车 1：镜头融化粘连成一条长镜头（One continuous take instead of montage）
- **修复咒语**：
  ```text
  This must be a multi-shot sequence with visible hard cuts. Do not generate a single continuous take. Each beat uses a completely different angle and framing with crisp cut transitions.
  ```

### 翻车 2：角色在相邻镜头中换脸或换衣（Character face/outfit changes）
- **修复咒语**：
  ```text
  Preserve the exact same character in every shot: identical bone structure, same eyes, identical navy tailored blazer with brass buttons, identical hair length. Do not alter identity or costume.
  ```

### 翻车 3：核心道具中途凭空消失（Object disappears mid-scene）
- **修复咒语**：
  ```text
  Track the object continuously. The dark purple-clay teapot remains physically present and firmly held in her right hand across all frames; it must never vanish or morph.
  ```

### 翻车 4：戏剧张力不足、表演像木偶（Weak drama, flat scene）
- **修复咒语**：
  ```text
  Play the scene with intense, quiet dramatic gravity. Every actor exhibits subtle physical tension: clenched jaw, restrained breathing, and piercing direct eye contact. No relaxed or neutral drifting.
  ```
- **表演层细目**：突然变脸 / 表情冻结 / 表演夸张 / 只哭不笑 / 只笑不泪 / 情绪直线上升 / 情绪一来就停任务等失败模式与改法，见 [EMOTION_PROCESS_DIRECTION.md](EMOTION_PROCESS_DIRECTION.md) §10。

### 翻车 5：多镜头快切时画面混乱狂晃（Messy random cuts）
- **修复咒语**：
  ```text
  Maintain strict 180-degree axis continuity. The camera remains strictly on the west side of the characters. Every cut lands cleanly on a decisive glance or physical impact.
  ```

---

## 四、 打斗 / 技能特效失败诊断（单变量排错）

用户拿翻车结果回来 → **每轮只改一类变量**，改完复测再定下一步。物理层细节见 `COMBAT_FX_ANCHOR_SYSTEM.md`。

| 症状 | 真因 | 修法 |
| :--- | :--- | :--- |
| 技能位置太低 / 贴地 | 没写高度与视角 | 补「悬于**百米高空画面左上方**」+「**仰视视角**」 |
| 出来的是实体（火龙 / 龙）而非流体 | 主体没带材质词 | 「巨型火龙」→「巨型龙形**火焰流体**」 |
| 技能从人物身前乱冒 | 锚点没写或位置写错 | 明确「锚点锁定**掌心**」「自**身后**浮现」 |
| 没有打击感 | 缺物理反馈 | 补「坍塌 + 碎石飞射 + **不规则形状**」 |
| 特效很假 / 像贴图 | 缺光效与环境氛围词 | 补体积光 / 环境漫射 / 自发光（可加 `volumetric fog`） |
| 双人镜头"低智"、两人没距离感 | 没写景别构图 | 补「两人位于画面两端相距百米」+「对角构图：一人在左下地面，一人在右上角」 |
| 人物与背景割裂、细节差 | 缺多视图 | 补四视图转身参考图（见 `PROMPT_TEMPLATE_ASSET_EXPANSION.md`） |
| 蓄力幅度不够 | 动作没写起手 | 补「抬手再向前伸出」 |
| 语病导致的偏差 | 用词不当 | 「不规则雷球」→「**不规则的形状**」 |
| H3 出现自由漂浮的光束 / 常驻光环 | 能量被当成装饰 | 能量只从**接触点爆发**；写实街战纯物理（灰尘 / 碎屑 / 闷哼） |
| 偶发异常（模型抽风） | **不是提示词问题** | **直接再生成一遍**，别改提示词 |

> **判据：失败是提示词问题，不是模型问题**——先查这张表，再考虑重生成。

---

## 五、 打斗特效的收尾与污染词硬约束

**结尾三不写**：不写「缓缓收势」「光芒渐熄」「镜头缓缓拉远」；不写定格摆姿势；不写"渐隐"式收尾。→ 改成：**最后一击 + 结果爆发 + 空间位置**。

**负向约束（默认都加）**：不要字幕 / 不要 BGM / 不要水印 / 不要 Logo / 不要可读文字。

**跨题材污染词（按题材排除）**：
- 武侠 / 仙侠禁：机甲、警笛、赛博、霓虹广告
- 现代街战禁：灵气、法力、御剑、阵纹
- 机甲禁：刀气、掌法、内力

> 提示词层预防见本表；物理层细节见 `COMBAT_FX_ANCHOR_SYSTEM.md`，词库见 `COMBAT_FX_VOCABULARY.md`。
