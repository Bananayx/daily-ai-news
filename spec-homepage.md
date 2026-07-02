# 每日AI晚报 — 首页设计规范

## 1. 页面概述

### 页面用途与角色
首页是"每日AI晚报"网站的主入口，承担三个核心功能：
- **今日要闻概览**：以摘要卡片形式展示当日最重要的AI新闻（3条），引导用户进入详情页。
- **历史新闻时间线**：以时间线布局呈现往期新闻，方便用户快速浏览过往内容。
- **关于介绍**：以双栏卡片介绍网站定位与作者信息，建立信任。

### 目标受众
- AI行业从业者、科技爱好者、需要快速获取AI动态的读者。
- 偏好高效信息获取、注重排版清晰度的技术向用户。

---

## 2. 设计系统令牌

### 颜色令牌

| CSS 变量 | 色值 | 用途上下文 |
|---|---|---|
| `--background` | `#c5c9c9` | 页面主体背景 (`<main>`) |
| `--foreground` | `#111111` | 标题文字颜色、时间线竖线与圆点 |
| `--card` | `#d8dada` | 卡片背景色（要闻摘要卡片、关于卡片） |
| `--card-foreground` | `#111111` | 卡片内文字颜色 |
| `--primary` | `#111111` | 导航栏背景、CTA按钮背景 |
| `--primary-foreground` | `#ffffff` | 导航栏内文字与Logo颜色 |
| `--muted-foreground` | `#888888` | 正文描述文字、日期标签、页脚文字 |
| `--accent` | `#0040ff` | Logo下划线装饰、链接文字颜色 |
| `--accent-foreground` | `#ffffff` | 分类标签（行业）文字颜色 |
| `--destructive` | `#d73333` | 分类标签（政策）背景色 |
| `--destructive-foreground` | `#ffffff` | 分类标签（政策）文字颜色 |
| `--border` | `#ffffff` | 卡片边框、分隔线颜色 |
| `--chart-3` | `#6b90ff` | 分类标签（研究）背景色 |
| `--ring` | `#000000` | 焦点环颜色 |

### 字体令牌

| 令牌 | 值 | 用途 |
|---|---|---|
| `--font-sans` | `Geist, ui-sans-serif, sans-serif, system-ui` | 正文描述文字 |
| `--font-mono` | `Geist Mono, ui-monospace, monospace` | Logo、导航链接、标题、分类标签、日期、按钮文字 |

**字号使用：**

| 元素 | 字号 | 字重 | 字体 |
|---|---|---|---|
| Logo | `20px` | `700` | `--font-mono` |
| 导航链接 | `14px` (text-sm) | `400` (继承) | `--font-mono` |
| 区块标题 (h2) | `24px` | `700` | `--font-mono` |
| 新闻标题 (h3) | `16px` (text-base) | `700` (font-bold) | `--font-mono` |
| 正文描述 | `14px` (text-sm) | `400` | `--font-sans` |
| 分类标签 | `12px` (text-xs) | `700` (font-bold) | `--font-mono` |
| 时间线日期 | `12px` (text-xs) | `700` (font-bold) | `--font-mono` |
| CTA按钮 | `14px` (text-sm) | `700` (font-bold) | `--font-mono` |
| 页脚文字 | `12px` (text-xs) | `400` | `--font-sans` |

**字距与行高：**

| 元素 | 属性 | 值 |
|---|---|---|
| Logo | `letter-spacing` | `-0.02em` |
| 区块标题 (h2) | `letter-spacing` | `-0.02em` |
| 正文描述 | `line-height` | `1.625` (leading-relaxed) |

### 间距令牌

| 元素 | 间距模式 | 值 |
|---|---|---|
| `<main>` 顶部 | `padding-top` | `56px` (pt-14) / `64px` (md:pt-16) |
| 各区块垂直间距 | `padding` | `32px` (py-8) / `48px` (md:py-12) |
| 区块标题下间距 | `margin-bottom` | `24px` (mb-6) |
| 要闻摘要卡片内边距 | `padding` | `24px` (p-6) / `32px` (md:p-8) |
| 新闻条目内部间距 | `gap` | `12px` (gap-3) |
| 新闻条目间分隔 | `padding-bottom + margin-bottom` | `24px` (pb-6 mb-6) |
| 时间线左侧偏移 | `padding-left` | `32px` (pl-8) |
| 时间线条目间距 | `padding-bottom` | `32px` (pb-8) |
| 关于卡片内边距 | `padding` | `24px` (p-6) |
| 关于卡片网格间距 | `gap` | `16px` (gap-4) |
| 页脚内边距 | `padding` | `16px` (py-4) |

