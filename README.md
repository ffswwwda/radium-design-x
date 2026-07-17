# radium-design-x

**Radium 未来感设计风格系统 · 我们改造版**（WorkBuddy Skill）

基于 Cosmin Capitanu (Dribbble: Radium) 的玻璃拟态 + 三色霓虹渐变风格，在原版基础上做了一处核心升级：

> **图标系统重写** —— 从原来薄弱的「用渐变背景」一句话指引，升级为一套完整的 **SVG sprite 图标系统**（三色渐变描边 `i-*` + 渐变底方块白图标 `w-*`），并确立铁律 **绝不用 emoji 当图标**。原版演示里的 🎨✨💫🌐🖱️🔄 等 emoji 全部改写为 SVG。

## 参考实现
- 线上范例：https://ffswwwda.github.io/user-research-console/ （用户研究预测引擎，本风格的完整落地）
- 图标演示：`references/icon-system.html`（可直接打开 / 复制即用）
- favicon：`assets/favicon.svg`（三色渐变小鱼）

## 结构
```
radium-design-x/
├── SKILL.md                    # 设计风格系统 + 图标系统（核心改造）+ 参考实现
├── references/icon-system.html # 独立图标演示页
├── assets/favicon.svg          # 三色渐变小鱼 favicon
└── README.md
```

## 安装
把本仓库放到 `~/.workbuddy/skills/radium-design-x/`，即可在 WorkBuddy 对话中调用。

## 图标写法速览
```html
<!-- body 开头注入一次 sprite（含 <linearGradient id="uiGrad">） -->
<!-- 渐变描边图标（透明/玻璃背景上） -->
<svg class="ic-svg"><use href="#i-globe"/></svg>
<!-- 白色图标（渐变底方块里，容器 color:#fff） -->
<div class="card-icon"><svg><use href="#w-sparkle"/></svg></div>
```
配色统一：`#00d4ff → #a855f7 → #ff6b9d`（135° 三色渐变）。

## 品牌来源
Radium design language by Cosmin Capitanu (https://dribbble.com/cosmin_capitanu).
