# Note: Zhang24-T2IDiffSurvey

论文全名：Text-to-image Diffusion Models in Generative AI: A Survey

译文参考：[【T2I】Text-to-image Diffusion Models in Generative AI: ASurvey](https://blog.csdn.net/2201_75801514/article/details/148117916)

## 写作动机

现有扩散综述多泛化覆盖全视觉领域，缺少专门针对文生图扩散的完整梳理；传统文生图综述多聚焦`GAN`、自回归方案。本文是首篇专门聚焦基于扩散模型的文本生成图像完整综述，填补细分赛道综述空白

## 文章结构

1. 扩散模型基础理论铺垫
2. 初代经典文生图扩散模型分两类梳理（像素空间/隐空间）
3. 后续全方面技术改进方案汇总
4. 模型评测体系
5. 跨模态衍生应用（文生视频、图像编辑等）
6. 现存挑战与未来研究方向

## 分类逻辑

1. 初代模型：按扩散执行空间划分（像素空间、隐空间）
2. 后续改进：按优化目标划分（网络架构优化、可控生成方案）

> In this section, we introduce the pioneering text-to-image work based on diffusion models, which can be roughly categorized considering where the diffusion process is conducted, i.e., the pixel space or latent space. The first class of methods generates images directly from the high-dimensional pixel level, including GLIDE and Imagen. Another stream of works propose to first compress the image to a low-dimensional space, and then train the diffusion model on this latent space. Representative methods falling into the class of latent space include Stable Diffusion and DALL-E 2.

## 内容梳理

1. 引言
    1. 阐述文生图任务通用AI价值，梳理文生图技术发展时间线（`AlignDRAW`/`GAN`/自回归/`Diffusion`四代路线）
    2. 对比已有综述短板：通用扩散综述不深耕T2I、`GAN`文生综述完全忽略扩散方法，点明本文独有定位首篇文生图扩散专项综述
    3. 给出全文章节结构图
2. 扩散模型基础背景
    1. 扩散模型前身理论：早期`DPM`、`Score-based`匹配模型
    2. `DDPM`完整原理：前向加噪、反向去噪数学流程、基础优化目标
    3. 条件生成核心技术：分类器引导、无分类器引导
3. 初代经典文生图扩散模型（开山之作）
    1. 像素空间范式：`GLIDE`、`Imagen`
    2. 隐空间范式：`Stable Diffusion`、`DALL-E2`，分别讲解`VAE`隐压缩、`CLIP`多模态隐对齐两条技术路线
    3. 梳理`SD`全系列迭代、`DALL-E`系列迭代更新特性
4. 模型进阶改进方案
    1. 架构优化分支：引导策略优化、多阶段去噪器、`UNet/DiT`骨干替换、采样加速技术
    2. 灵活可控生成分支：
        - 概念定制：Textual Inversion、DreamBooth
        - 空间布局控制：BoxDiff、SpaText、草图引导
        - 通用多条件控制：ControlNet、T2I-Adapter等
        - 分布外增强：检索增强扩散RDM
5. 模型评测体系
    1. 技术量化评测：FID、CLIP Score、IS等指标；DrawBench/UniBench等人工评测基准
    2. 伦理安全评测
6. 图像生成之外拓展应用
    1. T2-X跨模态生成
    2. 文本引导图像编辑
7. 挑战与未来展望
    1. 当前现存痛点：数据集偏见与多语言缺失、伪造检测困难、算力数据门槛高
    2. 未来方向：安全公平生成、统一多模态大扩散框架、跨领域模型融合

## 总结启发

和先前读过的两篇工作不同，它们属于全领域通用扩散综述；本文是垂直细分赛道综述，只聚焦文生图扩散，粒度更细、工程落地相关内容更丰富，适合做AIGC文生图方向入门

时间局限上，论文截止2024年11月文献，2025–2026年新工作未收录，即便如此论文依旧完成了一篇针对文生图扩散这样一个细分赛道的综述，这说明扩散模型细分领域的研究数量和热度是够的，意味着2026写一个更细方向的综述完全有可能。进一步坚定我寻找相对更新一点的细分赛道的想法

这篇文章读起来有种莫名的舒服感，让我想继续读下去，是因为行文思路符合一般人的思考逻辑吗？希望日后自己写综述也能有类似的感觉
