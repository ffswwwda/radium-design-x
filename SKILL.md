---
name: "radium-design-x"
version: "10.0"
description: "Radium 未来感设计风格系统（我们改造版）。玻璃拟态、三色霓虹渐变(#00d4ff→#a855f7→#ff6b9d 135°)、科技光效，核心升级为一套 SVG sprite 图标系统（渐变描边 + 白图标，绝不用 emoji）。参考实现见用户研究预测引擎页面。Invoke when designing futuristic dashboards, data-viz consoles, AR/VR interfaces, or tech-forward web apps that need a clean gradient SVG icon system."
---

# Radium 未来感设计风格 · 改造版

基于 Cosmin Capitanu (Dribbble: Radium) 的设计风格，打造沉浸式、科技感的数字界面。

> **本版相对原版的改动**：把原来薄弱的图标指引，升级成一套完整的 **SVG sprite 图标系统**（三色渐变描边 + 白图标模板 + CSS + 用法 + 校验），并确立**铁律：绝不用 emoji 当图标**。所有 emoji 图标改写为 SVG。参考页面用我们做的「用户研究预测引擎」。

### 参考实现（模仿对象）
- 线上范例：**https://ffswwwda.github.io/user-research-console/** —— 玻璃拟态 + 三色渐变 + SVG 图标系统的完整落地
- 独立图标演示：`references/icon-system.html`（可直接打开 / 复制即用）
- favicon 源码：`assets/favicon.svg`（三色渐变小鱼）

---

## 🔄 完整工作流

```
用户需求 → 结构搭建 → 元素分类 → 提示词编写 → 用户生成 → 评估验收 → 集成上线
```

### 阶段一：需求分析与结构搭建
1. 理解用户业务场景和核心功能
2. 设计页面结构和信息架构
3. 确定需要的视觉元素类型

### 阶段二：元素分类（前端 vs 生图）

| 类型 | 前端可实现 | 需要生图/视频 |
|------|-----------|--------------|
| UI组件（卡片、按钮、表单） | ✅ | ❌ |
| 数据可视化图表 | ✅ | ❌ |
| 玻璃拟态效果 | ✅ | ❌ |
| 渐变与光效 | ✅ | ❌ |
| 自定义光标与粒子效果 | ✅ | ❌ |
| 交互动画 | ✅ | ❌ |
| 3D设备渲染图 | ❌ | ✅ |
| 未来感场景背景 | ❌ | ✅ |
| AR/VR界面概念图 | ❌ | ✅ |
| 产品展示图 | ❌ | ✅ |
| 动态效果演示视频 | ❌ | ✅ |

### 阶段三：提示词编写
为需要生图的元素编写详细提示词，包括：
- 主题描述
- 风格要求
- 配色方案
- 构图要求
- 细节描述

### 阶段四：用户生成
用户使用AI绘图工具（如Midjourney、Stable Diffusion）生成资产

### 阶段五：评估验收
检查生成结果是否符合要求，确认后集成到项目中

---

## 🎨 设计风格特征

### 1. 玻璃拟态 (Glassmorphism)
- 半透明背景配合模糊效果
- 使用 backdrop-filter: blur() 实现毛玻璃质感
- 边框使用半透明白色或浅色
- 背景渐变增加层次感

```css
/* 暗色模式 */
.glass-card-dark {
    background: rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.12);
    border-radius: 20px;
}

/* 浅色模式 */
.glass-card-light {
    background: rgba(255, 255, 255, 0.6);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(0, 0, 0, 0.08);
    border-radius: 20px;
}
```

### 2. 配色系统

