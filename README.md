# Html2Video - AI Teaching Video Automation Platform

An AI teaching video automation platform using HyperFrames + GSAP, transforming AI fundamentals (linear algebra, machine learning, LLM principles) into high-quality visual educational videos with full "script→animation→voiceover→video" pipeline automation.

## 📦 Project Overview

### Completed Videos

| Video Name | Status | Description |
|------------|--------|-------------|
| **Python AI Tutorial** | ✅ | Python AI introductory tutorial |
| **ML Frameworks Guide** | ✅ | Introduction to mainstream machine learning frameworks |

## 🛠️ Tech Stack

- **HyperFrames**: HTML-based video synthesis framework
- **GSAP**: Animation library
- **CSS**: Styling and layout
- **KaTeX**: Mathematical formula rendering

## 📂 Project Structure

```
Html2Video/
├── python-ai-tutorial/       # Python AI Tutorial
│   ├── index.html
│   ├── DESIGN.md
│   └── script.txt
├── ml-frameworks-guide/      # ML Frameworks Guide
│   ├── index.html
│   ├── DESIGN.md
│   └── 机器学习主流框架指南.md
├── .gitignore
├── package.json
└── README.md
```

## 🚀 Quick Start

### Preview Video

```bash
cd <project-directory>
npx hyperframes preview
```

Click "Play" in the browser to view animations, or click scene buttons to jump to specific chapters.

### Render Output

```bash
# Quick preview
npx hyperframes render --quality draft

# Standard quality
npx hyperframes render --fps 30 --quality standard --output video.mp4

# High quality
npx hyperframes render --fps 60 --quality high --output video-hd.mp4
```

## 🎨 Visual Design Specs

- **Primary Background**: `#0D1117` (Dark Space Black)
- **Tech Blue**: `#00D4FF`
- **Purple**: `#A855F7`
- **Text**: `#F0F6FC`

See `DESIGN.md` in each subdirectory for details.

## 📖 Learning Suggestions

1. **Watch the full video first** to get the big picture
2. **Go scene by scene**: Click scene buttons to understand step by step
3. **Combine with code blocks**: The pseudo-code in the video helps understand algorithm flow

## 📄 License

MIT License