### 阴影令牌

| 令牌 | 值 | 使用位置 |
|---|---|---|
| `--shadow` | `2px 2px 0px rgba(0,0,0,1)` | 导航栏 `box-shadow` |
| `--shadow` | `2px 2px 0px var(--foreground)` | 要闻摘要卡片、关于卡片 |
| `--shadow` | `2px 2px 0px var(--foreground)` | CTA按钮 |
| `--shadow` | `2px 2px 0px var(--foreground)` | 回到顶部按钮 |

> 注：设计系统定义了 `shadow-xs` 至 `shadow-xl` 六个级别，但所有级别实际值相同（`2px 2px 0px`），仅 `shadow-xs` 透明度为 `0.5`。本页未使用 `shadow-xs`。

### 边框令牌

| 令牌 | 值 | 使用位置 |
|---|---|---|
| `--border` | `#ffffff` | 卡片边框 `1px solid`、新闻条目分隔线、页脚顶边框 |
| `--accent` | `#0040ff` | Logo底部装饰线 `2px solid` |

### 圆角令牌

| 令牌 | 值 | 说明 |
|---|---|---|
| `--radius` | `0px` | 全站无圆角，采用锐利/Brutalist风格 |

---

## 3. 页面结构

### 3.1 导航栏 (Navbar)