#### 暗色模式（Dark Mode）
- 主色调：深邃蓝紫 (#0f1525 - #1a1f3a)
- 强调色：青色 (#00d4ff)、粉色 (#ff6b9d)、紫色 (#a855f7)
- 渐变方向：对角线、环形、径向渐变

```css
.gradient-dark-primary {
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
}
```

#### 浅色模式（Light Mode）
- 主色调：暖灰白 (#F7F5F5 - #F1F1F1)、淡蓝白 (#E5F4F7)
- 强调色：柔和青色 (#00C3F3)、金属金色 (#DBB360 / #CA983B)、淡紫色 (#BFBADE / #877A87)
- 渐变方向：柔和的对角线渐变

```css
.gradient-light-primary {
    background: linear-gradient(135deg, #00C3F3 0%, #A5CCD4 50%, #BFBADE 100%);
}

.gradient-light-gold {
    background: linear-gradient(135deg, #DBB360 0%, #CA983B 100%);
}
```

### 3. 光效与阴影

#### 暗色模式
- 内发光效果增强立体感
- 柔和的外阴影营造漂浮感
- 辉光效果突出重点元素

```css
.glow-dark {
    box-shadow: 0 0 30px rgba(0, 212, 255, 0.3),
                0 0 60px rgba(168, 85, 247, 0.2),
                inset 0 1px 0 rgba(255, 255, 255, 0.1);
}
```

#### 浅色模式
- 柔和的阴影代替发光
- 轻微的内阴影增加质感
- 金色/青色点缀光效

```css
.glow-light {
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.08),
                inset 0 1px 0 rgba(255, 255, 255, 0.6);
}

.glow-light-gold {
    box-shadow: 0 0 20px rgba(219, 179, 96, 0.3),
                inset 0 1px 0 rgba(255, 255, 255, 0.8);
}
```

### 4. 空间层次感
- Z轴深度：通过阴影、透明度、缩放营造
- 卡片层叠：前后关系清晰
- 视差效果：背景与前景独立移动

### 5. 科技感元素
- 网格背景增加空间感
- 数据可视化图表使用渐变填充
- 图标使用简洁几何线条

---

## 🎨 浅色模式设计指南

### 1. 色彩特征

基于 Radium 的浅色作品（Summer Vibes、Summer Vibes 2、LightUp）分析：

| 作品 | 背景色 | 主强调色 | 辅助色 | 金属色 |
|------|--------|----------|--------|--------|
| Summer Vibes | #E5F4F7 (淡蓝白) | #00C3F3 (亮青) | #BFBADE (淡紫) | - |
| Summer Vibes 2 | #F7F5F5 (暖灰白) | #A5CCD4 (淡青) | #877A87 (灰紫) | #CA983B (金色) |
| LightUp | #DEDAD5 (暖灰) | #F1900E (橙色) | - | - |
| Logo | #F1F1F1 (纯白) | - | #A7A49F (灰) | #DBB360 (金色) |

### 2. 设计原则

- **暖灰底色**：避免冷白，使用 #F7F5F5 或 #F1F1F1
- **柔和蓝绿点缀**：#A5CCD4、#00C3F3、#02AFE9
- **金属暖色点缀**：金色系 #DBB360、#CA983B
- **淡雅紫色调和**：#BFBADE、#877A87、#4E3AA1
- **浅灰文字**：#414546、#3B3B3C
- **玻璃拟态**：白色半透明 + 浅色模糊

---

## ⚡ 交互设计体系

### 1. 自定义光标系统

Radium风格的核心交互特征之一，包含多层光标效果：

```css
.custom-cursor {
    position: fixed;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    pointer-events: none;
    z-index: 9999;
    mix-blend-mode: screen;
    box-shadow: 0 0 20px #00d4ff, 0 0 40px #a855f7;
    transform: translate(-50%, -50%);
    transition: width 0.3s ease, height 0.3s ease;
}

.cursor-glow {
    position: fixed;
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(0, 212, 255, 0.3) 0%, transparent 70%);
    pointer-events: none;
    z-index: 9998;
    transform: translate(-50%, -50%);
    transition: all 0.1s ease;
}

.particle {
    position: fixed;
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: #00d4ff;
    pointer-events: none;
    z-index: 9997;
    opacity: 0.8;
}
```

```javascript
const cursor = document.getElementById('cursor');
const cursorGlow = document.getElementById('cursorGlow');
let particles = [];

function moveCursor(e) {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top = e.clientY + 'px';
    cursorGlow.style.left = e.clientX + 'px';
    cursorGlow.style.top = e.clientY + 'px';
    createParticle(e.clientX, e.clientY);
}

function createParticle(x, y) {
    if (particles.length > 20) {
        particles[0].remove();
        particles.shift();
    }
    const particle = document.createElement('div');
    particle.className = 'particle';
    particle.style.left = x + 'px';
    particle.style.top = y + 'px';
    document.body.appendChild(particle);
    particles.push(particle);
    
    let opacity = 0.8, scale = 1;
    function animate() {
        opacity -= 0.02;
        scale -= 0.03;
        particle.style.opacity = opacity;
        particle.style.transform = `translate(-50%, -50%) scale(${scale})`;
        if (opacity > 0) requestAnimationFrame(animate);
        else { particle.remove(); particles = particles.filter(p => p !== particle); }
    }
    animate();
}

function handleMouseEnter() {
    cursor.style.width = '40px';
    cursor.style.height = '40px';
    cursorGlow.style.width = '150px';
    cursorGlow.style.height = '150px';
}

function handleMouseLeave() {
    cursor.style.width = '20px';
    cursor.style.height = '20px';
    cursorGlow.style.width = '100px';
    cursorGlow.style.height = '100px';
}

document.addEventListener('mousemove', moveCursor);
document.querySelectorAll('.btn, .glass-card, .stat-card, .gradient-item').forEach(el => {
    el.addEventListener('mouseenter', handleMouseEnter);
    el.addEventListener('mouseleave', handleMouseLeave);
});
```

### 2. 卡片深度交互

多层级动画效果，营造空间感：

```css
.glass-card {
    background: rgba(255, 255, 255, 0.06);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.12);
    border-radius: 24px;
    padding: 40px 32px;
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    position: relative;
    overflow: hidden;
}

.glass-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 4px;
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    opacity: 0;
    transform: scaleX(0);
    transition: all 0.4s ease;
}

.glass-card:hover::before {
    opacity: 1;
    transform: scaleX(1);
}

.glass-card:hover {
    transform: translateY(-12px) rotateX(2deg);
    border-color: rgba(0, 212, 255, 0.4);
    box-shadow: 
        0 25px 50px rgba(0, 0, 0, 0.2),
        0 0 40px rgba(0, 212, 255, 0.15),
        0 0 80px rgba(168, 85, 247, 0.1),
        inset 0 1px 0 rgba(255, 255, 255, 0.1);
}

.card-icon {
    width: 70px;
    height: 70px;
    border-radius: 20px;
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 32px;
    margin-bottom: 24px;
    transition: transform 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
}

.glass-card:hover .card-icon {
    transform: scale(1.15) rotate(5deg);
}

.card-title::after {
    content: '';
    position: absolute;
    bottom: -8px;
    left: 0;
    width: 40px;
    height: 3px;
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    opacity: 0;
    transform: scaleX(0);
    transition: all 0.4s ease;
}

.glass-card:hover .card-title::after {
    opacity: 1;
    transform: scaleX(1);
}
```

### 3. 按钮光效扫过动画

```css
.btn {
    padding: 16px 40px;
    border-radius: 16px;
    font-size: 18px;
    font-weight: 700;
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    border: none;
    position: relative;
    overflow: hidden;
}

.btn::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.3) 50%, transparent 70%);
    transform: translateX(-100%);
    transition: transform 0.6s ease;
}

.btn:hover::before {
    transform: translateX(100%);
}

.btn-primary {
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    color: white;
    box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
}

.btn-primary:hover {
    transform: translateY(-4px) scale(1.05);
    box-shadow: 0 20px 50px rgba(0, 212, 255, 0.4), 0 0 30px rgba(168, 85, 247, 0.3);
}
```

### 4. 渐变卡片交互

```css
.gradient-item {
    width: 140px;
    height: 140px;
    border-radius: 20px;
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    position: relative;
    overflow: hidden;
}

.gradient-item::after {
    content: '';
    position: absolute;
    top: 0; left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
    transition: left 0.6s ease;
}

.gradient-item:hover::after {
    left: 100%;
}

.gradient-item:hover {
    transform: scale(1.15) rotate(5deg);
    box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
}
```

### 5. 统计卡片动效

```css
.stat-card {
    background: rgba(255, 255, 255, 0.06);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.12);
    border-radius: 20px;
    padding: 32px;
    text-align: center;
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.stat-card:hover {
    transform: translateY(-8px) scale(1.02);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
    border-color: rgba(0, 212, 255, 0.3);
}

.stat-value {
    font-size: 42px;
    font-weight: 800;
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 12px;
    transition: transform 0.4s ease;
}

.stat-card:hover .stat-value {
    transform: scale(1.1);
}
```

### 6. 列表项滑动动效

```css
.feature-item {
    display: flex;
    align-items: center;
    gap: 24px;
    padding: 32px;
    background: rgba(255, 255, 255, 0.04);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    margin-bottom: 20px;
    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    border: 1px solid transparent;
}

.feature-item:hover {
    transform: translateX(12px);
    border-color: rgba(0, 212, 255, 0.3);
    background: rgba(255, 255, 255, 0.08);
}

.feature-icon {
    width: 50px;
    height: 50px;
    border-radius: 14px;
    background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    flex-shrink: 0;
    transition: transform 0.4s ease;
}

.feature-item:hover .feature-icon {
    transform: scale(1.2) rotate(10deg);
}
```

### 7. 页面入场动画

```css
@keyframes fadeInDown {
    from { opacity: 0; transform: translateY(-30px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeInUp {
    from { opacity: 0; transform: translateY(30px); }
    to { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.05); }
}

.title {
    animation: fadeInDown 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

.glass-card:nth-child(1) { animation: fadeInUp 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0.1s both; }
.glass-card:nth-child(2) { animation: fadeInUp 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0.2s both; }
.glass-card:nth-child(3) { animation: fadeInUp 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0.3s both; }
.glass-card:nth-child(4) { animation: fadeInUp 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0.4s both; }
```

### 8. 视差滚动效果

```css
.parallax-bg {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: 
        radial-gradient(circle at 20% 80%, rgba(0, 212, 255, 0.08) 0%, transparent 50%),
        radial-gradient(circle at 80% 20%, rgba(168, 85, 247, 0.08) 0%, transparent 50%);
    transform: translateZ(-1px) scale(1.5);
    pointer-events: none;
}

.parallax-grid {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: 
        linear-gradient(rgba(0, 212, 255, 0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0, 212, 255, 0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    transform: translateZ(-0.5px) scale(1.2);
    pointer-events: none;
}
```

```javascript
window.addEventListener('scroll', () => {
    const scrollY = window.scrollY;
    document.querySelector('.parallax-bg').style.transform = `translateZ(-1px) scale(1.5) translateY(${scrollY * 0.3}px)`;
    document.querySelector('.parallax-grid').style.transform = `translateZ(-0.5px) scale(1.2) translateY(${scrollY * 0.1}px)`;
});
```

### 9. 输入框动效

```css
.radium-input-group {
    position: relative;
    margin-bottom: 24px;
}

.radium-input {
    width: 100%;
    padding: 16px 20px;
    font-size: 16px;
    background: rgba(255, 255, 255, 0.06);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.12);
    border-radius: 16px;
    color: inherit;
    transition: all 0.4s var(--radium-easing);
    outline: none;
}

.radium-input:focus {
    border-color: rgba(0, 212, 255, 0.5);
    box-shadow: 
        0 0 20px rgba(0, 212, 255, 0.2),
        inset 0 1px 0 rgba(255, 255, 255, 0.1);
    background: rgba(255, 255, 255, 0.08);
}

.radium-input-label {
    position: absolute;
    top: 50%;
    left: 20px;
    transform: translateY(-50%);
    font-size: 16px;
    color: rgba(255, 255, 255, 0.5);
    pointer-events: none;
    transition: all 0.3s var(--radium-easing);
}

.radium-input:focus + .radium-input-label,
.radium-input:not(:placeholder-shown) + .radium-input-label {
    top: -10px;
    left: 16px;
    font-size: 12px;
    color: var(--radium-cyan);
    padding: 0 8px;
    background: var(--radium-bg-dark);
}

.light .radium-input {
    background: rgba(255, 255, 255, 0.7);
    border-color: rgba(0, 0, 0, 0.08);
}

.light .radium-input:focus {
    border-color: rgba(0, 195, 243, 0.5);
    box-shadow: 0 0 20px rgba(0, 195, 243, 0.15);
}

.light .radium-input:focus + .radium-input-label,
.light .radium-input:not(:placeholder-shown) + .radium-input-label {
    background: var(--radium-bg-light);
    color: var(--radium-cyan-light);
}
```

```html
<div class="radium-input-group">
    <input type="text" class="radium-input" placeholder=" " id="email">
    <label class="radium-input-label" for="email">邮箱地址</label>
</div>
```

### 10. 滚动进度条

```css
.scroll-progress {
    position: fixed;
    top: 0;
    left: 0;
    height: 4px;
    background: var(--radium-gradient);
    z-index: 9999;
    transition: width 0.1s ease;
    box-shadow: 0 0 20px var(--radium-cyan);
}
```

```javascript
function updateScrollProgress() {
    const scrollTop = window.scrollY;
    const docHeight = document.documentElement.scrollHeight - window.innerHeight;
    const progress = (scrollTop / docHeight) * 100;
    document.querySelector('.scroll-progress').style.width = `${progress}%`;
}

window.addEventListener('scroll', updateScrollProgress);
```

### 11. 涟漪点击效果

```css
.ripple-container {
    position: relative;
    overflow: hidden;
}

.ripple {
    position: absolute;
    border-radius: 50%;
    background: rgba(0, 212, 255, 0.3);
    transform: scale(0);
    animation: ripple-animation 0.6s linear;
    pointer-events: none;
}

@keyframes ripple-animation {
    to {
        transform: scale(4);
        opacity: 0;
    }
}
```

```javascript
function createRipple(event) {
    const button = event.currentTarget;
    const circle = document.createElement('span');
    const diameter = Math.max(button.clientWidth, button.clientHeight);
    const radius = diameter / 2;
    
    circle.style.width = circle.style.height = `${diameter}px`;
    circle.style.left = `${event.clientX - button.getBoundingClientRect().left - radius}px`;
    circle.style.top = `${event.clientY - button.getBoundingClientRect().top - radius}px`;
    circle.classList.add('ripple');
    
    const ripple = button.getElementsByClassName('ripple')[0];
    if (ripple) ripple.remove();
    
    button.appendChild(circle);
}

document.querySelectorAll('.ripple-container').forEach(btn => {
    btn.addEventListener('click', createRipple);
});
```

### 12. 数字滚动动画

```css
.counter {
    font-variant-numeric: tabular-nums;
}
```

```javascript
function animateNumber(element, target, duration = 2000) {
    const start = parseFloat(element.textContent.replace(/[^0-9.]/g, ''));
    const startTime = performance.now();
    
    function update(currentTime) {
        const elapsed = currentTime - startTime;
        const progress = Math.min(elapsed / duration, 1);
        const easeOutQuart = 1 - Math.pow(1 - progress, 4);
        const current = start + (target - start) * easeOutQuart;
        
        element.textContent = typeof target === 'number' && target % 1 !== 0 
            ? current.toFixed(2) 
            : Math.floor(current).toLocaleString();
        
        if (progress < 1) {
            requestAnimationFrame(update);
        }
    }
    
    requestAnimationFrame(update);
}

animateNumber(document.querySelector('.counter'), 12800);
```

### 13. 玻璃拟态模态框

```css
.modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.6);
    backdrop-filter: blur(10px);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    visibility: hidden;
    transition: all 0.4s var(--radium-easing);
    z-index: 1000;
}

.modal-overlay.active {
    opacity: 1;
    visibility: visible;
}

.modal-content {
    background: rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 24px;
    padding: 40px;
    max-width: 500px;
    width: 90%;
    transform: scale(0.9) translateY(20px);
    transition: all 0.4s var(--radium-easing);
    box-shadow: 
        0 25px 50px rgba(0, 0, 0, 0.3),
        0 0 40px rgba(0, 212, 255, 0.1);
}

.modal-overlay.active .modal-content {
    transform: scale(1) translateY(0);
}

.light .modal-content {
    background: rgba(255, 255, 255, 0.9);
    border-color: rgba(0, 0, 0, 0.08);
}
```

```javascript
function openModal() {
    document.querySelector('.modal-overlay').classList.add('active');
}

function closeModal() {
    document.querySelector('.modal-overlay').classList.remove('active');
}
```

### 14. 悬浮下拉菜单

```css
.dropdown {
    position: relative;
}

.dropdown-menu {
    position: absolute;
    top: calc(100% + 12px);
    left: 0;
    min-width: 200px;
    background: rgba(255, 255, 255, 0.08);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: 16px;
    padding: 8px 0;
    opacity: 0;
    visibility: hidden;
    transform: translateY(-10px);
    transition: all 0.3s var(--radium-easing);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
    z-index: 100;
}

.dropdown:hover .dropdown-menu {
    opacity: 1;
    visibility: visible;
    transform: translateY(0);
}

.dropdown-item {
    padding: 12px 20px;
    cursor: none;
    transition: all 0.2s ease;
    font-size: 14px;
}

.dropdown-item:hover {
    background: rgba(0, 212, 255, 0.1);
    padding-left: 24px;
}

.light .dropdown-menu {
    background: rgba(255, 255, 255, 0.95);
    border-color: rgba(0, 0, 0, 0.08);
}

.light .dropdown-item:hover {
    background: rgba(0, 195, 243, 0.1);
}
```

### 15. 标签页切换

```css
.tabs-container {
    display: flex;
    gap: 8px;
    margin-bottom: 24px;
    background: rgba(255, 255, 255, 0.04);
    backdrop-filter: blur(10px);
    padding: 8px;
    border-radius: 16px;
}

.tab {
    padding: 12px 28px;
    border-radius: 12px;
    cursor: none;
    transition: all 0.3s var(--radium-easing);
    font-weight: 600;
    font-size: 14px;
    position: relative;
}

.tab.active {
    background: var(--radium-gradient);
    color: white;
    box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
}

.tab-content {
    display: none;
    animation: fadeInUp 0.4s var(--radium-easing);
}

.tab-content.active {
    display: block;
}
```

```javascript
document.querySelectorAll('.tab').forEach(tab => {
    tab.addEventListener('click', () => {
        document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
        document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
        tab.classList.add('active');
        document.getElementById(tab.dataset.content).classList.add('active');
    });
});
```

### 16. 渐变进度条

```css
.progress-bar-container {
    height: 8px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 8px;
}

.progress-bar {
    height: 100%;
    background: var(--radium-gradient);
    border-radius: 4px;
    transition: width 1s var(--radium-easing);
    box-shadow: 0 0 20px var(--radium-cyan);
    position: relative;
    overflow: hidden;
}

.progress-bar::after {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
    animation: progress-shine 2s infinite;
}

@keyframes progress-shine {
    100% { left: 100%; }
}

.progress-label {
    display: flex;
    justify-content: space-between;
    font-size: 14px;
    opacity: 0.6;
}
```

### 17. 骨架屏加载动画

```css
.skeleton {
    background: linear-gradient(
        90deg,
        rgba(255, 255, 255, 0.05) 25%,
        rgba(255, 255, 255, 0.1) 50%,
        rgba(255, 255, 255, 0.05) 75%
    );
    background-size: 200% 100%;
    animation: skeleton-loading 1.5s infinite;
    border-radius: 12px;
}

.light .skeleton {
    background: linear-gradient(
        90deg,
        rgba(0, 0, 0, 0.03) 25%,
        rgba(0, 0, 0, 0.06) 50%,
        rgba(0, 0, 0, 0.03) 75%
    );
}

@keyframes skeleton-loading {
    0% { background-position: 200% 0; }
    100% { background-position: -200% 0; }
}

.skeleton-card {
    padding: 32px;
    border-radius: 20px;
    background: rgba(255, 255, 255, 0.04);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 255, 255, 0.08);
}

.skeleton-row {
    height: 20px;
    margin-bottom: 12px;
}

.skeleton-row.short { width: 60%; }
.skeleton-row.medium { width: 80%; }
.skeleton-row.full { width: 100%; }

.skeleton-circle {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    margin-bottom: 16px;
}
```

### 18. 图表交互效果

```javascript
const chartOption = {
    tooltip: {
        trigger: 'axis',
        backgroundColor: 'rgba(255, 255, 255, 0.1)',
        backdropFilter: 'blur(10px)',
        borderColor: 'rgba(0, 212, 255, 0.3)',
        borderWidth: 1,
        textStyle: { color: '#fff' },
        formatter: (params) => {
            return params.map(p => `${p.marker} ${p.seriesName}: ${p.value}`).join('<br/>');
        }
    },
    series: [{
        type: 'line',
        data: [120, 200, 150, 80, 220, 180],
        lineStyle: {
            width: 3,
            color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [
                { offset: 0, color: '#00d4ff' },
                { offset: 1, color: '#a855f7' }
            ])
        },
        itemStyle: {
            color: '#00d4ff',
            borderColor: '#fff',
            borderWidth: 2
        },
        areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                { offset: 0, color: 'rgba(0, 212, 255, 0.4)' },
                { offset: 1, color: 'rgba(0, 212, 255, 0.02)' }
            ])
        },
        emphasis: {
            itemStyle: {
                color: '#ff6b9d',
                shadowBlur: 20,
                shadowColor: 'rgba(255, 107, 157, 0.5)'
            }
        }
    }]
};
```

---

## 📝 生图提示词模板（暗色模式）

### 模板1：未来感设备渲染图

```
A futuristic [设备类型] with Radium design style, glassmorphism finish, 
neon cyan and purple gradient accents, glowing edges, dark background, 
high-tech aesthetic, 8k resolution, ultra detailed, product photography, 
cinematic lighting, soft shadows, depth of field, minimalist composition

设备类型可选：smartwatch, smartphone, tablet, laptop, smart speaker, AR headset, VR goggles, smart home device
```

**示例：智能手表渲染图**
```
A futuristic smartwatch with Radium design style, glassmorphism watch face, 
neon cyan and purple gradient accents, glowing edges, dark navy background, 
high-tech aesthetic, 8k resolution, ultra detailed, product photography, 
cinematic lighting, soft shadows, depth of field, minimalist composition, 
floating UI elements around the watch
```

### 模板2：科技感场景背景

```
Abstract futuristic technology background, Radium design style, 
glassmorphism layers, neon gradient waves, dark blue purple color scheme, 
glowing geometric shapes, digital grid lines, particles floating, 
cinematic lighting, depth of field, ultra detailed, 8k, 
soft focus background for UI overlay
```

### 模板3：数据可视化概念图

```
Futuristic data visualization dashboard concept, Radium design style, 
glassmorphism charts and graphs, neon glowing data lines, 
dark theme interface, holographic projections, floating UI elements, 
cyberpunk aesthetic, high-tech, 8k resolution, product concept art, 
cinematic lighting, depth of field
```

### 模板4：智能家居场景

```
Futuristic smart home interior, Radium design style, 
glassmorphism furniture, neon accent lighting, 
dark modern decor, holographic displays on walls, 
smart devices integrated, cinematic lighting, 
ultra detailed, 8k resolution, architectural visualization
```

### 模板5：AR/VR界面概念

```
Futuristic AR/VR heads-up display interface, Radium design style, 
transparent glassmorphism UI panels, neon glowing icons, 
dark background with subtle grid, holographic text elements, 
data visualization overlays, cyberpunk aesthetic, high-tech, 
8k resolution, concept art, cinematic lighting
```

### 模板6：产品展示图

```
[产品名称] product photography, Radium design style, 
glassmorphism packaging, neon gradient accents, 
dark background, cinematic lighting, soft shadows, 
depth of field, minimalist composition, professional product shot, 
8k resolution, ultra detailed
```

---

## 📝 生图提示词模板（浅色模式）

### 模板1：未来感设备渲染图（浅色）

```
A futuristic [设备类型] with Radium light design style, glassmorphism finish, 
soft pastel cyan and gold accents, subtle glowing edges, warm light background, 
clean minimalist aesthetic, 8k resolution, ultra detailed, product photography, 
soft natural lighting, gentle shadows, depth of field, elegant composition

设备类型可选：smartwatch, smartphone, tablet, laptop, smart speaker, AR headset, VR goggles, smart home device
```

**示例：智能手表渲染图（浅色）**
```
A futuristic smartwatch with Radium light design style, glassmorphism watch face, 
soft pastel cyan and gold accents, subtle glowing edges, warm white background, 
clean minimalist aesthetic, 8k resolution, ultra detailed, product photography, 
soft natural lighting, gentle shadows, depth of field, elegant composition, 
floating UI elements around the watch
```

### 模板2：科技感场景背景（浅色）

```
Abstract futuristic technology background, Radium light design style, 
glassmorphism layers in soft white, pastel gradient waves, 
warm light blue and gold color scheme, subtle geometric shapes, 
soft digital grid lines, gentle particles floating, 
soft natural lighting, depth of field, ultra detailed, 8k, 
soft focus background for UI overlay
```

### 模板3：数据可视化概念图（浅色）

```
Futuristic data visualization dashboard concept, Radium light design style, 
glassmorphism charts and graphs in soft white, subtle pastel data lines, 
light theme interface with warm gray text, clean professional aesthetic, 
soft glowing accents, 8k resolution, product concept art, 
soft natural lighting, depth of field
```

### 模板4：智能家居场景（浅色）

```
Futuristic smart home interior, Radium light design style, 
glassmorphism furniture in soft white, warm accent lighting, 
light modern decor with gold touches, subtle holographic displays, 
smart devices integrated, soft natural lighting, 
ultra detailed, 8k resolution, architectural visualization
```

### 模板5：AR/VR界面概念（浅色）

```
Futuristic AR/VR heads-up display interface, Radium light design style, 
transparent glassmorphism UI panels in soft white, subtle glowing icons, 
light background with soft grid, clean text elements, 
data visualization overlays in pastel colors, clean modern aesthetic, 
8k resolution, concept art, soft natural lighting
```

### 模板6：产品展示图（浅色）

```
[产品名称] product photography, Radium light design style, 
glassmorphism packaging in soft white, pastel gradient accents, 
warm light background, soft natural lighting, gentle shadows, 
depth of field, minimalist composition, professional product shot, 
8k resolution, ultra detailed
```

---

## 🎥 生视频提示词模板

### 模板1：UI动效演示（暗色）

```
Motion design animation of futuristic UI interface, Radium design style, 
glassmorphism panels appearing with smooth transitions, 
neon gradients flowing, elements floating and glowing, 
dark background, 4k resolution, 60fps, cinematic, 
smooth easing animations, professional motion graphics
```

### 模板2：UI动效演示（浅色）

```
Motion design animation of futuristic UI interface, Radium light design style, 
glassmorphism panels appearing with smooth transitions, 
pastel gradients flowing, elements floating with subtle glow, 
warm light background, 4k resolution, 60fps, cinematic, 
smooth easing animations, professional motion graphics
```

### 模板3：产品360度展示（暗色）

```
360 degree rotation animation of futuristic [设备类型], 
Radium design style, glassmorphism finish, neon glowing edges, 
dark background, 4k resolution, 60fps, smooth rotation, 
cinematic lighting that follows the product, 
professional product animation
```

### 模板4：产品360度展示（浅色）

```
360 degree rotation animation of futuristic [设备类型], 
Radium light design style, glassmorphism finish, subtle gold glowing edges, 
warm light background, 4k resolution, 60fps, smooth rotation, 
soft natural lighting that follows the product, 
professional product animation
```

### 模板5：场景过渡动画（暗色）

```
Smooth camera transition through futuristic space, 
Radium design style, glassmorphism layers passing by, 
neon gradient light streaks, dark void background, 
4k resolution, 60fps, cinematic camera movement, 
depth of field, professional motion graphics
```

### 模板6：场景过渡动画（浅色）

```
Smooth camera transition through futuristic space, 
Radium light design style, glassmorphism layers passing by, 
pastel gradient light streaks, warm light background, 
4k resolution, 60fps, cinematic camera movement, 
depth of field, professional motion graphics
```

---

## ✅ 评估验收标准

### 图片验收清单（暗色模式）
- [ ] 配色符合Radium风格（深邃蓝紫底色+霓虹青/粉/紫强调）
- [ ] 玻璃拟态效果明显（半透明+模糊）
- [ ] 光效和阴影层次丰富
- [ ] 分辨率足够（至少2048x2048）
- [ ] 构图适合UI集成（留有空间放置文字和控件）
- [ ] 细节丰富但不干扰UI内容
- [ ] 整体氛围统一

### 图片验收清单（浅色模式）
- [ ] 配色符合Radium风格（暖灰白底色+柔和青/金/紫强调）
- [ ] 玻璃拟态效果明显（白色半透明+浅色模糊）
- [ ] 阴影柔和自然，无刺眼光效
- [ ] 分辨率足够（至少2048x2048）
- [ ] 构图适合UI集成（留有空间放置文字和控件）
- [ ] 细节丰富但不干扰UI内容
- [ ] 整体氛围统一，干净优雅

### 视频验收清单
- [ ] 分辨率≥4K，帧率≥60fps
- [ ] 动画流畅无卡顿
- [ ] 风格统一，符合Radium设计语言
- [ ] 时长适合场景（通常5-15秒循环）
- [ ] 文件大小合理（建议使用WebM格式）
- [ ] 无缝循环（如果需要）

### 交互验收清单
- [ ] 自定义光标跟随流畅无卡顿，hover交互元素时放大效果明显
- [ ] 卡片hover效果自然（上浮、旋转、边框光效、顶部渐变条展开）
- [ ] 按钮光效扫过动画流畅，hover时放大+发光效果协调
- [ ] 粒子效果不过度干扰内容，数量控制在合理范围
- [ ] 所有动画使用统一的缓动曲线（cubic-bezier(0.25, 0.46, 0.45, 0.94)）
- [ ] 移动端自动禁用自定义光标，使用系统光标
- [ ] 输入框动效：focus时标签上浮、边框发光，符合Material Design风格
- [ ] 滚动进度条：顶部渐变进度条跟随滚动平滑更新
- [ ] 涟漪效果：点击按钮时产生扩散涟漪，600ms内自动消失
- [ ] 数字滚动动画：页面加载后数字平滑滚动到目标值，使用easeOutQuart缓动
- [ ] 模态框：打开/关闭时有缩放+位移过渡，背景模糊效果明显
- [ ] 下拉菜单：hover时平滑展开，item hover有背景色变化和缩进效果
- [ ] 标签页切换：点击切换时有fadeInUp入场动画，样式切换流畅
- [ ] 渐变进度条：进度条有光泽扫过动画，颜色符合Radium渐变配色
- [ ] 骨架屏加载：闪烁动画流畅，布局占位合理
- [ ] 明暗模式切换：所有元素颜色平滑过渡，无视觉闪烁
- [ ] 视差滚动效果：背景层与前景层独立移动，营造空间感

---

## 📦 组件设计规范

### 按钮
- 圆角：12-16px
- 渐变背景或透明边框
- hover时放大+发光效果
- 光泽扫过动画

### 卡片
- 圆角：16-24px
- 玻璃拟态背景
- 悬浮阴影
- 顶部装饰性渐变条
- hover时上浮+旋转效果

### 图标系统（核心 · 改造版重点）

> **铁律：绝对不要用 emoji 当图标。** 全部用内联 SVG sprite + 共享渐变。原版演示里的 🎨✨💫🌐🖱️🔄 等 emoji 已全部改写为下方的 SVG 图标。

#### 1. 在 `<body>` 开头注入 sprite（一次定义，全站 `<use>` 复用）

```html
<svg width="0" height="0" style="position:absolute" aria-hidden="true">
  <defs>
    <linearGradient id="uiGrad" x1="0" y1="0" x2="1" y2="1">
      <stop offset="0" stop-color="#00d4ff"/>
      <stop offset=".5" stop-color="#a855f7"/>
      <stop offset="1" stop-color="#ff6b9d"/>
    </linearGradient>
  </defs>
  <!-- 渐变描边图标（导航/卡/按钮/数据源），stroke=url(#uiGrad) -->
  <symbol id="i-grid" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><rect x="3" y="3" width="7" height="7" rx="1.6"/><rect x="14" y="3" width="7" height="7" rx="1.6"/><rect x="3" y="14" width="7" height="7" rx="1.6"/><rect x="14" y="14" width="7" height="7" rx="1.6"/></symbol>
  <symbol id="i-sliders" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><line x1="4" y1="8" x2="20" y2="8"/><circle cx="9" cy="8" r="2.4"/><line x1="4" y1="16" x2="20" y2="16"/><circle cx="15" cy="16" r="2.4"/></symbol>
  <symbol id="i-globe" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><circle cx="12" cy="12" r="9"/><path d="M3 12h18"/><path d="M12 3a14 14 0 0 1 0 18 14 14 0 0 1 0-18z"/></symbol>
  <symbol id="i-gear" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><circle cx="12" cy="12" r="3"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3M4.9 4.9l2.1 2.1M17 17l2.1 2.1M19.1 4.9 17 7M7 17l-2.1 2.1"/></symbol>
  <symbol id="i-doc" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M14 3H7a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h10a2 2 0 0 0 2-2V8z"/><path d="M14 3v5h5"/><path d="M9 13h6M9 17h4"/></symbol>
  <symbol id="i-layers" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M12 3 3 8l9 5 9-5z"/><path d="M3 13l9 5 9-5"/></symbol>
  <symbol id="i-compass" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><circle cx="12" cy="12" r="9"/><polygon points="15.5 8.5 11 11 8.5 15.5 13 13"/></symbol>
  <symbol id="i-zap" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><polygon points="13 2 4 14 11 14 11 22 20 10 13 10 13 2"/></symbol>
  <symbol id="i-bot" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><rect x="4" y="8" width="16" height="12" rx="2.5"/><path d="M12 8V4M9 4h6"/><circle cx="9.5" cy="14" r="1.2" fill="url(#uiGrad)"/><circle cx="14.5" cy="14" r="1.2" fill="url(#uiGrad)"/><path d="M9 18h6"/></symbol>
  <symbol id="i-mouse" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><rect x="7" y="2.5" width="10" height="19" rx="5"/><path d="M12 6v4"/></symbol>
  <symbol id="i-refresh" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M21 12a9 9 0 1 1-3-6.7"/><polyline points="21 3 21 8 16 8"/></symbol>
  <symbol id="i-wind" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M3 8h11a3 3 0 1 0-3-3"/><path d="M3 12h16a3 3 0 1 1-3 3"/><path d="M3 16h8a2.5 2.5 0 1 1-2.5 2.5"/></symbol>
  <symbol id="i-rainbow" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M3 18a9 9 0 0 1 18 0"/><path d="M6.5 18a5.5 5.5 0 0 1 11 0"/><path d="M10 18a2 2 0 0 1 4 0"/></symbol>
  <symbol id="i-trend" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><polyline points="3 17 9 11 13 15 21 7"/><polyline points="15 7 21 7 21 13"/></symbol>
  <symbol id="i-wave" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M2 8c2 0 2 2 4 2s2-2 4-2 2 2 4 2 2-2 4-2 2 2 4 2"/><path d="M2 14c2 0 2 2 4 2s2-2 4-2 2 2 4 2 2-2 4-2 2 2 4 2"/></symbol>
  <symbol id="i-bar" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M4 20h16"/><rect x="6" y="11" width="3" height="9" rx="1"/><rect x="11" y="6" width="3" height="14" rx="1"/><rect x="16" y="14" width="3" height="6" rx="1"/></symbol>
  <symbol id="i-target" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><circle cx="12" cy="12" r="9"/><circle cx="12" cy="12" r="5"/><circle cx="12" cy="12" r="1.6" fill="url(#uiGrad)"/></symbol>
  <symbol id="i-sparkle" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M12 3l2 6 6 2-6 2-2 6-2-6-6-2 6-2z"/></symbol>
  <symbol id="i-moon" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M21 12.8A8.5 8.5 0 1 1 11.2 3 6.6 6.6 0 0 0 21 12.8z"/></symbol>
  <symbol id="i-sun" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><circle cx="12" cy="12" r="4"/><path d="M12 2v2M12 20v2M2 12h2M20 12h2M4.9 4.9l1.4 1.4M17.7 17.7l1.4 1.4M19.1 4.9l-1.4 1.4M6.3 17.7l-1.4 1.4"/></symbol>
  <symbol id="i-alert" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M12 3 2 20h20z"/><path d="M12 9v5M12 17h.01"/></symbol>
  <!-- 白色图标（currentColor）：放在渐变底色方块上的品牌/流程/特性图标 -->
  <symbol id="w-glass" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="5" width="18" height="14" rx="3"/><path d="M3 10h18"/><circle cx="7" cy="7.5" r=".6" fill="currentColor"/></symbol>
  <symbol id="w-sparkle" viewBox="0 0 24 24" fill="currentColor" stroke="none"><path d="M12 2l2.2 6.8L21 11l-6.8 2.2L12 20l-2.2-6.8L3 11l6.8-2.2z"/></symbol>
  <symbol id="w-glow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="4"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3"/></symbol>
  <symbol id="w-layers" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 3 3 8l9 5 9-5z"/><path d="M3 13l9 5 9-5"/></symbol>
  <symbol id="w-fish" viewBox="0 0 24 24" fill="currentColor" stroke="none"><path d="M2 12c2.5-4 8-6 13-6 1.8 0 3.5.6 5 1.6L22 8v8l-2-1.6c-1.5 1-3.2 1.6-5 1.6-5 0-10.5-2-13-6z"/><circle cx="14" cy="11" r="1" fill="#1a1030"/></symbol>
</svg>
```

#### 2. 配套 CSS

```css
.ic-svg{display:inline-block;vertical-align:middle;flex-shrink:0;stroke-linecap:round;stroke-linejoin:round;fill:none}
.card-icon svg{width:26px;height:26px;color:#fff}     /* 卡图标：白图标 + 渐变底方块 */
.feature-icon svg{width:24px;height:24px;color:#fff}  /* 特性图标：白图标 + 渐变底方块 */
.side-item .ic-svg{width:18px;height:18px}            /* 侧栏导航：渐变描边 */
.stat-label .ic-svg{width:16px;height:16px}
```

（`.card-icon` / `.feature-icon` 沿用 Radium 的渐变背景方块 + hover 放大旋转；图标本身改用白色 SVG 保证对比度。）

#### 3. 用法

```html
<!-- 渐变描边图标（放在透明/玻璃背景上） -->
<svg class="ic-svg"><use href="#i-globe"/></svg>
<!-- 白色图标（放在 .card-icon / .feature-icon 这类渐变底方块里） -->
<div class="card-icon"><svg><use href="#w-sparkle"/></svg></div>
```

#### 图标规则（改造要点）
- **UI 图标（导航 / 卡 / 按钮 / 数据源）**：`stroke="url(#uiGrad)"` 三色渐变描边，细线 `stroke-width="2"`，Lucide / Feather 风格（克制几何）。
- **放在渐变底色方块上的图标（卡 / 特性 / 品牌 Logo）**：白色 `fill/stroke="currentColor"`，容器 `color:#fff` + 渐变背景，保证对比度。
- **命名**：渐变版 `i-xxx`、白版 `w-xxx`；新增图标沿用 `24×24` viewBox、`2px` 描边、简洁几何。
- ⚠️ 切换主题 / 重渲染的 JS **绝不能用 `el.textContent = …`** 覆盖图标节点（会把 SVG 变文字或空白）；改图标用 `innerHTML` 或直接操作 `<use>` 的 `href`。
- ⚠️ 渐变描边图标**必须有 `<linearGradient id="uiGrad">` 定义**，否则所有描边渲染成黑色。
- 校验：上线前 `grep` 全文件确认无 emoji 残留，且每个 `<use href="#x">` 都能在 sprite 里找到 `<symbol id="x">`。

### 图表
- 使用 ECharts
- 渐变填充
- 发光数据点
- 背景透明适配

---

## 🌈 完整CSS变量系统

### 暗色模式变量

```css
:root {
    --radium-bg-dark: #0a0e1a;
    --radium-bg-card: rgba(20, 28, 48, 0.6);
    --radium-bg-glass: rgba(255, 255, 255, 0.06);
    --radium-border: rgba(255, 255, 255, 0.1);
    --radium-border-glow: rgba(0, 212, 255, 0.3);
    --radium-text-primary: #ffffff;
    --radium-text-secondary: rgba(255, 255, 255, 0.6);
    --radium-text-muted: rgba(255, 255, 255, 0.4);
    --radium-cyan: #00d4ff;
    --radium-pink: #ff6b9d;
    --radium-purple: #a855f7;
    --radium-blue: #3b82f6;
    --radium-green: #10b981;
    --radium-yellow: #fbbf24;
    --radium-orange: #f97316;
    --radium-red: #ef4444;
    --radium-gradient-1: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
    --radium-gradient-2: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    --radium-gradient-3: linear-gradient(135deg, #0f1525 0%, #1a1f3a 50%, #0f1525 100%);
    --radium-glow-cyan: 0 0 30px rgba(0, 212, 255, 0.3);
    --radium-glow-pink: 0 0 30px rgba(255, 107, 157, 0.3);
    --radium-glow-purple: 0 0 30px rgba(168, 85, 247, 0.3);
    --radium-easing: cubic-bezier(0.25, 0.46, 0.45, 0.94);
}
```

### 浅色模式变量

```css
:root {
    --radium-bg-light: #F7F5F5;
    --radium-bg-card-light: rgba(255, 255, 255, 0.8);
    --radium-bg-glass-light: rgba(255, 255, 255, 0.6);
    --radium-border-light: rgba(0, 0, 0, 0.08);
    --radium-border-glow-light: rgba(0, 195, 243, 0.2);
    --radium-text-primary-light: #414546;
    --radium-text-secondary-light: rgba(0, 0, 0, 0.6);
    --radium-text-muted-light: rgba(0, 0, 0, 0.4);
    --radium-cyan-light: #00C3F3;
    --radium-teal-light: #A5CCD4;
    --radium-purple-light: #BFBADE;
    --radium-gold: #DBB360;
    --radium-gold-dark: #CA983B;
    --radium-gray-light: #A8A19F;
    --radium-blue-light: #02AFE9;
    --radium-gradient-light-1: linear-gradient(135deg, #00C3F3 0%, #A5CCD4 50%, #BFBADE 100%);
    --radium-gradient-light-2: linear-gradient(135deg, #DBB360 0%, #CA983B 100%);
    --radium-gradient-light-3: linear-gradient(135deg, #F7F5F5 0%, #F1F1F1 50%, #F7F5F5 100%);
    --radium-glow-cyan-light: 0 0 20px rgba(0, 195, 243, 0.2);
    --radium-glow-gold-light: 0 0 20px rgba(219, 179, 96, 0.3);
}
```

---

## 🌓 明暗模式切换实现

```css
body {
    transition: all 0.3s ease;
}

body.dark-mode {
    background: var(--radium-bg-dark);
    color: var(--radium-text-primary);
}

body.light-mode {
    background: var(--radium-bg-light);
    color: var(--radium-text-primary-light);
}

body.light-mode .glass-card {
    background: var(--radium-bg-glass-light);
    border-color: var(--radium-border-light);
}

body.light-mode .glow-effect {
    box-shadow: var(--radium-glow-cyan-light);
}
```

```javascript
function toggleTheme() {
    document.body.classList.toggle('dark-mode');
    document.body.classList.toggle('light-mode');
    localStorage.setItem('radium-theme', document.body.classList.contains('light-mode') ? 'light' : 'dark');
}

function initTheme() {
    const saved = localStorage.getItem('radium-theme');
    const prefersLight = window.matchMedia('(prefers-color-scheme: light)').matches;
    const theme = saved || (prefersLight ? 'light' : 'dark');
    document.body.classList.add(`${theme}-mode`);
}
```

---

## 📊 ECharts图表配置要点

### 暗色模式配置

```javascript
option = {
    backgroundColor: 'transparent',
    textStyle: { color: 'rgba(255,255,255,0.8)' },
    xAxis: {
        axisLine: { lineStyle: { color: 'rgba(255,255,255,0.2)' } },
        axisLabel: { color: 'rgba(255,255,255,0.6)' }
    },
    yAxis: {
        axisLine: { lineStyle: { color: 'rgba(255,255,255,0.2)' } },
        axisLabel: { color: 'rgba(255,255,255,0.6)' },
        splitLine: { lineStyle: { color: 'rgba(255,255,255,0.1)' } }
    },
    series: [{
        areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                { offset: 0, color: 'rgba(0, 212, 255, 0.4)' },
                { offset: 1, color: 'rgba(0, 212, 255, 0.05)' }
            ])
        }
    }]
};
```

### 浅色模式配置

```javascript
option = {
    backgroundColor: 'transparent',
    textStyle: { color: '#414546' },
    xAxis: {
        axisLine: { lineStyle: { color: 'rgba(0,0,0,0.1)' } },
        axisLabel: { color: 'rgba(0,0,0,0.6)' }
    },
    yAxis: {
        axisLine: { lineStyle: { color: 'rgba(0,0,0,0.1)' } },
        axisLabel: { color: 'rgba(0,0,0,0.6)' },
        splitLine: { lineStyle: { color: 'rgba(0,0,0,0.05)' } }
    },
    series: [{
        areaStyle: {
            color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
                { offset: 0, color: 'rgba(0, 195, 243, 0.3)' },
                { offset: 1, color: 'rgba(0, 195, 243, 0.03)' }
            ])
        }
    }]
};
```

---

## 📱 响应式设计要点

- 移动端隐藏侧边栏，使用抽屉式菜单
- 卡片网格改为单列布局
- 表格横向滚动
- 字体大小适当缩小
- 自定义光标在移动端自动禁用，使用系统光标

---

## 🔗 项目结构推荐

```
project/
├── index.html
├── css/
│   └── radium-style.css
├── js/
│   ├── app.js
│   └── data/
│       └── data.json
└── assets/
    ├── images/
    │   ├── backgrounds/    # AI生成的背景图
    │   ├── devices/        # AI生成的设备图
    │   └── concepts/       # AI生成的概念图
    ├── videos/             # AI生成的视频
    └── icons/
```

---

## 🎨 完整示例页面

以下是一个完整的Radium风格展示页面，包含所有交互效果：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Radium Design Style</title>
    <style>
        :root {
            --radium-bg-dark: #0a0e1a;
            --radium-bg-light: #F7F5F5;
            --radium-cyan: #00d4ff;
            --radium-pink: #ff6b9d;
            --radium-purple: #a855f7;
            --radium-gold: #DBB360;
            --radium-gradient: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
            --radium-easing: cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', sans-serif;
            min-height: 100vh;
            transition: all 0.5s ease;
            overflow-x: hidden;
            cursor: none;
        }

        body.dark { background: var(--radium-bg-dark); color: #ffffff; }
        body.light { background: var(--radium-bg-light); color: #414546; }

        body::before {
            content: '';
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background-image: 
                radial-gradient(circle at 20% 80%, rgba(0, 212, 255, 0.08) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(168, 85, 247, 0.08) 0%, transparent 50%),
                radial-gradient(circle at 50% 50%, rgba(255, 107, 157, 0.03) 0%, transparent 70%);
            pointer-events: none;
            z-index: 0;
        }

        body::after {
            content: '';
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            background-image: 
                linear-gradient(rgba(0, 212, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 212, 255, 0.03) 1px, transparent 1px);
            background-size: 60px 60px;
            pointer-events: none;
            z-index: 0;
        }

        .custom-cursor {
            position: fixed;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: var(--radium-gradient);
            pointer-events: none;
            z-index: 9999;
            mix-blend-mode: screen;
            box-shadow: 0 0 20px var(--radium-cyan), 0 0 40px var(--radium-purple);
            transform: translate(-50%, -50%);
            transition: width 0.3s ease, height 0.3s ease;
        }

        .cursor-glow {
            position: fixed;
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(0, 212, 255, 0.3) 0%, transparent 70%);
            pointer-events: none;
            z-index: 9998;
            transform: translate(-50%, -50%);
            transition: all 0.1s ease;
        }

        .particle {
            position: fixed;
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background: var(--radium-cyan);
            pointer-events: none;
            z-index: 9997;
            opacity: 0.8;
        }

        .container {
            position: relative;
            z-index: 1;
            max-width: 1200px;
            margin: 0 auto;
            padding: 80px 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 80px;
            padding-top: 40px;
        }

        .title {
            font-size: 56px;
            font-weight: 700;
            background: var(--radium-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 20px;
            animation: fadeInDown 0.8s var(--radium-easing);
            letter-spacing: -2px;
        }

        .subtitle {
            font-size: 20px;
            opacity: 0.6;
            animation: fadeInDown 0.8s var(--radium-easing) 0.2s both;
        }

        .theme-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 12px 24px;
            border-radius: 30px;
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            cursor: none;
            font-size: 14px;
            transition: all 0.3s ease;
            z-index: 100;
            backdrop-filter: blur(10px);
        }

        .theme-toggle:hover {
            transform: scale(1.05);
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.3);
            background: rgba(255,255,255,0.15);
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 32px;
            margin-bottom: 80px;
        }

        .glass-card {
            background: rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.12);
            border-radius: 24px;
            padding: 40px 32px;
            transition: all 0.4s var(--radium-easing);
            animation: fadeInUp 0.8s var(--radium-easing) backwards;
            position: relative;
            overflow: hidden;
        }

        .light .glass-card {
            background: rgba(255, 255, 255, 0.7);
            border-color: rgba(0, 0, 0, 0.06);
        }

        .glass-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 4px;
            background: var(--radium-gradient);
            opacity: 0;
            transform: scaleX(0);
            transition: all 0.4s ease;
        }

        .glass-card:hover::before {
            opacity: 1;
            transform: scaleX(1);
        }

        .glass-card:hover {
            transform: translateY(-12px) rotateX(2deg);
            border-color: rgba(0, 212, 255, 0.4);
            box-shadow: 
                0 25px 50px rgba(0, 0, 0, 0.2),
                0 0 40px rgba(0, 212, 255, 0.15),
                0 0 80px rgba(168, 85, 247, 0.1),
                inset 0 1px 0 rgba(255, 255, 255, 0.1);
        }

        .card-icon {
            width: 70px;
            height: 70px;
            border-radius: 20px;
            background: var(--radium-gradient);
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            margin-bottom: 24px;
            transition: transform 0.4s var(--radium-easing);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
        }
        .card-icon svg { width: 32px; height: 32px; stroke-linecap: round; stroke-linejoin: round; }

        .glass-card:hover .card-icon {
            transform: scale(1.15) rotate(5deg);
        }

        .card-title {
            font-size: 24px;
            font-weight: 700;
            margin-bottom: 16px;
            position: relative;
        }

        .card-title::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 40px;
            height: 3px;
            background: var(--radium-gradient);
            opacity: 0;
            transform: scaleX(0);
            transition: all 0.4s ease;
        }

        .glass-card:hover .card-title::after {
            opacity: 1;
            transform: scaleX(1);
        }

        .card-desc {
            font-size: 15px;
            opacity: 0.5;
            line-height: 1.8;
            transition: opacity 0.4s ease;
        }

        .glass-card:hover .card-desc {
            opacity: 0.8;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 24px;
            margin-bottom: 80px;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.12);
            border-radius: 20px;
            padding: 32px;
            text-align: center;
            animation: fadeInUp 0.8s var(--radium-easing) backwards;
            transition: all 0.4s var(--radium-easing);
        }

        .light .stat-card {
            background: rgba(255, 255, 255, 0.7);
            border-color: rgba(0, 0, 0, 0.06);
        }

        .stat-card:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
            border-color: rgba(0, 212, 255, 0.3);
        }

        .stat-value {
            font-size: 42px;
            font-weight: 800;
            background: var(--radium-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 12px;
            transition: transform 0.4s ease;
        }

        .stat-card:hover .stat-value {
            transform: scale(1.1);
        }

        .stat-label {
            font-size: 15px;
            opacity: 0.5;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .gradient-showcase {
            background: rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.12);
            border-radius: 24px;
            padding: 50px;
            margin-bottom: 80px;
            animation: fadeInUp 0.8s var(--radium-easing) backwards;
        }

        .light .gradient-showcase {
            background: rgba(255, 255, 255, 0.7);
            border-color: rgba(0, 0, 0, 0.06);
        }

        .showcase-title {
            font-size: 28px;
            margin-bottom: 40px;
            text-align: center;
            font-weight: 600;
        }

        .gradient-preview {
            display: flex;
            justify-content: center;
            gap: 24px;
            flex-wrap: wrap;
        }

        .gradient-item {
            width: 140px;
            height: 140px;
            border-radius: 20px;
            transition: all 0.4s var(--radium-easing);
            cursor: none;
            position: relative;
            overflow: hidden;
        }

        .gradient-item::after {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.6s ease;
        }

        .gradient-item:hover::after {
            left: 100%;
        }

        .gradient-item:hover {
            transform: scale(1.15) rotate(5deg);
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
        }

        .grad-1 { background: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%); }
        .grad-2 { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
        .grad-3 { background: linear-gradient(135deg, #00C3F3 0%, #A5CCD4 50%, #BFBADE 100%); }
        .grad-4 { background: linear-gradient(135deg, #DBB360 0%, #CA983B 100%); }
        .grad-5 { background: linear-gradient(135deg, #00d4ff 0%, #10b981 100%); }
        .grad-6 { background: linear-gradient(135deg, #ff6b9d 0%, #a855f7 100%); }

        .buttons-showcase {
            display: flex;
            justify-content: center;
            gap: 28px;
            flex-wrap: wrap;
            margin-bottom: 80px;
        }

        .btn {
            padding: 16px 40px;
            border-radius: 16px;
            font-size: 18px;
            font-weight: 700;
            cursor: none;
            transition: all 0.4s var(--radium-easing);
            border: none;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(255,255,255,0.3) 50%, transparent 70%);
            transform: translateX(-100%);
            transition: transform 0.6s ease;
        }

        .btn:hover::before {
            transform: translateX(100%);
        }

        .btn-primary {
            background: var(--radium-gradient);
            color: white;
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-4px) scale(1.05);
            box-shadow: 0 20px 50px rgba(0, 212, 255, 0.4), 0 0 30px rgba(168, 85, 247, 0.3);
        }

        .btn-secondary {
            background: transparent;
            border: 2px solid rgba(0, 212, 255, 0.5);
            color: var(--radium-cyan);
        }

        .light .btn-secondary {
            color: #00C3F3;
            border-color: rgba(0, 195, 243, 0.5);
        }

        .btn-secondary:hover {
            background: rgba(0, 212, 255, 0.1);
            border-color: var(--radium-cyan);
            transform: translateY(-4px);
            box-shadow: 0 0 30px rgba(0, 212, 255, 0.2);
        }

        .btn-gold {
            background: linear-gradient(135deg, #DBB360 0%, #CA983B 100%);
            color: #3B3B3C;
            box-shadow: 0 10px 30px rgba(219, 179, 96, 0.3);
        }

        .btn-gold:hover {
            transform: translateY(-4px) scale(1.05);
            box-shadow: 0 20px 50px rgba(219, 179, 96, 0.4);
        }

        .features-section {
            margin-bottom: 80px;
        }

        .feature-item {
            display: flex;
            align-items: center;
            gap: 24px;
            padding: 32px;
            background: rgba(255, 255, 255, 0.04);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            margin-bottom: 20px;
            transition: all 0.4s var(--radium-easing);
            border: 1px solid transparent;
        }

        .light .feature-item {
            background: rgba(255, 255, 255, 0.5);
        }

        .feature-item:hover {
            transform: translateX(12px);
            border-color: rgba(0, 212, 255, 0.3);
            background: rgba(255, 255, 255, 0.08);
        }

        .feature-icon {
            width: 50px;
            height: 50px;
            border-radius: 14px;
            background: var(--radium-gradient);
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            flex-shrink: 0;
            transition: transform 0.4s ease;
        }
        .feature-icon svg { width: 24px; height: 24px; stroke-linecap: round; stroke-linejoin: round; }

        .feature-item:hover .feature-icon {
            transform: scale(1.2) rotate(10deg);
        }

        .feature-info h3 {
            font-size: 18px;
            margin-bottom: 8px;
        }

        .feature-info p {
            font-size: 14px;
            opacity: 0.5;
        }

        .footer {
            text-align: center;
            opacity: 0.4;
            font-size: 14px;
            padding: 40px 0;
        }

        @keyframes fadeInDown {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .glass-card:nth-child(1) { animation-delay: 0.1s; }
        .glass-card:nth-child(2) { animation-delay: 0.2s; }
        .glass-card:nth-child(3) { animation-delay: 0.3s; }
        .glass-card:nth-child(4) { animation-delay: 0.4s; }
        .stat-card:nth-child(1) { animation-delay: 0.2s; }
        .stat-card:nth-child(2) { animation-delay: 0.3s; }
        .stat-card:nth-child(3) { animation-delay: 0.4s; }
        .stat-card:nth-child(4) { animation-delay: 0.5s; }

        @media (max-width: 768px) {
            .title { font-size: 36px; }
            .subtitle { font-size: 16px; }
            .cards-grid { grid-template-columns: 1fr; gap: 20px; }
            .stats-grid { grid-template-columns: repeat(2, 1fr); }
            .gradient-item { width: 100px; height: 100px; }
            .custom-cursor, .cursor-glow { display: none; }
            body { cursor: auto; }
            .btn { cursor: pointer; }
            .theme-toggle { cursor: pointer; }
        }

        .scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            height: 4px;
            background: var(--radium-gradient);
            z-index: 9999;
            transition: width 0.1s ease;
            box-shadow: 0 0 20px var(--radium-cyan);
        }

        .radium-input-group {
            position: relative;
            margin-bottom: 24px;
        }

        .radium-input {
            width: 100%;
            padding: 16px 20px;
            font-size: 16px;
            background: rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.12);
            border-radius: 16px;
            color: inherit;
            transition: all 0.4s var(--radium-easing);
            outline: none;
        }

        .radium-input:focus {
            border-color: rgba(0, 212, 255, 0.5);
            box-shadow: 0 0 20px rgba(0, 212, 255, 0.2), inset 0 1px 0 rgba(255, 255, 255, 0.1);
        }

        .radium-input-label {
            position: absolute;
            top: 50%;
            left: 20px;
            transform: translateY(-50%);
            font-size: 16px;
            color: rgba(255, 255, 255, 0.5);
            pointer-events: none;
            transition: all 0.3s var(--radium-easing);
        }

        .radium-input:focus + .radium-input-label,
        .radium-input:not(:placeholder-shown) + .radium-input-label {
            top: -10px;
            left: 16px;
            font-size: 12px;
            color: var(--radium-cyan);
            padding: 0 8px;
            background: var(--radium-bg-dark);
        }

        .light .radium-input {
            background: rgba(255, 255, 255, 0.7);
            border-color: rgba(0, 0, 0, 0.08);
        }

        .light .radium-input:focus + .radium-input-label,
        .light .radium-input:not(:placeholder-shown) + .radium-input-label {
            background: var(--radium-bg-light);
            color: #00C3F3;
        }

        .ripple-container { position: relative; overflow: hidden; }
        .ripple {
            position: absolute;
            border-radius: 50%;
            background: rgba(0, 212, 255, 0.3);
            transform: scale(0);
            animation: ripple-animation 0.6s linear;
            pointer-events: none;
        }

        @keyframes ripple-animation {
            to { transform: scale(4); opacity: 0; }
        }

        .counter { font-variant-numeric: tabular-nums; }

        .modal-overlay {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(10px);
            display: flex; align-items: center; justify-content: center;
            opacity: 0; visibility: hidden;
            transition: all 0.4s var(--radium-easing);
            z-index: 1000;
        }

        .modal-overlay.active { opacity: 1; visibility: visible; }

        .modal-content {
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 24px;
            padding: 40px;
            max-width: 500px;
            width: 90%;
            transform: scale(0.9) translateY(20px);
            transition: all 0.4s var(--radium-easing);
        }

        .modal-overlay.active .modal-content { transform: scale(1) translateY(0); }

        .tabs-container {
            display: flex; gap: 8px;
            background: rgba(255, 255, 255, 0.04);
            backdrop-filter: blur(10px);
            padding: 8px; border-radius: 16px;
            margin-bottom: 24px;
        }

        .tab {
            padding: 12px 28px; border-radius: 12px;
            cursor: none; transition: all 0.3s var(--radium-easing);
            font-weight: 600; font-size: 14px;
        }

        .tab.active {
            background: var(--radium-gradient);
            color: white;
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.3);
        }

        .tab-content { display: none; }
        .tab-content.active { display: block; }

        .progress-bar-container {
            height: 8px; background: rgba(255, 255, 255, 0.1);
            border-radius: 4px; overflow: hidden; margin-bottom: 8px;
        }

        .progress-bar {
            height: 100%; background: var(--radium-gradient);
            border-radius: 4px; transition: width 1s var(--radium-easing);
            box-shadow: 0 0 20px var(--radium-cyan);
            position: relative; overflow: hidden;
        }

        .progress-bar::after {
            content: ''; position: absolute; top: 0; left: -100%;
            width: 100%; height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            animation: progress-shine 2s infinite;
        }

        @keyframes progress-shine { 100% { left: 100%; } }

        .progress-label {
            display: flex; justify-content: space-between;
            font-size: 14px; opacity: 0.6;
        }

        .skeleton {
            background: linear-gradient(90deg, rgba(255,255,255,0.05) 25%, rgba(255,255,255,0.1) 50%, rgba(255,255,255,0.05) 75%);
            background-size: 200% 100%;
            animation: skeleton-loading 1.5s infinite;
            border-radius: 12px;
        }

        @keyframes skeleton-loading {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }

        .skeleton-row { height: 20px; margin-bottom: 12px; }
        .skeleton-row.short { width: 60%; }
        .skeleton-row.medium { width: 80%; }
        .skeleton-row.full { width: 100%; }

        .dropdown { position: relative; display: inline-block; }
        .dropdown-menu {
            position: absolute; top: calc(100% + 12px); left: 0;
            min-width: 200px;
            background: rgba(255, 255, 255, 0.08);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.15);
            border-radius: 16px;
            padding: 8px 0;
            opacity: 0; visibility: hidden;
            transform: translateY(-10px);
            transition: all 0.3s var(--radium-easing);
            z-index: 100;
        }

        .dropdown:hover .dropdown-menu {
            opacity: 1; visibility: visible; transform: translateY(0);
        }

        .dropdown-item {
            padding: 12px 20px; cursor: none;
            transition: all 0.2s ease; font-size: 14px;
        }

        .dropdown-item:hover {
            background: rgba(0, 212, 255, 0.1);
            padding-left: 24px;
        }

        .light .dropdown-menu { background: rgba(255, 255, 255, 0.95); border-color: rgba(0, 0, 0, 0.08); }
        .light .dropdown-item:hover { background: rgba(0, 195, 243, 0.1); }

        .chart-container {
            background: rgba(255, 255, 255, 0.04);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.12);
            border-radius: 24px;
            padding: 32px;
            height: 350px;
        }

        .light .chart-container {
            background: rgba(255, 255, 255, 0.7);
            border-color: rgba(0, 0, 0, 0.06);
        }
    </style>
</head>
<body class="dark">
    <!-- SVG 图标 sprite（改造版：全站图标复用，绝不用 emoji） -->
    <svg width="0" height="0" style="position:absolute" aria-hidden="true"><defs>
      <linearGradient id="uiGrad" x1="0" y1="0" x2="1" y2="1"><stop offset="0" stop-color="#00d4ff"/><stop offset=".5" stop-color="#a855f7"/><stop offset="1" stop-color="#ff6b9d"/></linearGradient></defs>
      <symbol id="i-moon" viewBox="0 0 24 24" fill="none" stroke="url(#uiGrad)" stroke-width="2"><path d="M21 12.8A8.5 8.5 0 1 1 11.2 3 6.6 6.6 0 0 0 21 12.8z"/></symbol>
      <symbol id="w-glass" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="5" width="18" height="14" rx="3"/><path d="M3 10h18"/></symbol>
      <symbol id="w-sparkle" viewBox="0 0 24 24" fill="currentColor" stroke="none"><path d="M12 2l2.2 6.8L21 11l-6.8 2.2L12 20l-2.2-6.8L3 11l6.8-2.2z"/></symbol>
      <symbol id="w-glow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="4"/><path d="M12 2v3M12 19v3M2 12h3M19 12h3"/></symbol>
      <symbol id="w-globe" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="9"/><path d="M3 12h18"/><path d="M12 3a14 14 0 0 1 0 18 14 14 0 0 1 0-18z"/></symbol>
      <symbol id="w-mouse" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="7" y="2.5" width="10" height="19" rx="5"/><path d="M12 6v4"/></symbol>
      <symbol id="w-refresh" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 12a9 9 0 1 1-3-6.7"/><polyline points="21 3 21 8 16 8"/></symbol>
      <symbol id="w-wind" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 8h11a3 3 0 1 0-3-3"/><path d="M3 12h16a3 3 0 1 1-3 3"/><path d="M3 16h8a2.5 2.5 0 1 1-2.5 2.5"/></symbol>
      <symbol id="w-rainbow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M3 18a9 9 0 0 1 18 0"/><path d="M6.5 18a5.5 5.5 0 0 1 11 0"/><path d="M10 18a2 2 0 0 1 4 0"/></symbol>
      <symbol id="w-trend" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 17 9 11 13 15 21 7"/><polyline points="15 7 21 7 21 13"/></symbol>
      <symbol id="w-wave" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M2 8c2 0 2 2 4 2s2-2 4-2 2 2 4 2 2-2 4-2 2 2 4 2"/><path d="M2 14c2 0 2 2 4 2s2-2 4-2 2 2 4 2 2-2 4-2 2 2 4 2"/></symbol>
      <symbol id="w-bar" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 20h16"/><rect x="6" y="11" width="3" height="9" rx="1"/><rect x="11" y="6" width="3" height="14" rx="1"/><rect x="16" y="14" width="3" height="6" rx="1"/></symbol>
      <symbol id="w-target" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="9"/><circle cx="12" cy="12" r="5"/><circle cx="12" cy="12" r="1.6" fill="currentColor"/></symbol>
    </svg>
    <div class="scroll-progress" id="scrollProgress"></div>
    <div class="custom-cursor" id="cursor"></div>
    <div class="cursor-glow" id="cursorGlow"></div>
    <button class="theme-toggle" onclick="toggleTheme()"><svg class="ic-svg" style="width:16px;height:16px;vertical-align:-3px"><use href="#i-moon"/></svg> 切换主题</button>

    <div class="container">
        <div class="header">
            <h1 class="title">Radium Design Style</h1>
            <p class="subtitle">基于 Cosmin Capitanu 的未来感设计风格系统 - 包含18种交互效果</p>
        </div>

        <div class="stats-grid">
            <div class="stat-card"><div class="stat-value counter" id="counter1">0</div><div class="stat-label">在售商品</div></div>
            <div class="stat-card"><div class="stat-value counter" id="counter2">0</div><div class="stat-label">总销售额</div></div>
            <div class="stat-card"><div class="stat-value counter" id="counter3">0</div><div class="stat-label">订单总数</div></div>
            <div class="stat-card"><div class="stat-value">+18.5%</div><div class="stat-label">环比增长</div></div>
        </div>

        <div class="cards-grid">
            <div class="glass-card"><div class="card-icon"><svg><use href="#w-glass"/></svg></div><h3 class="card-title">玻璃拟态</h3><p class="card-desc">半透明背景配合模糊效果，使用 backdrop-filter 实现毛玻璃质感。</p></div>
            <div class="glass-card"><div class="card-icon"><svg><use href="#w-sparkle"/></svg></div><h3 class="card-title">霓虹渐变</h3><p class="card-desc">主色调深邃蓝紫，强调色青色、粉色、紫色，渐变方向对角线、环形。</p></div>
            <div class="glass-card"><div class="card-icon"><svg><use href="#w-glow"/></svg></div><h3 class="card-title">光效阴影</h3><p class="card-desc">内发光效果增强立体感，柔和的外阴影营造漂浮感，辉光效果突出重点元素。</p></div>
            <div class="glass-card"><div class="card-icon"><svg><use href="#w-globe"/></svg></div><h3 class="card-title">空间层次</h3><p class="card-desc">Z轴深度通过阴影、透明度、缩放营造，视差效果增强沉浸感。</p></div>
        </div>

        <div class="gradient-showcase">
            <h2 class="showcase-title">渐变配色方案</h2>
            <div class="gradient-preview">
                <div class="gradient-item grad-1"></div>
                <div class="gradient-item grad-2"></div>
                <div class="gradient-item grad-3"></div>
                <div class="gradient-item grad-4"></div>
                <div class="gradient-item grad-5"></div>
                <div class="gradient-item grad-6"></div>
            </div>
        </div>

        <div class="buttons-showcase">
            <button class="btn btn-primary" onclick="openModal()">打开模态框</button>
            <button class="btn btn-secondary ripple-container">涟漪效果按钮</button>
            <button class="btn btn-gold">金色按钮</button>
        </div>

        <div class="gradient-showcase">
            <h2 class="showcase-title">输入框动效</h2>
            <div style="max-width: 400px; margin: 0 auto;">
                <div class="radium-input-group">
                    <input type="text" class="radium-input" placeholder=" " id="email">
                    <label class="radium-input-label" for="email">邮箱地址</label>
                </div>
                <div class="radium-input-group">
                    <input type="password" class="radium-input" placeholder=" " id="password">
                    <label class="radium-input-label" for="password">密码</label>
                </div>
            </div>
        </div>

        <div class="gradient-showcase">
            <h2 class="showcase-title">标签页切换</h2>
            <div class="tabs-container">
                <div class="tab active" data-content="tab1">销售数据</div>
                <div class="tab" data-content="tab2">用户分析</div>
                <div class="tab" data-content="tab3">趋势预测</div>
            </div>
            <div id="tab1" class="tab-content active">
                <p>销售数据内容：本月销售额达到 $1.28M，同比增长 18.5%。</p>
            </div>
            <div id="tab2" class="tab-content">
                <p>用户分析内容：活跃用户数 15.6K，新用户占比 35%。</p>
            </div>
            <div id="tab3" class="tab-content">
                <p>趋势预测内容：下月预计增长 22%，重点关注新品发布效果。</p>
            </div>
        </div>

        <div class="gradient-showcase">
            <h2 class="showcase-title">渐变进度条</h2>
            <div style="max-width: 600px; margin: 0 auto;">
                <div class="progress-label"><span>销售完成度</span><span>78%</span></div>
                <div class="progress-bar-container"><div class="progress-bar" style="width: 78%"></div></div>
                <div class="progress-label"><span>目标达成率</span><span>92%</span></div>
                <div class="progress-bar-container"><div class="progress-bar" style="width: 92%"></div></div>
                <div class="progress-label"><span>客户满意度</span><span>85%</span></div>
                <div class="progress-bar-container"><div class="progress-bar" style="width: 85%"></div></div>
            </div>
        </div>

        <div class="gradient-showcase">
            <h2 class="showcase-title">下拉菜单</h2>
            <div style="text-align: center;">
                <div class="dropdown">
                    <button class="btn btn-secondary">更多选项 ▼</button>
                    <div class="dropdown-menu">
                        <div class="dropdown-item">选项一</div>
                        <div class="dropdown-item">选项二</div>
                        <div class="dropdown-item">选项三</div>
                        <div class="dropdown-item">选项四</div>
                    </div>
                </div>
            </div>
        </div>

        <div class="gradient-showcase">
            <h2 class="showcase-title">骨架屏加载动画</h2>
            <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 24px;">
                <div class="skeleton-card">
                    <div class="skeleton skeleton-circle"></div>
                    <div class="skeleton skeleton-row short"></div>
                    <div class="skeleton skeleton-row medium"></div>
                    <div class="skeleton skeleton-row full"></div>
                </div>
                <div class="skeleton-card">
                    <div class="skeleton skeleton-circle"></div>
                    <div class="skeleton skeleton-row short"></div>
                    <div class="skeleton skeleton-row medium"></div>
                    <div class="skeleton skeleton-row full"></div>
                </div>
            </div>
        </div>

        <div class="gradient-showcase">
            <h2 class="showcase-title">核心交互效果</h2>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-mouse"/></svg></div><div class="feature-info"><h3>自定义发光光标</h3><p>霓虹渐变发光效果，带有追踪光晕和粒子拖尾</p></div></div>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-refresh"/></svg></div><div class="feature-info"><h3>卡片深度交互</h3><p>hover时上浮、旋转、边框光效、顶部渐变条展开</p></div></div>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-wind"/></svg></div><div class="feature-info"><h3>流体动画曲线</h3><p>使用 cubic-bezier 实现自然的弹性过渡效果</p></div></div>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-rainbow"/></svg></div><div class="feature-info"><h3>光效扫过动画</h3><p>按钮和渐变卡片上的光泽扫过效果</p></div></div>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-trend"/></svg></div><div class="feature-info"><h3>数字滚动动画</h3><p>页面加载时数字平滑滚动到目标值</p></div></div>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-wave"/></svg></div><div class="feature-info"><h3>涟漪点击效果</h3><p>点击按钮时产生扩散涟漪动画</p></div></div>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-bar"/></svg></div><div class="feature-info"><h3>标签页切换</h3><p>平滑切换不同内容区域</p></div></div>
            <div class="feature-item"><div class="feature-icon"><svg><use href="#w-target"/></svg></div><div class="feature-info"><h3>渐变进度条</h3><p>带光泽扫过效果的进度展示</p></div></div>
        </div>

        <div class="footer"><p>Radium Design Style - Cosmin Capitanu</p></div>
    </div>

    <div class="modal-overlay" id="modalOverlay">
        <div class="modal-content">
            <h3 style="margin-bottom: 16px;">玻璃拟态模态框</h3>
            <p style="opacity: 0.7; margin-bottom: 24px;">这是一个带有毛玻璃效果的模态框示例，点击下方按钮关闭。</p>
            <button class="btn btn-primary" onclick="closeModal()">关闭</button>
        </div>
    </div>

    <script>
        const cursor = document.getElementById('cursor');
        const cursorGlow = document.getElementById('cursorGlow');
        let particles = [];

        function moveCursor(e) {
            cursor.style.left = e.clientX + 'px';
            cursor.style.top = e.clientY + 'px';
            cursorGlow.style.left = e.clientX + 'px';
            cursorGlow.style.top = e.clientY + 'px';
            createParticle(e.clientX, e.clientY);
        }

        function createParticle(x, y) {
            if (particles.length > 20) { particles[0].remove(); particles.shift(); }
            const p = document.createElement('div');
            p.className = 'particle';
            p.style.left = x + 'px';
            p.style.top = y + 'px';
            document.body.appendChild(p);
            particles.push(p);
            let o = 0.8, s = 1;
            function animate() {
                o -= 0.02; s -= 0.03;
                p.style.opacity = o;
                p.style.transform = `translate(-50%, -50%) scale(${s})`;
                if (o > 0) requestAnimationFrame(animate);
                else { p.remove(); particles = particles.filter(item => item !== p); }
            }
            animate();
        }

        document.addEventListener('mousemove', moveCursor);

        document.querySelectorAll('.btn, .glass-card, .stat-card, .gradient-item, .feature-item, .theme-toggle, .tab').forEach(el => {
            el.addEventListener('mouseenter', () => {
                cursor.style.width = '40px'; cursor.style.height = '40px';
                cursorGlow.style.width = '150px'; cursorGlow.style.height = '150px';
            });
            el.addEventListener('mouseleave', () => {
                cursor.style.width = '20px'; cursor.style.height = '20px';
                cursorGlow.style.width = '100px'; cursorGlow.style.height = '100px';
            });
        });

        function toggleTheme() {
            document.body.classList.toggle('dark');
            document.body.classList.toggle('light');
        }

        function openModal() { document.getElementById('modalOverlay').classList.add('active'); }
        function closeModal() { document.getElementById('modalOverlay').classList.remove('active'); }

        document.querySelectorAll('.ripple-container').forEach(btn => {
            btn.addEventListener('click', (e) => {
                const circle = document.createElement('span');
                const d = Math.max(btn.clientWidth, btn.clientHeight);
                circle.style.width = circle.style.height = `${d}px`;
                circle.style.left = `${e.clientX - btn.getBoundingClientRect().left - d/2}px`;
                circle.style.top = `${e.clientY - btn.getBoundingClientRect().top - d/2}px`;
                circle.classList.add('ripple');
                btn.appendChild(circle);
                setTimeout(() => circle.remove(), 600);
            });
        });

        function animateNumber(el, target, duration = 2000) {
            const start = parseFloat(el.textContent.replace(/[^0-9.]/g, '')) || 0;
            const startTime = performance.now();
            function update(currentTime) {
                const elapsed = currentTime - startTime;
                const progress = Math.min(elapsed / duration, 1);
                const current = start + (target - start) * (1 - Math.pow(1 - progress, 4));
                el.textContent = Math.floor(current).toLocaleString();
                if (progress < 1) requestAnimationFrame(update);
            }
            requestAnimationFrame(update);
        }

        setTimeout(() => {
            animateNumber(document.getElementById('counter1'), 128);
            animateNumber(document.getElementById('counter2'), 1280000);
            animateNumber(document.getElementById('counter3'), 15600);
        }, 500);

        document.querySelectorAll('.tab').forEach(tab => {
            tab.addEventListener('click', () => {
                document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
                tab.classList.add('active');
                document.getElementById(tab.dataset.content).classList.add('active');
            });
        });

        function updateScrollProgress() {
            const scrollTop = window.scrollY;
            const docHeight = document.documentElement.scrollHeight - window.innerHeight;
            document.getElementById('scrollProgress').style.width = `${(scrollTop / docHeight) * 100}%`;
        }

        window.addEventListener('scroll', updateScrollProgress);
    </script>
</body>
</html>

---

## 🚀 部署指南

### 本地开发环境

#### Python HTTP Server（推荐）
```bash
cd project
python3 -m http.server 9292
```
访问：`http://localhost:9292/`

#### Node.js http-server
```bash
npm install -g http-server
cd project
http-server -p 9292 -c-1
```

#### Vite（推荐用于大型项目）
```bash
npm create vite@6.5.0 . -- --template vanilla
npm install
npm run dev -- --port 9292
```

### 构建优化

#### 使用 vite 构建生产版本
```bash
npm run build
```

构建后文件在 `dist/` 目录，可部署到任何静态服务器。

### 常用部署平台

#### GitHub Pages
1. 将代码推送到 GitHub 仓库
2. 进入仓库 Settings → Pages
3. Source 选择 `main` 分支的 `/` 或 `/dist` 目录
4. 等待部署完成，访问 `https://username.github.io/repo-name/`

#### Netlify
1. 连接 GitHub 仓库
2. Build command: `npm run build`
3. Publish directory: `dist`
4. 部署完成后获得临时域名

#### Vercel
1. 连接 GitHub 仓库
2. Framework Preset: `Vite`
3. 自动检测配置并部署

#### 自定义服务器（Nginx）
```nginx
server {
    listen 80;
    server_name your-domain.com;
    root /var/www/project/dist;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    # 启用 gzip 压缩
    gzip on;
    gzip_types text/css application/javascript image/svg+xml;
}
```

### 环境变量配置

在项目根目录创建 `.env` 文件（Vite项目）：
```env
VITE_APP_TITLE=Radium Dashboard
VITE_API_BASE_URL=https://api.example.com
```

在 JavaScript 中使用：
```javascript
const title = import.meta.env.VITE_APP_TITLE;
```

---

## ❓ 常见问题解答（FAQ）

### 1. 自定义光标在移动端不显示？
**原因**：移动端使用触摸操作，自定义光标会干扰用户体验。

**解决方案**：已在CSS中添加媒体查询，自动禁用移动端自定义光标：
```css
@media (max-width: 768px) {
    .custom-cursor, .cursor-glow { display: none; }
    body { cursor: auto; }
}
```

### 2. 玻璃拟态效果在Safari中不生效？
**原因**：Safari需要添加 `-webkit-backdrop-filter` 前缀。

**解决方案**：确保CSS中包含前缀：
```css
.glass-card {
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
}
```

### 3. 粒子效果过多导致性能问题？
**原因**：粒子数量没有限制，持续创建会导致DOM元素过多。

**解决方案**：已在代码中限制最大粒子数为20：
```javascript
if (particles.length > 20) {
    particles[0].remove();
    particles.shift();
}
```

### 4. ECharts图表在暗色模式下文字看不清？
**原因**：图表配置没有根据主题切换。

**解决方案**：使用 `updateChartsTheme()` 函数在主题切换时更新图表配置：
```javascript
function updateChartsTheme() {
    const charts = echarts.instances;
    charts.forEach(chart => {
        const isDark = currentTheme === 'dark';
        // 更新 tooltip、legend、axisLabel 等颜色配置
        chart.setOption({
            tooltip: {
                backgroundColor: isDark ? 'rgba(20, 28, 48, 0.9)' : 'rgba(255, 255, 255, 0.95)',
                textStyle: { color: isDark ? '#fff' : '#414546' }
            }
        });
    });
}
```

### 5. 页面加载时闪烁（FOUC）？
**原因**：主题样式在JavaScript执行前未生效。

**解决方案**：在 `<head>` 中添加内联CSS，确保页面加载时立即应用主题：
```html
<head>
    <script>
        const savedTheme = localStorage.getItem('radium-theme') || 'dark';
        document.documentElement.className = savedTheme;
    </script>
    <style>
        body { transition: background 0.3s ease, color 0.3s ease; }
        body.dark { background: #0a0e1a; color: #fff; }
        body.light { background: #F7F5F5; color: #414546; }
    </style>
</head>
```

### 6. 按钮点击无反应？
**原因**：自定义光标覆盖在按钮上方，阻止了点击事件。

**解决方案**：确保自定义光标添加 `pointer-events: none;`：
```css
.custom-cursor, .cursor-glow, .particle {
    pointer-events: none;
}
```

### 7. 渐变颜色在打印时显示异常？
**原因**：部分浏览器打印时不支持CSS渐变。

**解决方案**：添加打印样式：
```css
@media print {
    .btn-primary, .card-icon {
        background: #00d4ff !important;
        -webkit-print-color-adjust: exact;
        print-color-adjust: exact;
    }
}
```

### 8. 如何自定义主题颜色？
**解决方案**：修改CSS变量即可：
```css
:root {
    --radium-cyan: #00d4ff;
    --radium-pink: #ff6b9d;
    --radium-purple: #a855f7;
    --radium-gradient: linear-gradient(135deg, #00d4ff 0%, #a855f7 50%, #ff6b9d 100%);
}
```

### 9. 页面滚动时性能卡顿？
**原因**：`mousemove` 和 `scroll` 事件触发频繁，导致重绘过多。

**解决方案**：使用 `requestAnimationFrame` 和节流函数优化：
```javascript
let ticking = false;
function handleScroll() {
    if (!ticking) {
        window.requestAnimationFrame(() => {
            updateScrollProgress();
            ticking = false;
        });
        ticking = true;
    }
}
window.addEventListener('scroll', handleScroll);
```

### 10. 如何支持多语言？
**解决方案**：使用i18n方案，创建语言配置文件：
```javascript
const locales = {
    zh: { title: 'Radium设计风格', subtitle: '未来感UI设计系统' },
    en: { title: 'Radium Design Style', subtitle: 'Futuristic UI Design System' }
};

function setLocale(lang) {
    const texts = locales[lang];
    document.querySelectorAll('[data-i18n]').forEach(el => {
        el.textContent = texts[el.dataset.i18n];
    });
}
```

---

## ⚡ 性能优化建议

### 1. CSS优化

#### 使用CSS变量
统一管理颜色、间距等样式，减少重复代码：
```css
:root {
    --radium-spacing-xs: 4px;
    --radium-spacing-sm: 8px;
    --radium-spacing-md: 16px;
    --radium-spacing-lg: 32px;
}
```

#### 避免过度动画
限制同时运行的动画数量，使用 `will-change` 提示浏览器优化：
```css
.glass-card {
    will-change: transform, box-shadow;
}
```

#### 使用CSS containment
减少重绘范围：
```css
.glass-card {
    contain: layout style paint;
}
```

### 2. JavaScript优化

#### 事件节流
对高频事件（scroll、mousemove）使用节流：
```javascript
function throttle(func, limit) {
    let inThrottle;
    return function() {
        const args = arguments;
        const context = this;
        if (!inThrottle) {
            func.apply(context, args);
            inThrottle = true;
            setTimeout(() => (inThrottle = false), limit);
        }
    };
}

window.addEventListener('scroll', throttle(updateScrollProgress, 16));
```

#### 减少DOM操作
批量DOM更新，使用DocumentFragment：
```javascript
function createCards(data) {
    const fragment = document.createDocumentFragment();
    data.forEach(item => {
        const card = document.createElement('div');
        card.className = 'glass-card';
        // item.icon 存 sprite 符号 id（如 'w-glass'），绝不用 emoji
        card.innerHTML = `<div class="card-icon"><svg><use href="#${item.icon}"/></svg></div>`;
        fragment.appendChild(card);
    });
    container.appendChild(fragment);
}
```

#### 使用Intersection Observer
延迟加载卡片动画，只在进入视口时触发：
```javascript
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
            observer.unobserve(entry.target);
        }
    });
}, { threshold: 0.1 });

document.querySelectorAll('.glass-card').forEach(card => {
    card.style.opacity = '0';
    card.style.transform = 'translateY(30px)';
    observer.observe(card);
});
```

### 3. 图片优化

#### 使用WebP格式
提供现代浏览器支持的高效图片格式：
```html
<picture>
    <source srcset="image.webp" type="image/webp">
    <img src="image.png" alt="Description">
</picture>
```

#### 响应式图片
根据设备像素比提供合适大小：
```html
<img src="image.jpg" 
     srcset="image-600.jpg 600w, image-1200.jpg 1200w" 
     sizes="(max-width: 768px) 600px, 1200px"
     alt="Description">
```

#### 懒加载图片
```html
<img src="placeholder.jpg" data-src="image.jpg" class="lazy">
```
```javascript
document.addEventListener('DOMContentLoaded', () => {
    const lazyImages = document.querySelectorAll('.lazy');
    new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                const img = entry.target;
                img.src = img.dataset.src;
                img.classList.remove('lazy');
            }
        });
    }).observe(...lazyImages);
});
```

### 4. 资源优化

#### 代码分割
使用动态导入按需加载组件：
```javascript
async function loadChart() {
    const { initChart } = await import('./chart.js');
    initChart();
}
```

#### 缓存策略
使用Service Worker缓存静态资源：
```javascript
self.addEventListener('fetch', (event) => {
    event.respondWith(
        caches.match(event.request)
            .then(response => response || fetch(event.request))
    );
});
```

#### 启用Gzip压缩
在服务器端配置：
```nginx
gzip on;
gzip_types text/html text/css application/javascript image/svg+xml;
gzip_min_length 1000;
```

### 5. ECharts优化

#### 按需引入
只引入需要的图表类型：
```javascript
import * as echarts from 'echarts/core';
import { LineChart, BarChart, PieChart } from 'echarts/charts';
import { GridComponent, TooltipComponent } from 'echarts/components';

echarts.use([LineChart, BarChart, PieChart, GridComponent, TooltipComponent]);
```

#### 销毁未使用的图表
页面切换时销毁图表实例：
```javascript
function destroyCharts() {
    echarts.instances.forEach(chart => {
        chart.dispose();
    });
}
```

#### 限制图表渲染频率
```javascript
let chartTimer;
function updateChart(data) {
    clearTimeout(chartTimer);
    chartTimer = setTimeout(() => {
        chart.setOption({ series: [{ data }] });
    }, 100);
}
```

### 6. 移动端优化

#### 禁用不必要的动效
```css
@media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
    }
}
```

#### 优化触摸体验
```css
button, a {
    touch-action: manipulation;
    -webkit-tap-highlight-color: transparent;
}
```

#### 避免固定定位元素抖动
```css
.navbar {
    position: sticky;
    top: 0;
    will-change: transform;
}
```

### 7. 性能监控

#### 使用Lighthouse
定期运行性能审计：
```bash
npx lighthouse http://localhost:9292 --view
```

#### 监控FPS
```javascript
const fpsDiv = document.createElement('div');
fpsDiv.style.position = 'fixed';
fpsDiv.style.top = '10px';
fpsDiv.style.right = '10px';
document.body.appendChild(fpsDiv);

let frameCount = 0;
let lastTime = performance.now();
function measureFPS() {
    frameCount++;
    const currentTime = performance.now();
    if (currentTime - lastTime >= 1000) {
        fpsDiv.textContent = `${frameCount} FPS`;
        frameCount = 0;
        lastTime = currentTime;
    }
    requestAnimationFrame(measureFPS);
}
measureFPS();
```
