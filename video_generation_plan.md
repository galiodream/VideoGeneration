# 8周可控视频生成学习路线

## 目标

在 8 周内完成一条从 **视频生成基础** 到 **可控视频生成项目原型** 的压缩学习路线。  
最终目标不是“看完综述”，而是形成下面三类能力：

1. 理解视频生成底座：Diffusion / Flow / AR，UNet / DiT / AR-based video models  
2. 理解可控视频生成核心：结构控制、时间/运动控制、reference consistency、多条件控制  
3. 做出 2 个完整项目 + 1 个增强原型：
   - 项目 1：Pose / Depth Controlled Video Demo
   - 项目 2：Reference-based Character Consistency Demo
   - 项目 3：Multi-shot / Multi-condition Controlled Video Prototype

---

## 总体学习主线

这份路线以综述 **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 为主线地图，按下面顺序推进：

**基础生成模型 → 视频 foundation models → 控制信号注入 → 结构控制 / 一致性 / 多条件控制 → 编辑与工程化 → 长视频 / 系统化补充**

核心原则：

- 用综述搭知识框架
- 用代表论文补关键方法
- 用博客和官方文档补直觉
- 用开源项目把理解落到代码和实验上

---

# 一、核心资料总表

## 1. 主线必读资料

- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)**  
  作用：总路线图，梳理 controllable video generation 的基础、控制机制、分类、应用和未来方向。

