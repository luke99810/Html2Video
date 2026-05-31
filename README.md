# Html2Video - AI 教学视频自动制作

基于 HyperFrames + GSAP 的 AI 教学视频自动化制作平台。将 AI 基础知识（线性代数、机器学习、大模型原理等）转化为高质量的可视化教学视频，实现「脚本→动画→配音→视频」全流程自动化。

## 📦 项目概览

### 已完成视频

| 视频名称 | 状态 | 说明 |
|----------|------|------|
| **AI 数学基础** | ✅ | 涵盖数学基础知识，公式动画渲染 |
| **LLM Transformer 教程** | ✅ | 详解版教学视频，90秒，7个场景 |
| **Python AI 教程** | ✅ | Python AI 入门教程 |
| **机器学习框架指南** | ✅ | 主流机器学习框架介绍 |
| **AI Agent 面试指南** | ✅ | AI Agent 相关面试准备 |

## 🛠️ 技术栈

- **HyperFrames**: HTML-based 视频合成框架
- **GSAP**: 动画库
- **CSS**: 样式和布局
- **KaTeX**: 数学公式渲染

## 📂 项目结构

```
Html2Video/
├── ai-math-foundations/        # AI 数学基础
│   ├── index.html
│   ├── DESIGN.md
│   └── script.txt
├── llm-transformer-tutorial/   # LLM Transformer 教程
│   ├── index.html
│   ├── DESIGN.md
│   └── README.md
├── python-ai-tutorial/         # Python AI 教程
│   ├── index.html
│   ├── DESIGN.md
│   └── script.txt
├── ml-frameworks-guide/        # 机器学习框架指南
│   ├── index.html
│   ├── DESIGN.md
│   └── 机器学习主流框架指南.md
└── ai-agent-interview-guide/   # AI Agent 面试指南
    └── index.html
```

## 🚀 快速开始

### 预览视频

```bash
cd <项目目录>
npx hyperframes preview
```

浏览器中点击「播放」查看动画，或点击场景按钮跳转到特定章节。

### 渲染输出

```bash
# 快速预览
npx hyperframes render --quality draft

# 标准质量
npx hyperframes render --fps 30 --quality standard --output video.mp4

# 高清版本
npx hyperframes render --fps 60 --quality high --output video-hd.mp4
```

## 🎨 视觉设计规范

- **主背景色**: `#0D1117` (深邃夜空黑)
- **科技蓝**: `#00D4FF`
- **紫色**: `#A855F7`
- **文字**: `#F0F6FC`

详见各子目录的 `DESIGN.md` 文件。

## 📖 学习建议

1. **先看一遍完整视频**了解全貌
2. **逐场景细看**：点击场景按钮逐个理解
3. **结合代码块**：视频中的伪代码帮助理解算法流程

## 📄 许可证

MIT License
