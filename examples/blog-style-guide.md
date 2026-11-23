# 陶土暖阳 · 暖纸书卷博客 UI 风格指南

> 暖纸底色上的陶土橙书房：出版物式的书架首页、克制到只在交互处出现的橙色、中下方悬浮 Dock。
> 本文档是该博客视觉风格的唯一权威来源，任何 AI 或开发者仅凭此文档即可还原整套风格。
> 生成工具：blog-style-designer（确认日期 2026-11-23）

---

## 1. 视觉规范

### 1.1 配色

| 用途 | CSS 变量 | 色值 | 说明 |
|---|---|---|---|
| 底色 | `--blog-bg` | `#faf3ec` | 暖调纸底，比基准站更暖 |
| 主文字 | `--blog-text` | `#3a2d24` | 深墨棕，非纯黑 |
| 强调色 | `--blog-accent` | `#c96f4a` | 陶土橙，**只出现在交互处**（见 1.5 用色策略） |
| 强调色亮 | `--blog-accent-bright` | `#d98c5f` | 与强调色组成渐变（135deg） |
| 次级文字 | `--blog-text-dim` | `#9c8b7a` | 日期、副标题、元信息 |
| 强调次级文字 | `--blog-text-warm` | `#9c6b4f` | 选中态文字、链接文字（金棕） |
| 正文辅助 | `--blog-text-body` | `#7d6a56` | 摘要、引文（衬线时使用） |
| 卡片面 | `--blog-surface` | `#fffdfa` | 白卡、Dock、胶囊底 |
| 分割线 | `--blog-line` | `#eaddd0` | 页面分割线、边框 |
| NEW 标底 | `--blog-badge` | `#a34328` | 铁锈红，仅用于 NEW 徽章 |
| 网格纹理 | `--blog-grid` | `#eaddd033` | 背景网格线（见 3.2） |

**深色模式**：暂无深色模式。

**书封专用色板**（文章封面卡的底色，按序循环使用）：
`#f5e9d8`（米纸）/ `#b8623c`（砖橙）/ `#5b6d7a`（灰蓝）/ `#d9a441`（芥黄）/ `#8a5a44`（咖啡棕）/ `#f5e9d8+描边`（浅纸）/ `#7d8a6e`（苔绿）/ `#a34328`（铁锈红）。浅色书封配深字 `#3a2d24`，深色书封配 `#f8ede0` 系浅字；封面内衬细边框 `rgba(255,255,255,.2)`（浅底书封用 `#c96f4a55`）。

### 1.2 字体层级

| 层级 | 字体栈 | 字号/字重 | 用途 |
|---|---|---|---|
| H0（slogan） | `Georgia, 'Noto Serif SC', serif` | 40px / 800 | 首页 hero 大标语 |
| H1 | `Georgia, 'Noto Serif SC', serif` | 19-21px / 800 | 特写条标题、区块大标题 |
| H2 | `'Plus Jakarta Sans', 'PingFang SC', sans-serif` | 18-19px / 800 | 区块标题（「最近的文章」等） |
| 卡片标题 | `'Plus Jakarta Sans', 'PingFang SC', sans-serif` | 12.5-13px / 700 | 书封下方文章标题 |
| 正文/摘要 | `'Noto Serif SC', 'Songti SC', SimSun, serif` | 12.5-13px / 400，行高 1.9 | 摘要、引文、关于卡正文 |
| 辅助/元信息 | `'Plus Jakarta Sans', 'PingFang SC', sans-serif` | 10.5-11px / 400-600 | 日期、篇号、阅读时长、标签 |

规则：标题与 UI 用无衬线，**摘要与引文切换为衬线**（阅读质感）；书封上的封面题字用 `Georgia, 'Noto Serif SC', serif` 800 字重。

### 1.3 间距 / 圆角 / 阴影

- 间距体系：4 / 8 / 12 / 18 / 22 / 30 / 34 / 44（px）；页面左右主留白 56px；区块间 30-44px
- 圆角规则：书封 9px（内衬 5px）、白卡与特写条 12px、胶囊 999px；整体克制，无 20px 以上大圆角
- 阴影规则：
  - 书封：`0 3px 14px rgba(30,18,8,.10)`
  - 白卡/特写条：`0 3px 14px rgba(30,18,8,.07)`
  - Dock：`0 10px 30px rgba(58,45,36,.16)`（页面唯一重阴影，用于悬浮感）

### 1.4 气质关键词

出版物质感、陶土暖阳、克制点缀、书架隐喻、耐读

### 1.5 用色策略（核心约束，不得违反）

