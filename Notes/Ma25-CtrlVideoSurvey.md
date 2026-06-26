# Note: Ma25-CtrlVideoSurvey

论文全名：Controllable Video Generation: A Survey

解读参考：[最新综述 | 不止于文本：一文读懂“可控视频生成”技术全景](https://zhuanlan.zhihu.com/p/1931683819209090184)

## 写作动机

现有视频生成综述缺少以各类控制信号为核心、完整统一梳理全品类可控视频生成的体系化综述，填补以控制模态为分类主线的视频生成综述空白。

## 文章结构

1. 基础预备知识：五大生成范式（GAN/VAE/流模型/扩散/自回归）原理、文献筛选PRISMA流程、完整六层研究框架
2. 主流视频大模型汇总：UNet扩散、DiT扩散、自回归视频底座对比
3. 七大类单条件可控生成（核心分类）
4. 多条件融合&通用统一可控生成
5. 可控视频落地下游技术任务与行业应用
6. 当前技术局限与三大未来前沿研究方向
7. 全文总结

## 分类逻辑

1. 顶层一级分类（核心划分依据：输入控制模态）共7大类：结构控制、身份ID控制、图像参考控制、时序运动控制、音频驱动控制、其他小众控制、多模态通用统一控制
2. 中层技术范式划分（模型架构路线）：UNet扩散、DiT扩散、自回归AR、混合架构
3. 底层实现细分（条件注入方式）：ControlNet/Adapter插件、跨注意力条件编码、时序运动模块、专用特征编码器、推理无梯度引导

> Within this comprehensive framework, we adopt control modality as our primary taxonomic dimension for three reasons. First, the type of control signal fundamentally determines the architectural design choices, conditioning mechanisms, and technical challenges in video generation pipelines. Second, existing research efforts are predominantly organized around specific control types such as pose-guided animation or audio-driven synthesis, making this classification naturally align with the current literature structure.Third, control modalities serve as the critical bridge between user intent (expressed through various input forms) and the generated visual content. As shown in Fig. 4, we systematically categorize controllable video generation methods into seven modality classes: (1) Structure Control(e.g., pose, depth, sketch, bounding boxes), (2) ID Control (person or subject identity), (3) Image Control (reference images), (4) Temporal Control(flow, trajectory, camera, motion), (5) Audio Control (voice and sound), (6) Other Control (text rendering, style, points, BEV), and (7) Universal Control (multi-condition integration).

## 内容梳理

### 1. 引言

1. 行业痛点
2. 过往综述短板
3. 本文核心贡献：
    - 以控制信号为核心搭建完整分层分类体系
    - 梳理GAN/VAE/流匹配/扩散/自回归五大生成范式原理
    - 落地场景与现存缺陷

### 2. 前置预备知识

1. 五大生成模型拆解：GAN、VAE、DDPM、流模型&流匹配、自回归
2. 文献筛选流程（其实我不是很明白为什么要写这个）
3. 六层全域研究框架
4. 主流视频底座汇总：
    - UNet扩散：LVDM、AnimateDiff、Stable Video Diffusion
    - DiT扩散：CogVideoX、HunyuanVideo、StepVideo、Wan
    - 自回归：CausVid、NOVA、Cosmos、MAGI-1

### 3. 七大单条件可控生成（主体章节）

#### 3.1 结构空间控制

输入空间几何约束，细分5小类：

1. 姿态引导
2. 深度引导
3. 人脸关键点引导
4. 草图引导
5. 包围盒BBox控制

#### 3.2 ID主体身份控制

保证人物/物体跨帧外观不变，分人物人像、通用物体两类：

- 人像：ID-Animator、ConsisID，分微调LoRA/零调频域分解两条路线
- 多物体：VideoBooth、DisenStudio，解决多主体特征混淆、属性绑定冲突

#### 3.3 参考图像控制

以单张参考图为基底生成动态视频

#### 3.4 时序运动控制

管控镜头、物体运动轨迹，4个子类：

1. 光流引导：MOFA-Video、I2VControl，保证帧间平滑位移
2. 轨迹拖拽：DragAnything、TrailBlazer，用户手绘路径控制物体移动
3. 相机控制：Pan/Tilt/Dolly镜头，CameraCtrl、ViewCrafter，约束3D视锥一致性
4. 语义动作引导：舞蹈、行走等完整行为MotionBooth

#### 3.5 音频驱动控制

分语音人像、通用音画同步两条线：

1. 语音唇形动画
2. 音乐/环境音

#### 3.6 其他小众控制

风格迁移、文本渲染、点轨迹、BEV鸟瞰图，对应StyleMaster、TextAnimator、Panacea

#### 3.7 通用多条件统一控制

单框架兼容任意多类输入：

1. UNet路线：VideoComposer，时空条件编码器融合多信号
2. DiT路线：FullDiT、VACE，时空注意力统一处理全部条件
3. 自回归路线：InfinityStar，全部条件统一离散token序列化
核心难题：多控制信号权重失衡、互相冲突、长时序联合一致性差

### 4. 下游技术任务&产业应用

1. 技术任务层：视频补全/修复、视频合成、视频转4D、世界仿真
2. 落地场景层：影视广告、数字人元宇宙、自动驾驶仿真、机器人具身智能、教育内容创作

### 5. 现存局限与未来三大方向

1. 统一多条件约束编排：现有模型大多偏重单一控制，多条件融合易互相抵消，需要分层自适应权重、冲突消解模块化架构
2. 大语言+视频生成联合推理：LLM做高层创意拆解，自动生成姿态/相机/音频底层控制信号，解决复杂自然语言精准生成
3. 扩散+自回归混合长视频架构：扩散保证单帧画质，自回归强化长时序连贯，搭配稀疏注意力降低显存开销

### 6. 全文总结

系统梳理五大生成范式、七大类控制模态、主流视频底座；完整对比单条件、多条件、通用可控技术优劣；明确可控视频生成当前瓶颈与产业化落地路径

## 总结启发

越发觉得围绕可控/条件化生成相关的赛道来写会比较有说法

这篇文章有点奇妙的是真的要写自己是怎么筛文章的吗？
