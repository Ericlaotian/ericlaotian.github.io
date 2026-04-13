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

### 大标题（一级标题）

| 字体 | 风格 | 用途 |
|------|------|------|
| **站酷快乐体** | 粉笔手写、活泼 | 主标题（优先） |
| **汉仪粉笔体** | 粉笔涂抹感 | 主标题（备选） |
| **Long Cang**（龙藏体） | 手写、行书感 | 网页标题 |

**字号要求：** 60pt+（网页约 3rem+）

**颜色要求：**
- 纯白 `#FFFFFF`（主色）
- 暖黄 `#F4E1C1`（强调）

**效果要求：** 外发光效果模拟粉笔灰
```css
.chalk-title {
    font-family: 'ZCOOL KuaiLe', 'HanYi FenBi', 'Long Cang', cursive;
    font-size: 3rem;
    color: #FFFFFF;
    text-shadow: 
        0 0 10px rgba(255, 255, 255, 0.3),
        0 0 20px rgba(255, 255, 255, 0.15),
        0 0 30px rgba(255, 255, 255, 0.08);
}
```

### 正文/说明

| 字体 | 风格 | 用途 |
|------|------|------|
| **站酷小薇体** | 手写、可爱 | 正文、说明（优先） |
| **ZCOOL XiaoWei** | 手写、清晰 | 网页正文 |

**行间距要求：** 1.5 倍

**颜色要求：** 粉笔白 `#F5F5F5` 或 粉笔灰 `rgba(255,255,255,0.7)`

```css
body {
    font-family: 'ZCOOL XiaoWei', cursive;
    line-height: 1.5;
    color: #F5F5F5;
}
```

### 英文/数字

| 字体 | 风格 | 用途 |
|------|------|------|
| **Chalkboard SE** | 黑板手写 | 英文标题（优先） |
| **Patrick Hand** | 手写工整 | 英文正文 |
| **Gloria Hallelujah** | 粉笔手写 | 网页英文 |

```css
.en-text {
    font-family: 'Chalkboard SE', 'Patrick Hand', 'Gloria Hallelujah', cursive;
}
```

### 字体加载

```html
<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=ZCOOL+KuaiLe&family=ZCOOL+XiaoWei&family=Long+Cang&family=Gloria+Hallelujah&display=swap" rel="stylesheet">
```

### 字体使用规则

| 场景 | 字体 | 字号 | 颜色 |
|------|------|------|------|
| **大标题** | 站酷快乐体 / Long Cang | 3rem+ | 纯白/暖黄 |
| **小标题** | Long Cang | 1.8rem | 纯白 |
| **正文** | 站酷小薇体 | 1rem | 粉笔白 |
| **英文/数字** | Chalkboard SE | 同级 | 同级 |
| **注释/辅助** | ZCOOL XiaoWei | 0.9rem | 粉笔灰 |

---

## 三、质感处理

### 粉笔纹理叠加

**网页实现：**
```css
/* 文字粉笔灰效果 */
.chalk-text {
    text-shadow: 
        0 0 10px rgba(255, 255, 255, 0.3),
        0 0 20px rgba(255, 255, 255, 0.15),
        0 0 30px rgba(255, 255, 255, 0.08);
}

/* 粉笔纹理叠加（网页） */
.chalkboard-bg::after {
    content: '';
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url("粉笔纹理.png");
    mix-blend-mode: multiply;
    opacity: 0.3;
    pointer-events: none;
}
```

**设计软件（PS/AI）：**
1. 创建文字图层
2. 叠加粉笔纹理图片
3. 混合模式设为「正片叠底」或「叠加」
4. 不透明度 20%-40%

**效果要求：**
- 文字看起来像是真的写在板子上
- 不是浮在表面，有摩擦质感
- 边缘有粉笔灰掉落的颗粒感

---

## 四、粉笔质感效果

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

## 五、装饰元素

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

## 六、视觉层次

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

## 七、动效规范

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

## 八、场景应用

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