**陶土橙 `#c96f4a` 只允许出现在以下交互/标记处**：
1. 选中导航项的文字色与底部短下划线
2. 篇号文字（第 N 篇）
3. NEW 徽章旁的强调（NEW 徽章本体用 `#a34328`）
4. CTA「订阅慢递」的渐变底（`135deg, #c96f4a → #d98c5f`）
5. Dock 明暗切换钮的描边
6. 「查看全部 →」等次级链接文字（用金棕 `#9c6b4f`）

禁止：橙色大面积铺底、橙色正文、橙色标题重音字。

---

## 2. 组件规范

### 2.1 导航栏 — 中下方悬浮 Dock（文字 + CTA 混排）

- **位置与结构**：固定于页面底部居中（`bottom: 16px`），悬浮胶囊；页面无顶部导航栏，顶部只有 logo 行
- **内部结构**（从左到右）：`◉ 首页`（当前项：金棕文字 + 橙色圆点标记）→ 文章 → 随笔 → 🌙 圆钮（22-24px，`#f2ddc4` 底 + 1.5px 橙描边）→ `✦ 订阅慢递` CTA 胶囊（橙渐变底反白 700 字重）
- **样式要点**：底 `#fffdfa`、边框 `1px #eaddd0`、圆角 999px、内边距 `9px 10px 9px 22px`（CTA 侧收窄）、字号 12px、项间距 14px、重阴影见 1.3
- **悬浮态**：非当前项 hover 变金棕 `#9c6b4f`；当前项以圆点 + 文字色标记，不用背景色

### 2.2 首页版式 — Hero 特写版

首屏自上而下：

1. **logo 行**：圆形 logo（38px，`#f2ddc4` 底 + 2px 橙描边 + emoji）+ 博客名 16px/800 + `slow-flight ✦ blog` 小胶囊（surface 底 + line 边框，10px 字）
2. **Hero 区**（上边距 38px）：左侧衬线大标语 40px/800（「把日子写慢一点。」）+ 13px 衬线副标语；右侧两枚数据胶囊（surface 底 + line 边框，如「已出版 8 篇」「第 09 期排版中」）
3. **最新一期特写条**：白卡（surface + line 边框 + 12px 圆角），横向 flex：左侧 200px 书封竖图，右侧内容区（NEW 徽章 + 篇号行 → 19px 标题 → 衬线摘要 → 元信息行），内边距 20px 26px
4. **书架上的旧刊**：区块标题 19px/800 + 右侧「查看全部 →」（金棕）；4 列书封网格，间距 18px
5. **页脚**：居中 10px 字距 2px：「✦ 慢速飞行 · 把日子写慢一点 · © 2026」

### 2.3 文章卡片（书封卡）

- **结构**：书封图（3:4 竖版）→ 篇号行（10px：NEW 徽章 + 「第 N 篇」）→ 标题（12.5-13px/700）→ 元信息（10.5px 灰：日期 · 阅读时长）
- **书封图**：底色从 1.1 书封色板取；内衬边框（inset 9px，5px 圆角，1px 半透明线）；浅底封面可加网点纹理（repeating-radial-gradient，见 3.2）；封面题字为两行居中衬线 800 字重（如「重新<br>出发」，与文章标题呼应但独立成封面题名）
- **关键尺寸**：间距 18px；标题行高 1.5；卡片间不用外框、不悬浮（静态）

### 2.4 按钮 / 链接

- **主 CTA（订阅慢递）**：`linear-gradient(135deg, #c96f4a, #d98c5f)` 底反白，999px 胶囊，12px/700，padding `7px 16px`
- **次级链接（查看全部 →）**：金棕 `#9c6b4f` / 600 字重，无下划线
- **数据胶囊**：surface 底 + line 边框 + 999px + 金棕文字，11-12px
- **选中导航态**：金棕 700 字重 + 橙色圆点；**禁用**背景高亮

### 2.5 标签 / 元信息

- 元信息（日期、篇号、时长）：10.5px，`--blog-text-dim`，无字距要求
- 篇号强调：「第 N 篇」用橙 `#c96f4a` / 600
- NEW 徽章：`#a34328` 底反白，3px 圆角，padding `1px 7px`，9-10px/700，**仅最新一篇使用**

### 2.6 页脚

居中单行：`✦ 慢速飞行 · 把日子写慢一点 · © 2026`，10px、字距 2px、`--blog-text-dim`；无链接堆栈、无边框线。

---

## 3. CSS Tokens

### 3.1 变量定义

