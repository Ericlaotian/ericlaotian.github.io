# 数字员工火花 · 黑板报视觉风格标准

> 版本：v1.0 | 定义日期：2026-04-13

---

## 风格定义

**名称**：黑板报 (Chalkboard/Blackboard Style)

**核心关键词**：
- 深墨绿色/黑色背景
- 白色/彩色粉笔手绘线条
- 粉笔灰质感
- 手写字体
- 不规则边框

---

## 一、配色方案

### 主色板

| 颜色 | 色值 | 用途 |
|------|------|------|
| **黑板背景** | `#1B4D3E` | 主背景色（深墨绿） |
| **黑板背景（备选）** | `#2b2b2b` | 纯黑背景（夜间模式） |
| **粉笔白** | `#f5f5f5` | 主要文字 |
| **粉笔灰** | `rgba(255,255,255,0.5)` | 次要文字 |

### 点缀色

| 颜色 | 色值 | 用途 |
|------|------|------|
| **粉笔红** | `#ff6b6b` | 重点强调、标题 |
| **粉笔黄** | `#ffd93d` | 高亮、标注 |
| **粉笔橙** | `#ff9f43` | 次要强调 |
| **粉笔绿** | `#26de81` | 成功、正向 |
| **粉笔蓝** | `#45aaf2` | 链接、信息 |

---

## 二、字体规范

### 中文推荐字体

| 字体 | 风格 | 用途 |
|------|------|------|
| **Long Cang**（龙藏体） | 手写、行书感 | 标题、重点文字 |
| **ZCOOL XiaoWei**（站酷小薇） | 手写、可爱 | 正文、说明 |
| **汉仪小麦体** | 粉笔涂抹感 | 可选替换 |
| **方正喵呜体** | 手写萌系 | 可选替换 |

### 英文推荐字体

| 字体 | 风格 | 用途 |
|------|------|------|
| **Gloria Hallelujah** | 粉笔手写 | 英文标题 |
| **KG Blank Space Sketch** | 粉笔涂抹 | 可选替换 |
| **Patrick Hand** | 黑板书写 | 正文 |
| **Architects Daughter** | 手写工整 | 辅助文字 |

### 字体加载

```html
<link href="https://fonts.googleapis.com/css2?family=Long+Cang&family=ZCOOL+XiaoWei&family=Gloria+Hallelujah&display=swap" rel="stylesheet">
```

### 字体使用规则

```css
/* 标题 */
h1, h2, h3 {
    font-family: 'Long Cang', 'Gloria Hallelujah', cursive;
}

/* 正文 */
body {
    font-family: 'ZCOOL XiaoWei', 'Patrick Hand', cursive;
}
```

---

## 三、粉笔质感效果

### 1. 粉笔灰噪点

```css
/* 文字粉笔灰效果 */
.chalk-text {
    text-shadow: 
        0 0 1px rgba(255, 255, 255, 0.5),
        0 0 2px rgba(255, 255, 255, 0.3),
        1px 1px 3px rgba(0, 0, 0, 0.2);
}

/* 背景粉笔灰纹理 */
.chalkboard-bg::before {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.08'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
}
```

### 2. 粉笔涂抹感

```css
/* 粉笔涂抹边框 */
.chalk-border {
    border: 3px solid rgba(255, 255, 255, 0.6);
    border-radius: 5px;
    filter: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='rough'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.04' numOctaves='5'/%3E%3CfeDisplacementMap in='SourceGraphic' scale='3'/%3E%3C/filter%3E%3C/svg%3E#rough");
}
```

### 3. 手绘抖动线条

```css
/* 虚线边框（模拟手绘） */
.hand-drawn {
    border: 2px dashed rgba(255, 255, 255, 0.4);
}

/* 抖动动画 */
@keyframes shake {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-1px) rotate(-0.5deg); }
    75% { transform: translateX(1px) rotate(0.5deg); }
}
```

---

## 四、装饰元素

### 1. 粉笔夹

```css
.chalk-clip {
    width: 40px;
    height: 20px;
    background: linear-gradient(135deg, #D4A574, #C4956A);
    border-radius: 0 0 6px 6px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}
```

### 2. 擦除痕迹

```css
.erased {
    background: linear-gradient(
        90deg,
        transparent 0%,
        rgba(255,255,255,0.1) 50%,
        transparent 100%
    );
    opacity: 0.3;
}
```

### 3. 彩色粉笔条

```css
.chalk-line {
    height: 3px;
    background: linear-gradient(90deg,
        transparent,
        #ff6b6b,
        #ffd93d,
        #26de81,
        #45aaf2,
        transparent
    );
}
```

---

## 五、视觉层次

### 信息层级

| 层级 | 表现方式 |
|------|---------|
| **一级标题** | 大号字体 + 彩色粉笔 + 阴影发光 |
| **二级标题** | 中号字体 + 白色粉笔 + 虚线下划线 |
| **正文** | 标准字体 + 粉笔灰 |
| **强调** | 加粗 + 彩色粉笔 |
| **辅助信息** | 小号字体 + 粉笔灰50%透明度 |

### 间距规范

| 元素 | 间距 |
|------|------|
| 板块间距 | `4rem - 5rem` |
| 标题与内容 | `1.5rem - 2rem` |
| 段落间距 | `1rem - 1.5rem` |
| 卡片间距 | `1.5rem - 2rem` |

---

## 六、动效规范

### 微动效

| 效果 | 触发 | 时长 |
|------|------|------|
| **hover发光** | 鼠标悬停 | 0.3s |
| **抖动** | 强调元素 | 循环 |
| **渐入** | 滚动进入视口 | 0.5s |
| **粉笔灰飘落** | 页面加载 | 循环 |

### 过渡

```css
/* 标准过渡 */
transition: all 0.3s ease;

/* 弹性过渡 */
transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
```

---

## 七、场景应用

### 网站主页

- 背景：深墨绿 + 粉笔灰纹理
- 导航：粉笔白 + hover彩色
- 卡片：虚线边框 + 粉笔夹装饰

### 小红书配图

- 背景：纯黑或深墨绿
- 文字：粉笔白 + 彩色点缀
- 边框：手绘虚线

### 公众号文章

- 标题：粉笔白/红
- 小标题：粉笔黄/橙
- 正文：粉笔白
- 重点：下划线 + 彩色

---

## 八、素材库

### 图标风格

- 线性图标
- 粉笔涂抹感边缘
- 白色/彩色填充

### 插画风格

- 手绘简笔画
- 粉笔质感填充
- 不规则边框

### 照片处理

- 黑白/褪色滤镜
- 叠加粉笔灰纹理
- 虚线边框装饰

---

## 九、品牌一致性

### 适用范围

- 华创天诚官网
- 数字员工火花输出
- 小红书内容
- 公众号文章
- PPT演示文稿
- 名片、宣传物料

### 识别特征

1. **一眼可辨的黑板报风格**
2. **粉笔质感文字和边框**
3. **彩色点缀但不花哨**
4. **手写温度感**

---

## 十、版本记录

| 版本 | 日期 | 修改内容 |
|------|------|---------|
| v1.0 | 2026-04-13 | 初版定义 |

---

*火花 · 数字员工视觉规范*
