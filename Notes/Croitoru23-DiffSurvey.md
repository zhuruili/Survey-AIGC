# Note: Croitoru23-DiffSurvey

论文全名：Diffusion Models in Vision: A Survey
译文参考：[震撼TPAMI长文综述《视觉中的扩散模型》全文翻译](https://zhuanlan.zhihu.com/p/670413482)

## 写作动机

在“INTRODUCTION”章节的末尾，阐述了两个方面：

- 扩散模型的研究大量涌现，及时写一篇综述来帮助读者快速了解这一领域
- 提出多视角的扩散模型分类方法，帮助读者快速找到相关的研究

> 感觉这个动机比较宽泛，所有的综述都可以说这两点

## 文章结构

1. INTRODUCTION
2. GENERIC FRAMEWORK
3. A CATEGORIZATION OF DIFFUSION MODELS
4. CLOSING REMARKS AND FUTURE DIRECTIONS

大致是 ‘引言->梳理与概述->分类与详述->总结与展望’ 的行文思路

## 分类逻辑

本文采用四层多维度复合分类体系，核心以「任务」为主分类轴，辅以三大辅助分类维度对扩散模型进行完整梳理：

- 下游计算机视觉任务（核心主分类）
    把所有扩散模型按应用场景拆分为：无条件图像生成、条件图像生成、图生图、文生图、超分等数十类任务，每个任务单独综述相关论文

- 引导条件（二级细分维度）
    区分模型是无条件生成，还是带条件生成（类别标签、文本、原图、掩码、CLIP 特征等）

- 底层理论框架（三级细分维度）
    每个任务下的模型再按三大基础范式划分：DDPM（去噪扩散概率模型）、NCSN/Score-Based（噪声条件评分网络）、SDE（连续随机微分方程）

- 数据集（补充维度）
    各模型实验所用数据集（CIFAR、ImageNet、CelebA等），作为横向对比的分类参考

而这个分类逻辑是要在分类章节直接写明的：
> "We categorize diffusion models into a multi-perspective taxonomy considering different criteria of separation. Perhaps the most important criteria to separate the models are defined by (i) the task they are applied to, and (ii) the input signals they require. Furthermore, as there are multiple approaches in formulating a diffusion model, (iii) the underlying framework is another key factor for classifying diffusion models. Finally, the (iv) data sets used during training and evaluation are also of high importance, because they provide the means to compare different models on the same task. Our categorization of diffusion models according to the criteria enumerated above is presented in Table 1."

而这里的分类标准也是后续综述中论文列表的四项指标

## 内容梳理

从头到尾梳理文章的每个部分究竟在讲哪方面的内容，关注方向而不是内容本身

1. 引言
   1. 介绍扩散模型的突出表现
   2. 列举扩散模型的应用任务
   3. 说明扩散模型架构上的三种子类别
   4. 介绍行文思路
   5. 摆出贡献
2. 通用框架
   1. 说明扩散模型的总体思想
   2. `DDPMs`的核心思想
   3. `NCSNs`的核心思想
   4. `SDEs`的核心思想
   5. 扩散模型与其他生成模型的关系
3. 分类
    这一章节按前面提到的四个维度对大量论文进行逐项概述。按分类下的发展过程逐项提及对应的论文，并用简短的语言概括每一篇文章的主要做法。从内容上这一章节占文章的主要篇幅
4. 总结与展望
   1. 梳理已有进展
   2. 指出当下研究存在的问题
   3. 说明未来可能的研究方向

## 总结启发

写一篇综述需要阅读的论文数量比想象中要多。但可以看出综述虽然提到的文章很多，但是对于每一篇文章并没有描写的太细致，基本都是一小段话总结一篇文章。针对每篇文章写出一小段总结理论上只需要略读就可以做到。但是要对整体方向有把握需要精读该方向的里程碑文章

从时间上，这篇综述主要是总结2022年以及之前的工作，这距离2020开始的扩散模型爆发仅仅过去了两年，而站在我准备撰写综述的2026时间节点，在“扩散模型”主题下的细分研究的数量应该已经非常多了，没有办法在一篇文章里面塞下，我在动笔前应当找到一个更加细化的方向，并且涉及的文章应当是近两三年内的，时间更早的研究早就有别人写过综述了，因此2024年之前的研究我应该只需要看里程碑文章即可，帮助把握整体方向，至于细分领域的研究仅看近两年的论文
