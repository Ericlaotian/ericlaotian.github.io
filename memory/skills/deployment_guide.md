# 部署操作指南

> 火花 · 艾瑞克老田工作室项目沉淀

## 方案一：本地预览（当前使用）

### 启动服务
```bash
cd /workspace/website
python3 -m http.server 8000 --bind 0.0.0.0
```

### 访问
通过 CodeBuddy preview 服务生成临时 URL。

### 特点
- 即时可用，无需配置
- URL 临时有效
- 适合内部测试和预览

---

## 方案二：GitHub Pages（推荐长期方案）

### 步骤
1. 在 GitHub 创建仓库：`erik-laotian.github.io`
2. 上传 `index.html` 和 `style.css`
3. 等待 1-2 分钟自动部署
4. 访问 `https://erik-laotian.github.io`

### 自定义域名（可选）
1. 购买域名（推荐 .com，约 ¥55/年）
2. 在域名商配置 DNS：`CNAME` 记录指向 `erik-laotian.github.io`
3. 在仓库 Settings → Pages → Custom domain 填入域名
4. 启用 Enforce HTTPS

### 优点
- 免费
- 自动 HTTPS
- 支持 CI/CD（推送即部署）
- 可绑定自定义域名

---

## 方案三：Vercel（推荐备选）

### 步骤
1. 注册 Vercel 账号
2. 导入 GitHub 仓库
3. 自动检测静态站点并部署
4. 获得免费域名：`xxx.vercel.app`

### 优点
- 国内访问速度优于 GitHub Pages
- 自动部署
- 可绑定自定义域名
- 免费额度充足

---

## 方案四：腾讯云轻量应用服务器

### 步骤
1. 购买轻量应用服务器（¥50-100/月）
2. 安装 Nginx：`apt install nginx`
3. 配置 Nginx 指向网站目录
4. 配置域名解析到服务器 IP
5. 申请免费 SSL 证书（Let's Encrypt）

### 优点
- 完全可控
- 国内访问最快
- 可托管其他服务

### 缺点
- 需要持续付费
- 需要运维能力
