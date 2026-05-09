# MoVATrack — 项目主页

> **基于多模态图像信息融合的无人机跟踪算法设计**
> 金子杰 · 北京科技大学 自动化学院 · 指导教师：李擎 教授
>
> 本科毕业设计（论文）项目主页 · 仿 Nerfies / CVPR supplementary 模板

**🌐 在线查看：** `https://jinzijie-bupt.github.io/MoVATrack/`（部署后）

**🚀 第一次部署？** 请看 [DEPLOY_GUIDE.md](DEPLOY_GUIDE.md) 零基础逐步操作。

## 目录结构

```
docs/
├── index.html                    主页（含 Header / Showcase / A/B / Results / BibTeX）
├── static/
│   ├── css/
│   │   └── index.css            自定义 CSS（USTB 蓝色调）
│   ├── images/                  Poster 缩略图（5 张）
│   │   ├── day_clear_poster.jpg
│   │   ├── dusk_absent_poster.jpg
│   │   ├── night_lowlight_poster.jpg
│   │   ├── ab_night_vaaf_poster.jpg
│   │   └── ab_dusk_mgtr_poster.jpg
│   └── videos/                  Showcase / A/B 视频（5 段 MP4，~16 MB 总）
│       ├── day_clear.mp4
│       ├── dusk_absent.mp4
│       ├── night_lowlight.mp4
│       ├── ab_night_vaaf.mp4
│       └── ab_dusk_mgtr.mp4
└── README.md                    本文件
```

## 本地预览

```bash
cd /data/public/jinzijie_uautrack/AUTriX_v5_local/docs
python -m http.server 8000
# 浏览器打开 http://localhost:8000
# 或 SSH 隧道：ssh -L 8000:localhost:8000 user@server
```

## 部署到 GitHub Pages

### 方式一：使用 `docs/` 目录（推荐）

1. 在你 GitHub 仓库创建 `docs/` 目录，把 `index.html` + `static/` 推上去
2. 仓库设置 → Pages → Source 选择 `Branch: main, /docs`
3. 等几分钟，访问 `https://<你的用户名>.github.io/<仓库名>/`

### 方式二：使用 `gh-pages` 分支

```bash
# 在仓库根目录
git checkout --orphan gh-pages
git rm -rf .
cp -r docs/* .
git add .
git commit -m "Initial project page"
git push origin gh-pages
# Pages → Source → Branch: gh-pages, /(root)
```

## 部署前需要替换的占位

`index.html` 里的徽章链接（搜索 `PLACEHOLDER`）：

| 徽章 | 占位链接 | 替换为 |
|---|---|---|
| Paper | `#` | 论文 PDF 公开链接（如挂在 arXiv 或学校仓库） |
| Code | `https://github.com/PLACEHOLDER_USER/PLACEHOLDER_REPO` | 你的 GitHub 仓库 URL |
| Model | `https://huggingface.co/PLACEHOLDER_USER/MoVATrack` | HF 模型仓库 URL（如未公开可暂留 `#`） |
| Dataset | `https://github.com/ZhaoJ9014/Anti-UAV` | ✅ 已填好（Anti-UAV 官方仓库） |
| Online Demo | `https://huggingface.co/spaces/PLACEHOLDER_USER/MoVATrack` | HF Space URL，待部署后替换 |

## Hugging Face Space 部署（在线 Demo）

`docs/index.html` 顶部「🚀 Online Demo」徽章应链到 HF Space。
HF Space 的核心代码在 `code/hci/main_gradio.py`，可直接搬到 HF Spaces。

参考流程详见 `code/hci/HF_SPACE_DEPLOY.md`（待创建）。