```css
:root {
  /* 配色 */
  --blog-bg: #faf3ec;
  --blog-text: #3a2d24;
  --blog-accent: #c96f4a;
  --blog-accent-bright: #d98c5f;
  --blog-text-dim: #9c8b7a;
  --blog-text-warm: #9c6b4f;
  --blog-text-body: #7d6a56;
  --blog-surface: #fffdfa;
  --blog-line: #eaddd0;
  --blog-badge: #a34328;

  /* 书封色板（按序循环） */
  --blog-cover-1: #f5e9d8;
  --blog-cover-2: #b8623c;
  --blog-cover-3: #5b6d7a;
  --blog-cover-4: #d9a441;
  --blog-cover-5: #8a5a44;
  --blog-cover-6: #7d8a6e;
  --blog-cover-7: #a34328;

  /* 字体 */
  --blog-font-ui: 'Plus Jakarta Sans', 'PingFang SC', 'Microsoft YaHei', sans-serif;
  --blog-font-serif: Georgia, 'Noto Serif SC', 'Songti SC', SimSun, serif;
  --blog-font-body: 'Noto Serif SC', 'Songti SC', SimSun, serif;

  /* 阴影 */
  --blog-shadow-cover: 0 3px 14px rgba(30,18,8,.10);
  --blog-shadow-card: 0 3px 14px rgba(30,18,8,.07);
  --blog-shadow-dock: 0 10px 30px rgba(58,45,36,.16);
}
```

### 3.2 核心组件样式片段

```css
/* 背景：暖纸底 + 网格纸纹理（铺满 body） */
body {
  background: var(--blog-bg);
  background-image:
    linear-gradient(rgba(234,221,208,.2) 1px, transparent 1px),
    linear-gradient(90deg, rgba(234,221,208,.2) 1px, transparent 1px);
  background-size: 22px 22px;
  color: var(--blog-text);
  font-family: var(--blog-font-ui);
}
```

```css
/* 文章书封卡（3:4 竖版 + 内衬边框，浅底可加网点纹理） */
.cover {
  aspect-ratio: 3 / 4;
  border-radius: 9px;
  box-shadow: var(--blog-shadow-cover);
  display: flex; align-items: center; justify-content: center;
  position: relative; overflow: hidden;
}
.cover::before {
  content: ''; position: absolute; inset: 9px;
  border-radius: 5px; border: 1px solid rgba(255,255,255,.2);
}
.cover--paper::before {
  border-color: rgba(201,111,74,.34);
  background-image: repeating-radial-gradient(circle at 50% 45%,
    rgba(201,111,74,.12) 0 2px, transparent 2px 9px);
}
.cover-title {
  position: relative; text-align: center; line-height: 1.5;
  font-family: var(--blog-font-serif); font-weight: 800; font-size: 15px;
}
```

```css
/* 中下方悬浮 Dock（文字 + 明暗钮 + CTA） */
.dock {
  position: fixed; left: 50%; bottom: 16px; transform: translateX(-50%);
  display: flex; align-items: center; gap: 14px;
  background: var(--blog-surface);
  border: 1px solid var(--blog-line);
  border-radius: 999px;
  padding: 9px 10px 9px 22px;
  font-size: 12px;
  box-shadow: var(--blog-shadow-dock);
}
.dock__item { color: #6b5c4e; }
.dock__item--active { color: var(--blog-text-warm); font-weight: 700; }
.dock__item--active::before {
  content: '◉'; margin-right: 4px; color: var(--blog-text-warm);
}
.dock__cta {
  background: linear-gradient(135deg, var(--blog-accent), var(--blog-accent-bright));
  color: #fff; font-weight: 700; border-radius: 999px; padding: 7px 16px;
}
```

```css
/* 最新一期特写条（白卡横向布局） */
.feature {
  display: flex;
  background: var(--blog-surface);
  border: 1px solid var(--blog-line);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: var(--blog-shadow-card);
}
.feature__cover { width: 200px; flex-shrink: 0; }
.feature__body { flex: 1; padding: 20px 26px; }
.feature__title { font-size: 19px; font-weight: 800; margin-top: 8px; }
.feature__excerpt {
  font-family: var(--blog-font-body); font-size: 12.5px;
  line-height: 1.9; color: var(--blog-text-body); margin-top: 8px;
}
```

```css
/* NEW 徽章与元信息行 */
.badge-new {
  background: var(--blog-badge); color: #fff;
  border-radius: 3px; padding: 1px 7px;
  font-size: 10px; font-weight: 700;
}
.meta { font-size: 10.5px; color: var(--blog-text-dim); }
.meta__no { color: var(--blog-accent); font-weight: 600; }
```

---

## 附：本次确认路径（存档）

暖纸书卷风（基准 book.oiloil.org）→ 实现 A 浅色基准版 → 配色 2「陶土暖阳」→ 应用 A「克制点缀」→ 导航 4「中下方悬浮 Dock」→ Dock 实现 B「文字 + 订阅 CTA 混排」→ 高保真版 2「Hero 特写版」。
参考基准：book.oiloil.org（书架骨架与暖纸语言）。示例博客名「慢速飞行」为占位内容，实际使用时替换。