- **[Lilian Weng: Diffusion Models for Video Generation](https://lilianweng.github.io/posts/2024-04-12-diffusion-video/)**  
  作用：帮助建立视频扩散模型直觉，理解视频比图像难在哪里。

- **[Diffusers: Text-to-Video 文档](https://huggingface.co/docs/diffusers/en/api/pipelines/text_to_video)**  
  作用：快速跑通视频生成 pipeline。

- **[Diffusers: AnimateDiff 文档](https://huggingface.co/docs/diffusers/api/pipelines/animatediff)**  
  作用：理解 MotionAdapter / Motion Module 如何给图像扩散模型加入视频能力。

- **[Hugging Face 博客：State of open video generation models in Diffusers](https://huggingface.tw/blog/video_gen)**  
  作用：了解当前开源视频模型生态。

---

## 2. 代表论文 / 博客 / 方法资料

### 视频底座

- **[AnimateDiff (paper)](https://arxiv.org/abs/2307.04725)**
- **[AnimateDiff (GitHub)](https://github.com/guoyww/AnimateDiff)**

- **[Open Diffusion Models for High-Quality Video Generation / VideoCrafter (paper)](https://arxiv.org/abs/2310.19512)**
- **[VideoCrafter (GitHub)](https://github.com/ailab-cvc/videocrafter)**

- **[CogVideoX (GitHub)](https://github.com/zai-org/CogVideo)**

- **[LTX-Video (GitHub)](https://github.com/Lightricks/LTX-Video)**

- **[Open-Sora (GitHub)](https://github.com/hpcaitech/Open-sora)**
- **[Open-Sora 1.2 Report](https://github.com/hpcaitech/Open-Sora/blob/main/docs/report_03.md)**

### 控制 / 编辑 / 一致性

- **[Hugging Face: ControlNet 博客](https://huggingface.co/blog/controlnet)**
- **[Hugging Face: Text2Video / Text2Video-Zero 博客](https://huggingface.co/blog/text-to-video)**

- **[Conditional Image Leakage in I2V Diffusion Models](https://arxiv.org/html/2406.15735v1)**
- **[cond-image-leakage (GitHub)](https://github.com/thu-ml/cond-image-leakage)**

- **[Runway Gen-4 研究页](https://runwayml.com/research/introducing-runway-gen-4)**
- **[Runway Gen-4.5 研究页](https://runwayml.com/research/introducing-runway-gen-4.5)**

### 长视频 / 效率 / 系统化

- **[FreeNoise (GitHub)](https://github.com/AILab-CVC/FreeNoise)**
- **[TeaCache for LTX-Video README](https://github.com/ali-vilab/TeaCache/blob/main/TeaCache4LTX-Video/README.md)**

---

## 3. 开源项目优先级

### 第一优先
- **[Diffusers Text-to-Video](https://huggingface.co/docs/diffusers/en/api/pipelines/text_to_video)**
- **[AnimateDiff](https://github.com/guoyww/AnimateDiff)**

适合：
- 跑第一个视频生成 demo
- 理解 MotionAdapter / Motion Module
- 理解 pipeline 结构

### 第二优先
- **[VideoCrafter](https://github.com/ailab-cvc/videocrafter)**

适合：
- text2video / image2video
- 控制与编辑实验
- 做更完整 demo

### 第三优先
- **[CogVideoX](https://github.com/zai-org/CogVideo)**

适合：
- 接触更现代的大型开源视频底模
- 理解 DiT 风格 video generation

### 第四优先
- **[LTX-Video](https://github.com/Lightricks/LTX-Video)**

适合：
- 理解高效、生产感更强的视频模型路线

### 第五优先
- **[Open-Sora](https://github.com/hpcaitech/Open-sora)**

适合：
- 读系统设计
- 补训练与工程视角

---

# 二、8 周详细路线

## 第 1 周：视频生成底座入门

### 本周目标
建立视频生成基础认知，弄清视频生成和图像生成的区别。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 的基础部分与 video foundation models 部分
- **[Lilian Weng: Diffusion Models for Video Generation](https://lilianweng.github.io/posts/2024-04-12-diffusion-video/)**
- **[Diffusers: Text-to-Video 文档](https://huggingface.co/docs/diffusers/en/api/pipelines/text_to_video)**

### 本周建议读
- **[AnimateDiff (paper)](https://arxiv.org/abs/2307.04725)**
- **[Open Diffusion Models for High-Quality Video Generation / VideoCrafter (paper)](https://arxiv.org/abs/2310.19512)**

### 本周上手项目
- **[Diffusers Text-to-Video](https://huggingface.co/docs/diffusers/en/api/pipelines/text_to_video)**
- **[AnimateDiff](https://github.com/guoyww/AnimateDiff)**

### 本周完成内容
1. 跑通一个最小 text-to-video demo  
2. 跑通一个 AnimateDiff demo  
3. 自己画出一张视频生成模型草图  
4. 总结：
   - 视频为什么比图像难
   - 什么是 temporal consistency
   - UNet-based / DiT-based / AR-based 大致区别

### 本周交付物
- 一份 2 页笔记
- 一个最小推理 demo
- 一张模型结构草图

---

## 第 2 周：控制信号如何注入模型

### 本周目标
理解“控制”不是简单多喂一个输入，而是控制信号如何进入 denoising / generative process。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 中 control mechanisms 相关部分
- **[Hugging Face: ControlNet 博客](https://huggingface.co/blog/controlnet)**
- **[Diffusers: AnimateDiff 文档](https://huggingface.co/docs/diffusers/api/pipelines/animatediff)**

### 本周建议读
- **[Hugging Face: Text2Video / Text2Video-Zero 博客](https://huggingface.co/blog/text-to-video)**

### 本周上手项目
- **[AnimateDiff](https://github.com/guoyww/AnimateDiff)**
- **[VideoCrafter](https://github.com/ailab-cvc/videocrafter)**

### 本周完成内容
1. 总结控制信号注入方式：
   - condition encoder
   - feature injection
   - adapter / residual branch
   - cross-attention conditioning
2. 对比两种控制信号：
   - pose
   - depth
3. 找一个支持 controllable video 的 repo，理清输入输出流程

### 本周交付物
- 一张“控制信号注入方式对比表”
- 一个最小对比实验：
  - 无控制
  - 有 pose / depth 控制

---

## 第 3 周：项目 1 原型——结构控制视频生成

### 本周目标
做出第一个真正可展示的 controllable video 原型。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 中 single-condition / structure control 相关部分
- **[Hugging Face: ControlNet 博客](https://huggingface.co/blog/controlnet)**

### 本周建议读
- **[Hugging Face: Text2Video / Text2Video-Zero 博客](https://huggingface.co/blog/text-to-video)**
- **[AnimateDiff (paper)](https://arxiv.org/abs/2307.04725)**

### 本周上手项目
优先二选一：
- AnimateDiff + pose/depth 预处理
- VideoCrafter + 结构控制实验

### 本周完成内容
1. 选一个主控制：
   - pose
   - 或 depth
2. 构建最小原型：
   - 输入参考图 / 起始帧
   - 输入 pose / depth 条件
   - 输出 3~5 秒视频
3. 做至少 3 组 case

### 本周交付物
- 项目 1 v1
- 3 组实验结果
- 控制信号可视化
- 简单失败案例记录

---

## 第 4 周：完善项目 1 + 补评测意识

### 本周目标
把项目 1 从“能跑”推进到“像作品”。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 中 structure / temporal control 相关部分
- **[Hugging Face 博客：State of open video generation models in Diffusers](https://huggingface.tw/blog/video_gen)**

### 本周建议读
- **[VideoCrafter (GitHub)](https://github.com/ailab-cvc/videocrafter)**
- **[Lilian Weng: Diffusion Models for Video Generation](https://lilianweng.github.io/posts/2024-04-12-diffusion-video/)**

### 本周上手项目
继续打磨：
- AnimateDiff
- 或 VideoCrafter

### 本周完成内容
1. 补 5~10 个测试样例
2. 做 2 组对比：
   - 控制强度变化
   - 不同 prompt 下控制是否有效
3. 分析失败场景：
   - 快速动作
   - 遮挡
   - 大视角变化
4. 初步考虑评测维度：
   - 控制命中
   - 闪烁
   - 结构漂移

### 本周交付物
- 项目 1 完整版
- 一组系统对比实验
- 一份失败分析总结

---

## 第 5 周：项目 2 原型——角色一致性

### 本周目标
进入更有价值的一层：reference-based consistency。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 中更细粒度控制 / multi-condition 相关部分
- **[Runway Gen-4 研究页](https://runwayml.com/research/introducing-runway-gen-4)**

### 本周建议读
- **[Conditional Image Leakage in I2V Diffusion Models](https://arxiv.org/html/2406.15735v1)**
- **[VideoCrafter (GitHub)](https://github.com/ailab-cvc/videocrafter)**

### 本周上手项目
优先：
- **[VideoCrafter](https://github.com/ailab-cvc/videocrafter)**

如果机器条件允许，也可开始接触：
- **[CogVideoX](https://github.com/zai-org/CogVideo)**

### 本周完成内容
1. 做 reference-based character consistency 最小原型：
   - 同一个角色参考图
   - 2~3 个镜头 / 角度
2. 观察是否能保持：
   - 脸部
   - 发型
   - 衣服主色
   - 主体身份特征
3. 开始记录 reference consistency 和 motion 之间的冲突

### 本周交付物
- 项目 2 v1
- 同角色多镜头结果
- 一份“哪里保持住，哪里漂了”的总结

---

## 第 6 周：多镜头一致性 + 条件冲突

### 本周目标
把项目 2 从“参考图视频生成”升级为“多镜头一致性 demo”。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 中 multi-condition / universal controllable generation 相关部分
- **[Runway Gen-4.5 研究页](https://runwayml.com/research/introducing-runway-gen-4.5)**

### 本周建议读
- **[Conditional Image Leakage in I2V Diffusion Models](https://arxiv.org/html/2406.15735v1)**
- **[Open-Sora 1.2 Report](https://github.com/hpcaitech/Open-Sora/blob/main/docs/report_03.md)**

### 本周上手项目
- **[VideoCrafter](https://github.com/ailab-cvc/videocrafter)**
- **[CogVideoX](https://github.com/zai-org/CogVideo)**

### 本周完成内容
1. 做一个 3-shot 小序列：
   - Shot A：正面中景
   - Shot B：侧面近景
   - Shot C：动作变化 / 轻微 camera movement
2. 加入简单镜头控制或动作约束
3. 理解三者冲突：
   - 身份一致性
   - 动作自由度
   - 镜头变化

### 本周交付物
- 项目 2 完整版
- 一个 3-shot 小样片
- 一份“控制冲突”分析

---

## 第 7 周：项目 3 原型——多条件控制

### 本周目标
做最有价值的雏形：multi-condition controllable video prototype。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 中 multi-condition 与 future directions 相关部分
- **[LTX-Video (GitHub)](https://github.com/Lightricks/LTX-Video)**

### 本周建议读
- **[Open-Sora (GitHub)](https://github.com/hpcaitech/Open-sora)**
- **[Open-Sora 1.2 Report](https://github.com/hpcaitech/Open-Sora/blob/main/docs/report_03.md)**

### 本周上手项目
根据重心选择：
- 更偏 demo：VideoCrafter / CogVideoX
- 更偏系统理解：LTX-Video / Open-Sora

### 本周完成内容
做一个最小多条件原型，输入至少包括两类条件：
- 角色参考图
- camera instruction / shot list
- 结构或动作条件（三选二）

推荐任务：  
> 给定一个角色参考图，让角色从站立到转身再走出画面，镜头从中景切到近景再切到侧面。

### 本周交付物
- 项目 3 v1
- 一个多条件 3-shot 原型
- 一份“哪些条件最难同时满足”的总结

---

## 第 8 周：补长视频 / 评测 / 系统感

### 本周目标
把前 7 周做的东西放回更完整的大图景里，并补长视频与系统化视角。

### 本周必读
- **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)** 中应用与未来方向部分
- **[Open-Sora 1.2 Report](https://github.com/hpcaitech/Open-Sora/blob/main/docs/report_03.md)**

### 本周建议读
- **[FreeNoise (GitHub)](https://github.com/AILab-CVC/FreeNoise)**
- **[Hugging Face 博客：State of open video generation models in Diffusers](https://huggingface.tw/blog/video_gen)**
- **[TeaCache for LTX-Video README](https://github.com/ali-vilab/TeaCache/blob/main/TeaCache4LTX-Video/README.md)**

### 本周上手项目
按兴趣补一个方向：
- 长视频：FreeNoise
- 速度和效率：LTX-Video + TeaCache

### 本周完成内容
1. 回看你前 7 周的成果，整理成能力链：
   - 单条件 controllable generation
   - reference consistency
   - 多条件控制
   - 长视频 / 系统化补充
2. 补系统理解：
   - evaluation
   - conditioning
   - efficiency
3. 确定后续长期分叉方向：
   - 更偏 controllable video
   - 更偏 video editing
   - 更偏 world model / embodied / agentic pipeline

### 本周交付物
- 三个项目的最终整理版
- 一页能力地图
- 一份后续深挖方向清单

---

# 三、8 周结束后应具备的能力结构

## 1. 生成底层
- diffusion
- flow matching
- AR
- latent video modeling

## 2. 视频建模
- spatial-temporal attention
- motion module
- temporal consistency
- long-range dependency

## 3. 可控视频生成
- structure control
- motion / temporal control
- reference / identity consistency
- multi-condition control

## 4. 工程与系统化
- 开源视频模型上手能力
- 基本实验对比意识
- 失败案例分析
- 长视频 / 加速 / 评测初步理解

---

# 四、最终建议的执行优先级

如果时间很紧，只保留这条主线：

1. **[Controllable Video Generation: A Survey](https://arxiv.org/abs/2507.16869)**
2. **[Lilian Weng: Diffusion Models for Video Generation](https://lilianweng.github.io/posts/2024-04-12-diffusion-video/)**
3. **[Diffusers Text-to-Video](https://huggingface.co/docs/diffusers/en/api/pipelines/text_to_video)**
4. **[AnimateDiff](https://github.com/guoyww/AnimateDiff)**
5. **[VideoCrafter](https://github.com/ailab-cvc/videocrafter)**
6. **[Conditional Image Leakage in I2V Diffusion Models](https://arxiv.org/html/2406.15735v1)**
7. **[CogVideoX](https://github.com/zai-org/CogVideo)**
8. **[LTX-Video](https://github.com/Lightricks/LTX-Video)** 或 **[Open-Sora](https://github.com/hpcaitech/Open-sora)**

一句话总结这 8 周路线：

**先用综述和博客建立视频生成与可控生成全景认知，再用 Diffusers + AnimateDiff 跑通最小视频生成，再用 VideoCrafter / CogVideoX 做结构控制和 reference consistency，最后补多条件控制、长视频和系统化视角。**
