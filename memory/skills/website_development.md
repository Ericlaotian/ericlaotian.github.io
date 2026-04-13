# 网站开发经验

> 火花 · 艾瑞克老田工作室项目沉淀

## 项目概述
- **客户**：艾瑞克老田工作室
- **类型**：个人品牌展示站
- **风格**：暗黑黑板报（Chalkboard）卡通风
- **技术栈**：纯 HTML/CSS + Google Fonts

## 设计风格要点

### 配色方案
| 角色 | 色值 | 用途 |
|------|------|------|
| 背景色 | `#2b2b2b` | 模拟黑板 |
| 文字色 | `#f0f0f0` | 粉笔白 |
| 强调色 | `#ff9f43` | 橙色高亮 |
| 辅助色 | `#26de81` / `#45aaf2` | 绿色/蓝色 |

### 字体
- **Ma Shan Zheng**（马善政）：标题用手写体，增加手写感
- **ZCOOL KuaiLe**（站酷快乐体）：正文用卡通体，轻松活泼
- 加载方式：Google Fonts CDN

### 视觉元素
- 粉笔虚线边框（`border: 2px dashed`）
- 粉笔夹装饰（CSS 绘制，模拟物理回形针）
- 黑板纹理背景（多层 radial-gradient 叠加）
- CSS 绘制极客青蛙形象（无需图片资源）

## 关键 CSS 技巧

### 黑板纹理
```css
body::before {
    background:
        radial-gradient(ellipse at 20% 50%, rgba(255,255,255,0.02), transparent 50%),
        repeating-linear-gradient(0deg, transparent, transparent 2px, rgba(255,255,255,0.003) 2px, rgba(255,255,255,0.003) 4px);
    pointer-events: none;
}
```

### 粉笔夹装饰
```css
.chalk-clip {
    width: 60px; height: 30px;
    background: linear-gradient(135deg, #8B4513, #A0522D);
    border-radius: 0 0 8px 8px;
}
```

### 滚动动画
- 使用 `IntersectionObserver` 实现卡片入场动画
- 元素初始 `opacity: 0; transform: translateY(30px)`
- 进入视口时添加 `.visible` 类

## 坑 & 解决方案

1. **Google Fonts 国内加载慢**
   - 考虑使用 fonts.googleapis.cn 镜像
   - 或下载字体文件本地托管

2. **CSS 绘制复杂图形耗时**
   - 青蛙形象用纯 CSS 实现，适合简单卡通
   - 复杂形象建议用 SVG 或图片

3. **虚线边框在不同浏览器表现不一致**
   - `dashed` 样式跨浏览器差异小，可放心使用
   - 圆角 + 虚线组合效果良好

## 文件结构
```
/website
├── index.html    # 页面结构
├── style.css     # 所有样式
└── server.log    # 服务器日志
```
