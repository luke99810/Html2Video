# LLM Transformer 底层原理 - 详解版教学视频

一个使用 HyperFrames 制作的关于大语言模型底层原理的深度教学视频。

## 视频内容概览（90秒，7个场景）

| 章节 | 时间 | 核心内容 |
|------|------|----------|
| **开场** | 0-5s | 标题动画，四大主题预览 |
| **Token 详解** | 5-18s | BPE 分词算法、Embedding 向量、词表展示 |
| **Transformer** | 18-35s | Q/K/V 计算、位置编码、多头注意力、架构解析 |
| **数据准备** | 35-50s | 数据清洗流水线、自监督学习、Next Token Prediction |
| **预训练** | 50-68s | Batch 训练、损失函数、Scaling Law、训练成本 |
| **RLHF** | 68-82s | SFT、Reward Model、PPO 算法详解 |
| **总结** | 82-90s | 完整流程图、核心要点回顾 |

## 核心知识点详解

### 1. Token 化
- **BPE 算法**：Byte Pair Encoding，通过合并高频字符对构建词表
- **子词优势**：处理生僻词（如 "unhappiness" → "un" + "##hap" + "##pi" + "##ness"）
- **Embedding**：每个 Token 映射到高维向量（如 768 维），向量值代表语义特征
- **中英文差异**：英文约 1 Token/词，中文约 2-3 Token/字

### 2. Transformer 架构
- **自注意力机制**：Query · Key = Attention Score，决定关注哪些位置
- **位置编码**：正弦/余弦函数为每个位置生成独特"指纹"
- **多头注意力**：8-96 个头并行，捕捉不同特征（语法、语义、指代等）
- **残差连接**：Add & Norm 稳定深层网络训练

### 3. 数据准备
- **数据来源**：网页(Common Crawl)、书籍、论文、代码
- **清洗流程**：去重 → 过滤 → Token 化 → 构建训练样本
- **自监督学习**：Next Token Prediction，文本本身就是标签
- **训练样本**：`[我, 喜欢, 深度]` → 预测 `"学习"`

### 4. 预训练
- **损失函数**：交叉熵损失 `-log P(target_token | context)`
- **优化算法**：AdamW + 学习率预热 + 梯度裁剪
- **Scaling Law**：性能 ∝ 参数数^α × 数据量^β × 计算量^γ
- **训练成本**：GPT-3 约 $460万，GPT-4 估计 >$1亿

### 5. RLHF 对齐
- **SFT**：用高质量对话数据微调，学习指令遵循
- **Reward Model**：人类排序训练奖励模型，学习人类偏好
- **PPO**：强化学习优化策略，最大化奖励同时保持稳定性
- **评判维度**：有用性、真实性、无害性、流畅性

## 使用方法

### 预览视频
```bash
cd llm-transformer-tutorial
npx hyperframes preview
```

浏览器中点击「播放」查看动画，或点击场景按钮跳转到特定章节。

### 渲染输出
```bash
# 快速预览
npx hyperframes render --quality draft

# 标准质量
npx hyperframes render --fps 30 --quality standard --output llm-tutorial.mp4

# 高清版本
npx hyperframes render --fps 60 --quality high --output llm-tutorial-hd.mp4
```

## 项目结构

```
llm-transformer-tutorial/
├── index.html      # 主视频文件（7 场景，90秒）
├── DESIGN.md       # 视觉设计规范
└── README.md       # 本文件
```

## 自定义修改

### 修改内容
直接编辑 `index.html` 中的文本、代码块、公式等。

### 调整时间
编辑 `<script>` 中的 GSAP 时间线：
```javascript
// 修改场景开始时间
tl.set("#scene-token", { opacity: 1 }, 5)  // 第5秒开始

// 修改动画持续时间
duration: 0.8  // 改为 1.0 秒
```

### 添加配音
```bash
# 生成 AI 配音
npx hyperframes tts "Token 是模型的字母表..." --voice af_nova --output narration.wav
```

## 技术栈

- **HyperFrames**: HTML-based 视频合成框架
- **GSAP**: 动画库
- **CSS**: 样式和布局

## 学习建议

1. **先看一遍完整视频**了解全貌
2. **逐场景细看**：点击场景按钮（1.Token → 2.Transformer...）逐个理解
3. **结合代码块**：视频中的伪代码帮助理解算法流程
4. **参考外部资料**：
   - [Attention Is All You Need](https://arxiv.org/abs/1706.03762) - Transformer 原论文
   - [Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) - 可视化讲解
   - [RLHF 论文](https://arxiv.org/abs/2203.02155) - 训练语言模型遵循人类反馈

---

制作日期: 2026-04-18
版本: 2.0（详解版）
