# Note: Cao25-T2ICtrlSurvey

论文全名：Controllable Generation with Text-to-Image Diffusion Models: A Survey
译文参考：[TPAMI 2025 | 基于文生图扩散模型的可控生成：综述](https://zhuanlan.zhihu.com/p/1992894155656040595)

## 写作动机

现有扩散综述仅粗略提及文生图可控技术，或只覆盖单类控制方案，缺少以控制条件为核心、体系化梳理全品类可控生成技术的综述

## 文章结构

1. 基础前置知识：DDPM/主流T2I扩散模型、可控任务分类、评测指标、本文三层分类体系
2. 单类新颖条件可控生成
3. 多条件联合可控生成
4. 通用无差别万能可控生成
5. 可控生成下游应用
6. 全文总结与未来研究方向

## 分类逻辑

1. 宏观三层顶层分类（按控制条件数量/通用性划分）：单新颖条件生成、多条件融合生成、通用可控生成
2. 底层微观范式（单条件模块统一划分）：条件打分预测、训练无代价条件打分估计
3. 细分技术拆分：
    - 条件打分预测：微调式PEFT方案、Adapter插件方案
    - 条件引导打分估计：推理阶段梯度引导类方法

> Additionally, we provide a detailed overview of research in this area, categorizing it from the condition perspective into three directions: generation with specific conditions, generation with multiple conditions, and universal controllable generation.

## 内容梳理

1. 引言
    1. 点明纯文本提示存在表达局限，可控生成是行业刚需；统计历年可控论文数量证明领域爆发式增长
    2. 对比过往综述缺陷：通用扩散综述仅浅涉可控、多模态综述不深挖T2I控制机制
    3. 明确本文四大核心贡献：三层条件分类体系、统一两大底层控制范式、系统梳理各类代表方法、完整汇总全行业落地应用
2. 前置预备知识
    1. DDPM基础原理：前向加噪、反向去噪数学公式，拓展DDIM、流匹配等衍生框架
    2. 主流文生图扩散模型汇总表：像素空间（GLIDE/Imagen）、隐空间（SD全系列、PixArt、Flux）
    3. 可控任务大类：空间控制、图像个性化、脑电/音频跨模态控制、文本渲染、上下文生成等
    4. 评测两大维度：图像质量（FID、HPS、美学分）、条件对齐（CLIPScore、mIoU、DINO相似度）
    5. 提出全文核心三层分类框架
3. 单新颖条件可控生成
    1. 范式一：条件打分预测
        - 微调PEFT分支：DreamBooth、LoRA系列
        - Adapter插件分支：
          - 空间控制：ControlNet、T2I-Adapter、UniControl、布局类GLIGEN
          - 个性化：IP-Adapter、PhotoMaker、ELITE等人脸/实物参考生成
          - 跨模态：音频引导、相机视角控制
          - 增强文本：长段落生成、多语言、图像文字渲染
    2. 范式二：训练无代价条件打分估计（推理阶段梯度引导）
        - 注意力图调制：布局约束、属性绑定、参考特征注入
        - 外部预训练模型梯度引导：Universal Guidance、BoxDiff、Attend-and-Excite等
4. 多条件融合可控生成
    按融合技术分为5大类：联合训练、持续学习、权重融合、注意力融合、引导组合；分别梳理Composer、ZipLoRA、Mix-of-Show等代表方案，解决多条件冲突、特征混淆问题
5. 通用万能可控生成
    统一框架，不限定输入条件类型：
    1. 通用条件打分预测（DiffBlender、Emu2多模态上下文）
    2. 通用条件引导打分估计（Universal Guidance、FreeDom，复用现成检测器提供梯度）
6. 可控生成下游应用
    图像编辑、修复补全、图像合成、文生3D、基于扩散的世界模型
7. 总结与未来方向
    1. 全文工作整体复盘
    2. 两大前沿方向：统一跨模态通用控制范式、构建带精细控制机制的视频世界模型

## 总结启发

这篇综述完全聚焦“可控”细分赛道，粒度更极致，专门拆解各类附加控制信号的底层数学机理与工程实现，适合做可控生成、ControlNet、个性化微调方向来看，感觉我在写综述的时候也可以来个“可控”/“条件化生成”的细分赛道

时间上，这篇文章已经覆盖了很多2025的工作了，相对而言已经比较新了，而且从论文中的有张数量图看来“可控生成”赛道的文章也是逐年上涨的，一年都有上百篇，完全够写综述了