- **HTML 结构**：`<nav>` > `<div>` (max-w-3xl 容器) > Logo `<a>` + 导航链接 `<div>`
- **视觉描述**：黑色全宽条带，固定于页面顶部，高度 `56px`（移动端）/ `64px`（桌面端）。带有 `2px 2px 0px` 黑色硬阴影，形成悬浮立体效果。
- **CSS 属性**：
  - `position: fixed; top: 0; left: 0; width: 100%; z-index: 50; height: 56px`
  - `background: var(--primary)` (#111111)
  - `color: var(--primary-foreground)` (#ffffff)
  - `box-shadow: 2px 2px 0px var(--foreground)` (#111111)
  - 容器：`max-width: 768px` (max-w-3xl), `margin: 0 auto`, `padding: 0 16px` (移动端) / `0` (桌面端)

### 3.2 今日AI要闻区块 (Section 1)

- **HTML 结构**：`<section>` > `<div>` (max-w-3xl) > `<h2>` + `<div>` (摘要卡片) > 新闻条目 x3 + CTA
- **视觉描述**：灰色背景页面上，标题区"今日AI要闻"以等宽粗体呈现，下方为一张白色卡片，内含三条新闻摘要，每条以分类标签+标题+描述构成，条目间以白色水平线分隔。底部有黑色CTA按钮引导至详情页。
- **CSS 属性**：
  - 区块：`padding: 32px 16px`（移动）/ `48px 0`（桌面）
  - 标题：`font-family: var(--font-mono); font-size: 24px; font-weight: 700; color: var(--foreground); letter-spacing: -0.02em`
  - 卡片：`background: var(--card); box-shadow: 2px 2px 0px var(--foreground); border: 1px solid var(--border); padding: 24px` (移动) / `32px` (桌面)
  - 条目分隔线：`border-bottom: 1px solid var(--border)`
  - CTA区域顶部分隔线：`border-top: 1px solid var(--border)`

### 3.3 历史新闻区块 (Section 2)

- **HTML 结构**：`<section>` > `<div>` (max-w-3xl) > `<h2>` + `<div>` (relative 容器) > 竖线 `<div>` + 时间线条目 x3
- **视觉描述**：左侧有一条 `2px` 宽的黑色竖线，每个时间线条目左侧有一个 `16x16px` 黑色圆点标记。条目由日期标签、标题、描述文字、"查看详情"链接组成。
- **CSS 属性**：
  - 时间线竖线：`width: 2px; background: var(--foreground); position: absolute; left: 0; top: 0; bottom: 0`
  - 日期圆点：`width: 16px; height: 16px; background: var(--foreground); transform: translateX(-7px); position: absolute; left: -32px; top: 0`
  - 日期文字：`font-family: var(--font-mono); font-size: 12px; font-weight: 700; color: var(--muted-foreground)`
  - 查看详情链接：`font-family: var(--font-mono); font-size: 14px; font-weight: 700; color: var(--accent)` (#0040ff)

### 3.4 关于区块 (Section 3)

- **HTML 结构**：`<section>` > `<div>` (max-w-3xl) > `<h2>` + `<div>` (grid) > 关于卡片 x2
- **视觉描述**：桌面端呈双栏网格布局，每张卡片包含标题与说明文字。移动端堆叠为单栏。
- **CSS 属性**：
  - 网格：`grid-template-columns: 1fr`（移动）/ `repeat(2, 1fr)` (md) / `gap: 16px`
  - 卡片：`background: var(--card); box-shadow: 2px 2px 0px var(--foreground); border: 1px solid var(--border); padding: 24px`

### 3.5 页脚 (Footer)

- **HTML 结构**：`<footer>` > `<div>` (max-w-3xl) > 版权 `<span>` + 免责声明 `<span>`
- **视觉描述**：灰色卡片背景，顶部白色边框，左右分布版权与免责文字。
- **CSS 属性**：
  - `background: var(--card); border-top: 1px solid var(--border); padding: 16px`
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

### 导航链接样式
- **字体**：`var(--font-mono)`
- **字号**：`14px` (text-sm)
- **颜色**：`var(--primary-foreground)` (#ffffff)
- **装饰**：`text-decoration: none`
- **过渡**：`transition: color 150ms`
- **可见性**：移动端隐藏 (`hidden md:inline-block`)，桌面端显示
- 首页包含两个链接："历史新闻"（锚点 `#history`）和"关于"（锚点 `#about`）

### 阴影/边框处理
- `box-shadow: 2px 2px 0px var(--foreground)` — 硬阴影，Brutalist 风格
- 无额外边框

---

## 5. 内容组件规范

### 5.1 今日要闻摘要卡片

- **组件名称**：今日AI要闻摘要卡片
- **视觉结构**：白色背景矩形卡片，内含3个新闻条目 + 底部CTA按钮
- **CSS 属性**：
  - `background: var(--card)` (#d8dada)
  - `box-shadow: 2px 2px 0px var(--foreground)` (#111111)
  - `border: 1px solid var(--border)` (#ffffff)
  - `border-radius: 0px`
  - `padding: 24px`（移动）/ `32px`（桌面）
- **内容排版层级**：
  1. 条目标题行：分类标签 `<span>` + 标题 `<h3>`，横向排列
  2. 描述段落 `<p>`
  3. 条目间分隔：`border-bottom: 1px solid var(--border)`
  4. CTA 按钮：`background: var(--primary); color: var(--primary-foreground); padding: 8px 16px; box-shadow: 2px 2px 0px var(--foreground); font-size: 14px; font-weight: 700`

### 5.2 新闻条目（摘要卡片内）

- **组件名称**：新闻摘要条目
- **视觉结构**：标签与标题同行，下方描述段落
- **CSS 属性**：
  - 容器：`display: flex; flex-direction: column; gap: 12px`
  - 分隔：`padding-bottom: 24px; margin-bottom: 24px; border-bottom: 1px solid var(--border)`
  - 标签行：`display: flex; align-items: center; gap: 12px`

### 5.3 时间线条目

- **组件名称**：历史新闻时间线条目
- **视觉结构**：黑色圆点标记 + 日期 + 标题 + 描述 + 链接
- **CSS 属性**：
  - 外层容器：`position: relative; padding-bottom: 32px`
  - 圆点：`width: 16px; height: 16px; background: var(--foreground); transform: translateX(-7px)`
  - 内容区：`display: flex; flex-direction: column; gap: 8px`
  - 日期标签：`font-family: var(--font-mono); font-size: 12px; font-weight: 700; color: var(--muted-foreground)`
  - 标题：`font-family: var(--font-mono); font-size: 16px; font-weight: 700; color: var(--foreground)`
  - 描述：`font-size: 14px; line-height: 1.625; color: var(--muted-foreground); font-family: var(--font-sans)`
  - 链接：`font-family: var(--font-mono); font-size: 14px; font-weight: 700; color: var(--accent)`

### 5.4 关于卡片

- **组件名称**：信息介绍卡片
- **视觉结构**：白色背景矩形，标题 + 段落文字
- **CSS 属性**：
  - `background: var(--card)` (#d8dada)
  - `box-shadow: 2px 2px 0px var(--foreground)` (#111111)
  - `border: 1px solid var(--border)` (#ffffff)
  - `padding: 24px`
- **标题**：`font-family: var(--font-mono); font-size: 16px; font-weight: 700; color: var(--foreground); margin-bottom: 12px`
- **描述**：`font-size: 14px; line-height: 1.625; color: var(--muted-foreground); font-family: var(--font-sans)`

### 5.5 CTA 按钮

- **组件名称**：主操作按钮
- **CSS 属性**：
  - `background: var(--primary)` (#111111)
  - `color: var(--primary-foreground)` (#ffffff)
  - `padding: 8px 16px`
  - `box-shadow: 2px 2px 0px var(--foreground)` (#111111)
  - `font-family: var(--font-mono); font-size: 14px; font-weight: 700`
  - `text-decoration: none`
  - `display: inline-flex; align-items: center`

---

## 6. 分类标签配色体系

首页摘要卡片中使用了3个分类标签，采用**填充背景 + 白色文字**样式（与详情页的描边样式不同）。

| 分类名称 | 图标 | 背景色 | 色值 | 文字颜色 | 样式 |
|---|---|---|---|---|---|
| 行业 | 无（纯文字） | `var(--accent)` | `#0040ff` | `var(--accent-foreground)` `#ffffff` | `background: var(--accent); color: #ffffff; padding: 2px 8px; font-size: 12px; font-weight: 700` |
| 研究 | 无（纯文字） | `var(--chart-3)` | `#6b90ff` | `var(--accent-foreground)` `#ffffff` | `background: var(--chart-3); color: #ffffff; padding: 2px 8px; font-size: 12px; font-weight: 700` |
| 政策 | 无（纯文字） | `var(--destructive)` | `#d73333` | `var(--destructive-foreground)` `#ffffff` | `background: var(--destructive); color: #ffffff; padding: 2px 8px; font-size: 12px; font-weight: 700` |

> 注：首页标签为 `inline-flex` + `text-xs` + `font-bold`，无自定义 CSS class，样式通过内联 style 实现。

---

## 7. 交互行为

### 回到顶部按钮
- **显示阈值**：页面滚动超过 `300px`（`window.scrollY > 300`）
- **动画**：CSS `transition: opacity 200ms`，通过 `opacity: 0/1` 和 `pointer-events: none/auto` 切换可见性
- **点击行为**：`window.scrollTo({top: 0, behavior: 'smooth'})` 平滑滚动至顶部
- **监听方式**：`window.addEventListener('scroll', toggle, {passive: true})` — 被动事件监听，不影响滚动性能

### 链接悬停效果
- 导航链接：`transition-colors duration-150`（Tailwind class），内联无额外 hover 样式
- 查看详情链接（时间线）：无显式 hover 效果定义

### 卡片悬停效果
- 首页卡片**无悬停动效**（与详情页 `.news-card:hover` 不同）

### 平滑滚动
- 回到顶部按钮使用 `behavior: 'smooth'`
- 导航锚点链接（`#history`、`#about`）依赖浏览器默认跳转行为，未设置 `scroll-behavior: smooth`

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
| 区块垂直间距 | `padding: 32px 16px` (py-8 px-4) |
| 要闻卡片内边距 | `padding: 24px` (p-6) |
| 关于区块布局 | 单栏堆叠 (`grid-cols-1`) |
| 导航链接 | 隐藏 (`hidden md:inline-block`) |

### 桌面端 (md, >=768px)

| 属性 | 值 |
|---|---|
| 导航栏高度 | `64px` (md:h-16) |
| 主内容顶部偏移 | `padding-top: 64px` (md:pt-16) |
| 容器左右内边距 | `padding: 0` (md:px-0) |
| 区块垂直间距 | `padding: 48px 0` (md:py-12) |
| 要闻卡片内边距 | `padding: 32px` (md:p-8) |
| 关于区块布局 | 双栏网格 (`md:grid-cols-2`) |
| 导航链接 | 显示 (`md:inline-block`) |

---

## 10. 可访问性

### 语义化 HTML
- `<nav>` — 导航栏
- `<main>` — 页面主内容
- `<section>` — 各内容区块（今日要闻、历史新闻、关于）
- `<h2>` — 区块标题
- `<h3>` — 新闻条目标题
- `<footer>` — 页脚
- `<article>` — 本页未使用（仅详情页使用）

### ARIA 标签
- 回到顶部按钮：`aria-label="回到顶部"`

### 焦点状态
- 依赖 Tailwind CSS 默认焦点环（使用 `--ring` 变量 `#000000`）
- 页面中未显式定义自定义焦点样式

### 减弱动效支持
- 首页**未显式定义** `prefers-reduced-motion` 媒体查询（回到顶部按钮的 `transition: opacity 200ms` 未做减弱处理）
