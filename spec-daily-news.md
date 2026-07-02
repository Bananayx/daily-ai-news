# 每日AI晚报 — 每日新闻详情页设计规范

## 1. 页面概述

### 页面用途与角色
每日新闻详情页是"每日AI晚报"的核心内容页，展示特定日期的全部AI新闻条目。承担以下功能：
- **日期标题展示**：以大号等宽字体突出显示新闻日期，建立时间锚点。
- **新闻详情列表**：以卡片列表形式逐条呈现完整新闻，包含分类标签、发布时间、标题、摘要及信息来源链接。
- **今日趋势点评**：以纯文本段落形式提供编辑视角的行业趋势分析。

### 目标受众
- 需要了解当日AI新闻全貌的深度读者。
- 希望按分类（行业、学术、政策、产品、融资）快速浏览信息的用户。
- 重视信息来源可追溯性的专业用户。

---

## 2. 设计系统令牌

### 颜色令牌

| CSS 变量 | 色值 | 用途上下文 |
|---|---|---|
| `--background` | `#c5c9c9` | 页面主体背景 (`<main>`) |
| `--foreground` | `#111111` | 标题文字颜色、日期大标题 |
| `--card` | `#d8dada` | 新闻卡片背景、页脚背景 |
| `--card-foreground` | `#111111` | 卡片内文字颜色（正文描述） |
| `--primary` | `#111111` | 导航栏背景 |
| `--primary-foreground` | `#ffffff` | 导航栏内文字与Logo颜色 |
| `--muted-foreground` | `#888888` | 星期副标题、时间戳、信息来源链接、趋势点评文字、页脚文字 |
| `--accent` | `#0040ff` | Logo下划线装饰、行业标签描边颜色、信息来源链接hover颜色 |
| `--accent-foreground` | `#ffffff` | 行业标签文字颜色（仅用于首页填充样式） |
| `--destructive` | `#d73333` | 政策标签描边颜色 |
| `--destructive-foreground` | `#ffffff` | 政策标签文字颜色（仅用于首页填充样式） |
| `--border` | `#ffffff` | 卡片边框、页脚顶边框 |
| `--ring` | `#000000` | 焦点环颜色 |
| `--chart-2` | `#386aff` | 融资标签描边颜色 |
| `--chart-3` | `#6b90ff` | 学术研究标签描边颜色 |

**自定义颜色（非令牌）：**

| 色值 | 用途上下文 |
|---|---|
| `#e08a00` | 产品发布标签描边颜色 |

### 字体令牌

| 令牌 | 值 | 用途 |
|---|---|---|
| `--font-sans` | `Geist, ui-sans-serif, sans-serif, system-ui` | 趋势点评正文、页脚文字 |
| `--font-mono` | `Geist Mono, ui-monospace, monospace` | Logo、导航链接、日期标题、星期副标题、区块标题、新闻卡片标题、分类标签、时间戳、信息来源链接、回到首页按钮文字 |

**字号使用：**

| 元素 | 字号 | 字重 | 字体 |
|---|---|---|---|
| Logo | `20px` | `700` | `--font-mono` |
| 导航按钮 | `14px` (text-sm) | `400` (继承) | `--font-mono` |
| 日期大标题 (h1) | `clamp(32px, 5vw, 56px)` | `700` | `--font-mono` |
| 星期副标题 | `18px` | `400` (继承) | `--font-mono` |
| 区块标题 (h2) | `24px` | `700` | `--font-mono` |
| 新闻标题 (h2, 卡片内) | `20px` | `700` | `--font-mono` |
| 正文描述（卡片） | `15px` | `400` | 继承 (var(--font-sans) 通过 body) |
| 趋势点评正文 | `14px` | `400` | `--font-sans` |
| 分类标签 | `12px` | `500` | `--font-mono` |
| 时间戳 | `13px` | `400` | `--font-mono` |
| 信息来源链接 | `12px` | `400` | `--font-mono` |
| 页脚文字 | `12px` (text-xs) | `400` | `--font-sans` |

**字距与行高：**

