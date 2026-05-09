<div align="center">

# MoVATrack

### 基于多模态图像信息融合的无人机跟踪算法设计

*Design of UAV Tracking Algorithm Based on Multi-modal Image Information Fusion*

[![Project Page](https://img.shields.io/badge/Project-Page-blue)](https://jinzijie-bupt.github.io/MoVATrack/)
[![Live Demo](https://img.shields.io/badge/🤗_Spaces-Live_Demo-yellow)](https://huggingface.co/spaces/jin-bupt/MoVATrack)
[![Status](https://img.shields.io/badge/Status-WIP-orange)](https://github.com/jinzijie-bupt/MoVATrack)
[![License](https://img.shields.io/badge/License-CC--BY--NC--4.0-green)](#license)

**[金子杰](https://github.com/jinzijie-bupt)** · 指导教师：**李擎 教授**
**[北京科技大学](https://www.ustb.edu.cn/) · [自动化学院](https://saee.ustb.edu.cn/)**
*本科毕业设计（论文）· 2026 届*

[🌐 在线项目主页](https://jinzijie-bupt.github.io/MoVATrack/) &nbsp;|&nbsp; [🤗 在线 Demo (HF Space)](https://huggingface.co/spaces/jin-bupt/MoVATrack)

</div>

---

## 项目简介

本项目针对无人机视觉跟踪任务面临的三类核心挑战，以 SUTrack 单流跟踪框架为基础，
在**架构 / 训练 / 推理**三个层面分别提出三个核心模块：

- **VAAF**（Visibility-Aware Adaptive Fusion）— 可见性自适应融合
- **RMD**（Robust Modality Distillation）— 鲁棒模态蒸馏
- **MGTR**（Memory-Guided Tracking & Re-detection）— 记忆引导跟踪与重检测

方法在 Anti-UAV、Anti-UAV410、DUT Anti-UAV 与 CST Anti-UAV 四个公开基准上系统验证。
在 CST 极小目标基准上 SA(0.30) 达到 **39.18**，超越当前公开最优方法 GlobalTrack 共 **3.96** 个百分点。

> 📖 **完整方法说明、视频演示、量化结果请查看：[在线项目主页](https://jinzijie-bupt.github.io/MoVATrack/)**

## 主要结果

| 数据集 | 指标 | 基线 | UAUTrack | **本文方法** | Δ |
|---|---|---:|---:|---:|---:|
| Anti-UAV TIR | SA | 70.50 | 71.90 | **73.81** | +1.91 |
| Anti-UAV RGB | SA | 75.10 | 76.20 | **77.47** | +1.27 |
| Anti-UAV410 | SA | 65.20 | 66.30 | **67.07** | +0.77 |
| **CST Anti-UAV** | SA(0.30) | 32.10 | 35.92 *(GlobalTrack)* | **39.18** | **+3.96** |

## 仓库结构

本仓库为项目主页托管仓库（GitHub Pages 站点源），包含：

```
.
├── index.html          项目主页（含 Hero / 演示视频 / 方法概述 / 数据集 / 结果表 / BibTeX）
├── static/
│   ├── css/index.css   样式表
│   ├── images/         5 张演示帧 poster
│   └── videos/         5 段双模态跟踪演示视频（17 MB 总大小）
└── README.md           本文档
```

**在线 Demo** 已上线于 [Hugging Face Space](https://huggingface.co/spaces/jin-bupt/MoVATrack)
（ZeroGPU A100 burst，支持 RGB+IR 双模态 / 仅 RGB / 仅 IR 三种模式 + MGTR 超参在线调节 + 模态退化压测）；
**论文 PDF**、**完整代码**与**模型权重**将随论文进展逐步公开。

## 数据集

本文实验所用 4 个公开无人机基准：

| 数据集 | 模态 | 发布机构 | 项目链接 |
|---|---|---|---|
| Anti-UAV | RGB + IR | 中国科学院 | [官方主页](https://anti-uav.github.io/) · [GitHub](https://github.com/ZhaoJ9014/Anti-UAV) |
| Anti-UAV410 | IR | 北京理工大学 | [下载 (官方仓库)](https://github.com/ZhaoJ9014/Anti-UAV) · [arXiv](https://arxiv.org/abs/2306.15767) |
| DUT Anti-UAV | RGB | 大连理工大学 | [GitHub](https://github.com/wangdongdut/DUT-Anti-UAV) |
| CST Anti-UAV | IR | 南昌航空大学 | [GitHub](https://github.com/PCwenyue/CST-Anti-UAV) |

## 引用

```bibtex
@thesis{jin2026movatrack,
  title  = {基于多模态图像信息融合的无人机跟踪算法设计},
  author = {金子杰},
  school = {北京科技大学 自动化学院},
  type   = {本科毕业设计（论文）},
  year   = {2026},
  advisor= {李擎}
}
```

## License

页面内容、视频演示遵循 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/) 协议，
仅供学术与非商业用途。

页面模板参考自 [Nerfies](https://nerfies.github.io)，基于 [Bulma CSS](https://bulma.io) 构建。

---

<div align="center">

© 2026 金子杰 · [北京科技大学](https://www.ustb.edu.cn/) [自动化学院](https://saee.ustb.edu.cn/)

</div>
