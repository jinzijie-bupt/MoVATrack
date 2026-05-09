# GitHub Pages 部署 — 零基础步骤

针对你的情况（GitHub 用户名：[`jinzijie-bupt`](https://github.com/jinzijie-bupt)，没有部署过 Pages）的逐步操作。

整个过程大约 **10-15 分钟**。结果是：
- 一个公网可访问的项目主页：**`https://jinzijie-bupt.github.io/<你创建的仓库名>/`**
- 任何人可以打开这个链接看到你的项目页面、视频 demo、结果表

---

## 前置：确认环境

我们当前的服务器有 git，所以可以直接在服务器上推。先确认一下：

```bash
# 在服务器命令行
git --version
# 应该输出类似 git version 2.34.1
```

确认 GitHub 账号已经登录 / 有 Personal Access Token (PAT)。如果没 PAT：
1. 浏览器打开 https://github.com/settings/tokens
2. 点 "Generate new token" → "Generate new token (classic)"
3. Note 填 "AUTriX deploy"，过期时间随便（建议 1 个月）
4. 勾选权限：**`repo`** （唯一必须的）
5. 点 Generate，**复制 token**（页面只显示一次，离开就找不到了）
6. 把 token 暂时记在某个安全的地方（如本地密码管理器）

---

## 步骤 1：在 GitHub 上新建仓库

浏览器打开：[github.com/new](https://github.com/new)

填写：
- **Repository name**: `MoVATrack`（或你喜欢的名字，但别用中文）
- **Description**: `本科毕业论文项目主页 — 基于多模态图像信息融合的无人机跟踪算法`
- **Public**（必须公开，否则免费版 GitHub Pages 不能用）
- 不勾选 "Initialize this repository with a README"（咱们待会儿从本地 push 进去）

点 **Create repository**。

完成后你会拿到一个仓库 URL，类似：
```
https://github.com/jinzijie-bupt/MoVATrack
```

---

## 步骤 2：在服务器上准备 git 仓库

在服务器上执行（从 `docs/` 目录开始）：

```bash
# 进入项目目录
cd /data/public/jinzijie_uautrack/AUTriX_v5_local/docs

# 初始化一个 git 仓库（如果还没初始化）
git init

# 配置一下 git 用户名（如果第一次用）
git config user.name "金子杰"
git config user.email "你的邮箱@邮箱.com"

# 添加所有文件
git add index.html static/ DEPLOY_GUIDE.md README.md

# 提交
git commit -m "init: MoVATrack project page"

# 设置默认分支为 main（GitHub 现在默认）
git branch -M main

# 关联远程仓库
git remote add origin https://github.com/jinzijie-bupt/MoVATrack.git

# 推送
git push -u origin main
```

最后一步会要求**用户名**和**密码**：
- 用户名填：`jinzijie-bupt`
- 密码填：刚才生成的 **Personal Access Token**（不是 GitHub 登录密码！）

视频 + 图片总共约 **17 MB**，第一次 push 大概 10-30 秒（看网络）。

---

## 步骤 3：开启 GitHub Pages

浏览器打开你的仓库：`https://github.com/jinzijie-bupt/MoVATrack`

1. 点上面的 **Settings**（最右边的齿轮图标）
2. 左侧菜单找到 **Pages**
3. 在 "Build and deployment" 区域：
   - **Source** 选：`Deploy from a branch`
   - **Branch** 选：`main`，再选 `/ (root)` 然后 Save

**等 1-3 分钟**，GitHub 自己会编译。然后页面顶部会出现绿色提示：
```
Your site is live at https://jinzijie-bupt.github.io/MoVATrack/
```

打开这个链接，应该就能看到你的项目主页了！

---

## 之后想更新内容

任何时候改了 `index.html` / CSS / 视频 / 图片，只需：

```bash
cd /data/public/jinzijie_uautrack/AUTriX_v5_local/docs
git add .
git commit -m "更新：修了 xxx"
git push
```

GitHub Pages 会在 1-2 分钟内自动重新部署。

---

## 故障排查

### Q: `git push` 报 "Authentication failed"
A: PAT 可能过期了或权限不对。回到步骤 0 重新生成一个 token，必须勾 `repo` 权限。

### Q: 推完了但访问 `https://jinzijie-bupt.github.io/MoVATrack/` 是 404
A: 可能 GitHub 还在编译，等 5 分钟再试。如果还不行：
   - Settings → Pages 看 "Last deployment" 有没有红色错误
   - 确认 Source 是 `main` + `/ (root)`，而不是 `gh-pages` 或 `/docs`

### Q: 页面打开了但视频不放
A: 视频文件可能没推上去。在仓库里检查 `static/videos/` 是否有 5 个 .mp4 文件。
   如果没有：
   ```bash
   git lfs install   # 一次就够
   git lfs track "*.mp4"
   git add .gitattributes static/videos/*.mp4
   git commit -m "use LFS for videos"
   git push
   ```

### Q: 想让链接更短/更好记
A: GitHub Pages 支持自定义域名，但需要你自己买域名（可选，不推荐本科毕设搞这个）。

---

## 文件最终清单（推上 GitHub 的内容）

```
docs/                                         <- 整个 docs 目录推上去
├── index.html                                主页
├── static/
│   ├── css/index.css                         样式
│   ├── images/  (5 张 poster JPG)            缩略图
│   └── videos/  (5 段 MP4)                   视频
├── DEPLOY_GUIDE.md                           本文（可选推或不推）
└── README.md                                 项目页说明
```

总大小约 **17 MB**（5 段视频占了大头）。

---

## 推完之后该做什么

1. ✅ 把链接 `https://jinzijie-bupt.github.io/MoVATrack/` 给你导师看一下，问下有什么意见
2. 论文写完整 → 上传到学校仓库 / arXiv → 把 PDF 链接填回 `index.html` 的 "论文 PDF" 徽章
3. 代码整理好 → 单独建一个公开仓库 → 把仓库链接填回 "代码" 徽章
4. 等你 HF Pro 充值好 → 部署 HF Space → 把 Space 链接填回 "在线 Demo" 徽章

每次更新只需要改 `index.html` 然后 `git push` 就行，**不需要重新部署**。