| 元素 | 属性 | 值 |
|---|---|---|
| Logo | `letter-spacing` | `-0.02em` |
| 日期大标题 (h1) | `letter-spacing` | `-0.03em` |
| 日期大标题 (h1) | `line-height` | `1.1` |
| 星期副标题 | `letter-spacing` | `-0.01em` |
| 区块标题 (h2) | `letter-spacing` | `-0.02em` |
| 新闻卡片标题 (h2) | `letter-spacing` | `-0.01em` |
| 新闻卡片标题 (h2) | `line-height` | `1.3` |
| 正文描述（卡片） | `line-height` | `1.6` |
| 趋势点评正文 | `line-height` | `1.8` |

### 间距令牌

| 元素 | 间距模式 | 值 |
|---|---|---|
| `<main>` 顶部 | `padding-top` | `56px` (pt-14) / `64px` (md:pt-16) |
| 日期区块上内边距 | `padding-top` | `48px` (pt-12) / `64px` (md:pt-16) |
| 日期区块下内边距 | `padding-bottom` | `32px` (pb-8) / `40px` (md:pb-10) |
| 日期装饰线顶部间距 | `margin-top` | `16px` |
| 新闻列表下内边距 | `padding-bottom` | `64px` (pb-16) / `96px` (md:pb-24) |
| 新闻卡片间距 | `gap` | `20px` (gap-5) |
| 新闻卡片内边距 | `padding` | `24px` |
| 卡片内部间距 | `gap` | `12px` (gap-3) |
| 趋势点评区块间距 | `gap` | `16px` (gap-4) |
| 趋势点评区块下内边距 | `padding-bottom` | `64px` (pb-16) / `96px` (md:pb-24) |
| 页脚内边距 | `padding` | `16px` (py-4) |
| 区块标题下间距 | `margin-bottom` | `24px` (mb-6) |

### 阴影令牌

| 令牌 | 值 | 使用位置 |
|---|---|---|
| `--shadow` | `2px 2px 0px rgba(0,0,0,1)` | 导航栏 `box-shadow` |
| `--shadow` | `2px 2px 0px var(--foreground)` | 新闻卡片（默认状态） |
| `--shadow` | `3px 3px 0px var(--foreground)` | 新闻卡片（hover 状态） |
| `--shadow` | `2px 2px 0px var(--foreground)` | 回到顶部按钮 |

> 注：设计系统定义了 `shadow-xs` 至 `shadow-xl` 六个级别，所有级别实际值相同（`2px 2px 0px`），仅 `shadow-xs` 透明度为 `0.5`。新闻卡片 hover 状态使用自定义的 `3px 3px` 阴影。

### 边框令牌

| 令牌 | 值 | 使用位置 |
|---|---|---|
| `--border` | `#ffffff` | 新闻卡片边框 `1px solid`、页脚顶边框 |
| `--accent` | `#0040ff` | Logo底部装饰线 `2px solid` |

**分类标签描边边框：**

| 标签类别 | 描边颜色 | 值 |
|---|---|---|
| 行业动态 | `var(--accent)` | `#0040ff` |
| 学术研究 | `var(--chart-3)` | `#6b90ff` |
| 政策法规 | `var(--destructive)` | `#d73333` |
| 产品发布 | 自定义硬编码 | `#e08a00` |
| 融资动态 | `var(--chart-2)` | `#386aff` |

### 圆角令牌

| 令牌 | 值 | 说明 |
|---|---|---|
| `--radius` | `0px` | 全站无圆角，采用锐利/Brutalist风格 |

---

## 3. 页面结构

### 3.1 导航栏 (Navbar)

- **HTML 结构**：`<nav>` > `<div>` (max-w-3xl 容器) > Logo `<a>` + 导航按钮 `<div>`
- **视觉描述**：黑色全宽条带，固定于页面顶部，高度 `56px`（移动端）/ `64px`（桌面端）。带有 `2px 2px 0px` 黑色硬阴影，形成悬浮立体效果。右侧为"回到首页"描边按钮。
- **CSS 属性**：
  - `position: fixed; top: 0; left: 0; width: 100%; z-index: 50; height: 56px`
  - `background: var(--primary)` (#111111)
  - `color: var(--primary-foreground)` (#ffffff)
  - `box-shadow: 2px 2px 0px var(--foreground)` (#111111)
  - 容器：`max-width: 768px` (max-w-3xl), `margin: 0 auto`, `padding: 0 16px` (移动端) / `0` (桌面端)

### 3.2 日期标题区块 (Section 1)

- **HTML 结构**：`<section>` > `<h1>` (日期) + `<p>` (星期) + `<div>` (装饰线)
- **视觉描述**：页面首屏大号区域，日期以响应式大号等宽粗体呈现（移动端32px至桌面端56px），下方为灰色星期副标题，再下方一条 `64px` 宽、`2px` 高的蓝色（`--accent`）装饰线。
- **CSS 属性**：
  - 区块：`padding: 48px 16px 32px`（移动）/ `64px 0 40px`（桌面），`max-width: 768px; margin: 0 auto`
  - h1 日期：`font-family: var(--font-mono); font-size: clamp(32px, 5vw, 56px); font-weight: 700; color: var(--foreground); line-height: 1.1; letter-spacing: -0.03em; text-wrap: balance; word-break: keep-all`
  - p 星期：`font-family: var(--font-mono); font-size: 18px; color: var(--muted-foreground); margin-top: 8px; letter-spacing: -0.01em`
  - 装饰线：`width: 64px; height: 2px; background: var(--accent); margin-top: 16px`

### 3.3 新闻卡片列表区块 (Section 2)

- **HTML 结构**：`<section>` > `<article>` (news-card) x8
- **视觉描述**：8张新闻卡片纵向排列，每张卡片包含分类标签+时间戳行、标题、正文摘要、信息来源链接。卡片之间间距 `20px`。卡片有硬阴影和白色边框，hover 时轻微位移并增大阴影。
- **CSS 属性**：
  - 区块：`padding-bottom: 64px`（移动）/ `96px`（桌面），`max-width: 768px; margin: 0 auto; display: flex; flex-direction: column; gap: 20px`

### 3.4 今日趋势点评区块 (Section 3)

- **HTML 结构**：`<section>` > `<h2>` + `<div>` (flex-col gap-4) > `<p>` x3
- **视觉描述**：标题"今日趋势点评"下方的三个分析段落，灰色文字、较宽松行高，无卡片包裹，直接展示在页面背景上。
- **CSS 属性**：
  - 区块：`padding-bottom: 64px`（移动）/ `96px`（桌面），`max-width: 768px; margin: 0 auto`
  - 标题：`font-family: var(--font-mono); font-size: 24px; font-weight: 700; color: var(--foreground); letter-spacing: -0.02em; margin-bottom: 24px`
  - 段落容器：`display: flex; flex-direction: column; gap: 16px`
  - 段落：`color: var(--muted-foreground); font-family: var(--font-sans); font-size: 14px; line-height: 1.8`

### 3.5 页脚 (Footer)

- **HTML 结构**：`<footer>` > `<div>` (max-w-3xl 容器) > 版权 `<span>` + 免责声明 `<span>`
- **视觉描述**：灰色卡片背景，顶部白色边框，左右分布版权与免责文字。
- **CSS 属性**：
  - `background: var(--card); border-top: 1px solid var(--border); padding: 16px`
  - 容器：`display: flex; align-items: center; justify-content: space-between; width: 100%`
  - 文字：`font-family: var(--font-sans); font-size: 12px; color: var(--muted-foreground)`

### 3.6 回到顶部按钮

- **HTML 结构**：`<button>` > 内嵌 `<svg>` 箭头图标
- **视觉描述**：固定在右下角的黑色方形按钮，内含向上箭头SVG图标。
- **CSS 属性**：
  - `position: fixed; bottom: 24px; right: 24px; width: 40px; height: 40px`
  - `background: var(--primary); color: var(--primary-foreground); border: none`
  - `box-shadow: 2px 2px 0px var(--foreground)`
  - `font-size: 18px`

---

## 4. 导航栏规范

### 固定定位
- `position: fixed; top: 0; left: 0; width: 100%; z-index: 50`
- 高度：`56px`（移动端, h-14）/ `64px`（桌面端, md:h-16）

### 容器约束
- `max-width: 768px` (max-w-3xl)
- `margin: 0 auto`
- `display: flex; align-items: center; justify-content: space-between; height: 100%`
- 移动端内边距：`padding: 0 16px` (px-4)
- 桌面端内边距：`padding: 0` (md:px-0)

### Logo 样式
- **字体**：`var(--font-mono)` (Geist Mono)
- **字号**：`20px`
- **字重**：`700`
- **颜色**：`var(--primary-foreground)` (#ffffff)
- **字距**：`letter-spacing: -0.02em`
- **装饰**：底部 `2px solid var(--accent)` (#0040ff) 下划线，`padding-bottom: 2px`
- **文本**：`每日AI晚报`
- **链接**：`text-decoration: none; display: flex; align-items: center; gap: 8px`

### 导航按钮样式（详情页特有）
- **按钮文字**：`<- 回到首页`
- **字体**：`var(--font-mono)`
- **字号**：`14px` (text-sm)
- **颜色**：`var(--primary-foreground)` (#ffffff)
- **边框**：`1px solid var(--primary-foreground)` (#ffffff)
- **内边距**：`6px 14px`
- **装饰**：`text-decoration: none`
- **过渡**：`transition-colors duration-150`
- **可见性**：移动端隐藏 (`hidden md:inline-flex`)，桌面端显示
- **交互**：链接至 `index.html`

### 阴影/边框处理
- `box-shadow: 2px 2px 0px var(--foreground)` -- 硬阴影，Brutalist 风格
- 无额外边框

---

## 5. 内容组件规范

### 5.1 新闻卡片 (.news-card)

- **组件名称**：新闻详情卡片
- **视觉结构**：灰色背景矩形卡片，内部从上到下依次为：分类标签与时间戳行（flex 布局，两端对齐）、标题、摘要正文、信息来源链接。
- **CSS 属性**：
  - `background: var(--card)` (#d8dada)
  - `box-shadow: 2px 2px 0px var(--foreground)` (#111111)
  - `border: 1px solid var(--border)` (#ffffff)
  - `border-radius: 0px`
  - `padding: 24px`
  - `transition: transform 120ms cubic-bezier(.2,.8,.2,1)`
- **Hover 状态**：
  - `transform: translate(-1px, -1px)`
  - `box-shadow: 3px 3px 0px var(--foreground)` (#111111)
  - 效果：卡片向左上角微移1px，阴影扩大1px，模拟"浮起"效果
- **内容排版层级**：
  1. 标签行（flex 布局）：分类标签 `<span class="tag">` + 时间戳 `<span class="time-stamp">`
  2. 标题 `<h2>`：`font-family: var(--font-mono); font-size: 20px; font-weight: 700; color: var(--foreground); line-height: 1.3; letter-spacing: -0.01em; word-break: keep-all; text-wrap: balance`
  3. 摘要 `<p>`：`font-size: 15px; line-height: 1.6; color: var(--foreground); max-width: 72ch`
  4. 来源链接 `<a class="source-link">`

### 5.2 分类标签 (.tag)

- **组件名称**：新闻分类标签
- **基础样式 (`.tag`)**：
  - `display: inline-flex; align-items: center; gap: 4px`
  - `font-family: var(--font-mono); font-size: 12px; font-weight: 500`
  - `padding: 2px 8px; border: 2px solid transparent; line-height: 1.5; letter-spacing: 0`
  - 背景透明 (`background: transparent`)
- **变体样式**：详见第6节"分类标签配色体系"

### 5.3 时间戳 (.time-stamp)

- **组件名称**：发布时间戳
- **CSS 属性**：
  - `font-family: var(--font-mono); font-size: 13px; color: var(--muted-foreground)`
  - `font-variant-numeric: tabular-nums` — 等宽数字对齐

### 5.4 信息来源链接 (.source-link)

- **组件名称**：新闻来源链接
- **CSS 属性**：
  - `display: inline-flex; align-items: center; gap: 4px`
  - `font-family: var(--font-mono); font-size: 12px; color: var(--muted-foreground)`
  - `text-decoration: none`
  - `transition: color 150ms cubic-bezier(.2,.8,.2,1)`
- **Hover 状态**：
  - `color: var(--accent)` (#0040ff)
- **格式**：`信息来源: 来源名 ->`

### 5.5 回到首页按钮（导航内）

- **组件名称**：导航返回按钮
- **视觉描述**：白色描边矩形按钮，内含左箭头字符和"回到首页"文字
- **CSS 属性**：
  - `display: inline-flex; align-items: center`
  - `font-family: var(--font-mono); font-size: 14px`
  - `color: var(--primary-foreground)` (#ffffff)
  - `border: 1px solid var(--primary-foreground)` (#ffffff)
  - `padding: 6px 14px`
  - `text-decoration: none`

---

## 6. 分类标签配色体系

详情页使用**描边 + 透明背景 + 彩色文字**样式，与首页的填充背景样式形成区分。

| 分类名称 | 图标 (Emoji) | CSS Class | 描边颜色 | 色值 | 文字颜色 | 样式细节 |
|---|---|---|---|---|---|---|
| 行业动态 | `🏢` | `.tag-industry` | `var(--accent)` | `#0040ff` | `var(--accent)` `#0040ff` | `border-color: #0040ff; color: #0040ff; background: transparent` |
| 学术研究 | `🔬` | `.tag-research` | `var(--chart-3)` | `#6b90ff` | `var(--chart-3)` `#6b90ff` | `border-color: #6b90ff; color: #6b90ff; background: transparent` |
| 政策法规 | `⚖️` | `.tag-policy` | `var(--destructive)` | `#d73333` | `var(--destructive)` `#d73333` | `border-color: #d73333; color: #d73333; background: transparent` |
| 产品发布 | `🚀` | `.tag-product` | 自定义硬编码 | `#e08a00` | 硬编码 `#e08a00` | `border-color: #e08a00; color: #e08a00; background: transparent` |
| 融资动态 | `💰` | `.tag-funding` | `var(--chart-2)` | `#386aff` | `var(--chart-2)` `#386aff` | `border-color: #386aff; color: #386aff; background: transparent` |

**基础标签样式 (`.tag`)：**
```css
.tag {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  font-family: var(--font-mono);
  font-size: 12px;
  font-weight: 500;
  padding: 2px 8px;
  border: 2px solid transparent;
  line-height: 1.5;
  letter-spacing: 0;
}
```

> 注：Emoji 图标包裹在标签内的 `<span>` 元素中，与分类文字之间由 `gap: 4px` 分隔。

---

## 7. 交互行为

### 回到顶部按钮
- **显示阈值**：页面滚动超过 `300px`（`window.scrollY > 300`）
- **动画**：CSS `transition: opacity 200ms`，通过 `opacity: 0/1` 和 `pointer-events: none/auto` 切换可见性
- **点击行为**：`window.scrollTo({top: 0, behavior: 'smooth'})` 平滑滚动至顶部
- **监听方式**：`window.addEventListener('scroll', toggle, {passive: true})` -- 被动事件监听，不影响滚动性能

### 卡片悬停效果 (.news-card:hover)
- **位移**：`transform: translate(-1px, -1px)` -- 向左上角平移1px
- **阴影变化**：`box-shadow: 2px 2px 0px` 变为 `3px 3px 0px var(--foreground)` -- 阴影增大1px
- **过渡动画**：`transition: transform 120ms cubic-bezier(.2,.8,.2,1)`
- **效果描述**：卡片"浮起"微动效果，保持 Brutalist 硬阴影风格的一致性

### 链接悬停效果
- **信息来源链接 (.source-link:hover)**：颜色从 `var(--muted-foreground)` (#888888) 过渡到 `var(--accent)` (#0040ff)
  - 过渡：`transition: color 150ms cubic-bezier(.2,.8,.2,1)`
- **导航链接**：`transition-colors duration-150`（Tailwind class），无额外 hover 样式定义

### 平滑滚动
- 回到顶部按钮使用 `behavior: 'smooth'`
- 页面未设置全局 `scroll-behavior: smooth`

---

## 8. 页脚规范

### 布局结构
- `<footer>` > `<div>` (max-w-3xl 容器) > 两个 `<span>` 元素左右分布
- 容器：`display: flex; align-items: center; justify-content: space-between; width: 100%`

### 排版
- **字体**：`var(--font-sans)` (Geist)
- **字号**：`12px` (text-xs)
- **颜色**：`var(--muted-foreground)` (#888888)

### 背景/边框处理
- `background: var(--card)` (#d8dada)
- `border-top: 1px solid var(--border)` (#ffffff)

### 容器宽度
- `max-width: 768px` (max-w-3xl), `margin: 0 auto`
- 内边距：`padding: 0 16px`（移动端）/ `0`（桌面端）

### 内容
- 左侧：`&copy; 2025 每日AI晚报`
- 右侧：`内容由AI生成，请谨慎甄别。`

---

## 9. 响应式断点

### 移动端（默认，<768px）

| 属性 | 值 |
|---|---|
| 导航栏高度 | `56px` (h-14) |
| 主内容顶部偏移 | `padding-top: 56px` (pt-14) |
| 容器左右内边距 | `padding: 0 16px` (px-4) |
| 日期区块上内边距 | `padding-top: 48px` (pt-12) |
| 日期区块下内边距 | `padding-bottom: 32px` (pb-8) |
| 日期标题字号 | `clamp(32px, 5vw, 56px)` -- 在此断点下约为 32px~44px |
| 新闻列表下内边距 | `padding-bottom: 64px` (pb-16) |
| 趋势点评区块下内边距 | `padding-bottom: 64px` (pb-16) |
| 导航"回到首页"按钮 | 隐藏 (`hidden md:inline-flex`) |
| 新闻卡片间距 | `gap: 20px` (gap-5) |
| 新闻卡片内边距 | `padding: 24px` |

### 桌面端 (md, >=768px)

| 属性 | 值 |
|---|---|
| 导航栏高度 | `64px` (md:h-16) |
| 主内容顶部偏移 | `padding-top: 64px` (md:pt-16) |
| 容器左右内边距 | `padding: 0` (md:px-0) |
| 日期区块上内边距 | `padding-top: 64px` (md:pt-16) |
| 日期区块下内边距 | `padding-bottom: 40px` (md:pb-10) |
| 日期标题字号 | `clamp(32px, 5vw, 56px)` -- 在此断点下约为 56px |
| 新闻列表下内边距 | `padding-bottom: 96px` (md:pb-24) |
| 趋势点评区块下内边距 | `padding-bottom: 96px` (md:pb-24) |
| 导航"回到首页"按钮 | 显示 (`md:inline-flex`) |
| 新闻卡片间距 | `gap: 20px` (gap-5) -- 两端一致 |
| 新闻卡片内边距 | `padding: 24px` -- 两端一致 |

---

## 10. 可访问性

### 语义化 HTML
- `<nav>` -- 导航栏
- `<main>` -- 页面主内容
- `<section>` -- 各内容区块（日期标题、新闻列表、趋势点评）
- `<h1>` -- 日期大标题（页面唯一一级标题）
- `<h2>` -- 区块标题、新闻卡片标题
- `<article>` -- 每张新闻卡片使用 `<article class="news-card">` 包裹，语义正确
- `<footer>` -- 页脚

### ARIA 标签
- 回到顶部按钮：`aria-label="回到顶部"`

### 焦点状态
- 依赖 Tailwind CSS 默认焦点环（使用 `--ring` 变量 `#000000`）
- 页面中未显式定义自定义焦点样式

### 减弱动效支持
- **已实现** `@media (prefers-reduced-motion: reduce)` 媒体查询：
  ```css
  @media (prefers-reduced-motion: reduce) {
    .news-card { transition: none; }
    .source-link { transition: none; }
  }
  ```
- 卡片 hover 位移动画和链接颜色过渡在减弱动效模式下完全禁用
- 回到顶部按钮的 `transition: opacity 200ms` **未**在此媒体查询中处理

### 其他可访问性特性
- `<html lang="zh-CN">` -- 正确的语言声明
- `text-wrap: balance` -- 标题自动平衡换行，改善阅读体验
- `word-break: keep-all` -- 防止中文标题在字内断行
- `max-width: 72ch` -- 正文段落最大宽度限制，避免宽屏下行过长
- `font-variant-numeric: tabular-nums` -- 时间戳数字等宽排列，便于视觉对齐
