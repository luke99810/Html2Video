# Html2Video - AI Teaching Video Automation Platform

An AI teaching video automation platform using HyperFrames + GSAP, transforming AI fundamentals into high-quality visual educational videos with full "script→animation→voiceover→video" pipeline automation.

## 📦 Project Structure

```
Html2Video/
├── framework/                    # Core Framework
│   ├── hyperframes/              # Main HyperFrames framework
│   │   ├── SKILL.md             # Core skill definition
│   │   ├── visual-styles.md     # Visual style guide
│   │   ├── patterns.md          # Design patterns
│   │   ├── house-style.md       # House style guide
│   │   ├── data-in-motion.md    # Data visualization
│   │   ├── palettes/            # Color palettes
│   │   └── references/          # Technical references
│   │       ├── typography.md
│   │       ├── transitions.md
│   │       ├── captions.md
│   │       ├── tts.md
│   │       ├── audio-reactive.md
│   │       ├── player-template.md
│   │       └── ...
│   ├── gsap/                    # GSAP animation reference
│   │   ├── SKILL.md
│   │   └── references/
│   │       └── effects.md
│   ├── hyperframes-cli/         # CLI command tool
│   │   └── SKILL.md
│   ├── hyperframes-registry/    # Component registry
│   │   ├── SKILL.md
│   │   ├── examples/
│   │   └── references/
│   └── website-to-hyperframes/  # Web to video conversion
│       ├── SKILL.md
│       └── references/
├── python-ai-tutorial/          # Example: Python AI Tutorial
│   ├── index.html
│   ├── DESIGN.md
│   └── script.txt
└── ml-frameworks-guide/         # Example: ML Frameworks Guide
    ├── index.html
    ├── DESIGN.md
    └── 机器学习主流框架指南.md
```

## 🛠️ Tech Stack

- **HyperFrames**: HTML-based video synthesis framework
- **GSAP**: Professional animation library
- **CSS**: Styling and layout
- **KaTeX**: Mathematical formula rendering

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

## 📚 Framework Modules

### hyperframes
The main framework providing core video composition capabilities with HTML-based approach.

### hyperframes-cli
Command-line interface tool for streamlined video generation workflow.

### hyperframes-registry
Component registry system for managing and reusing video building blocks.

### website-to-hyperframes
Conversion toolkit for transforming web content into HyperFrames video format.

### gsap
Animation reference library with professional effects and transitions.

## 📖 Learning Suggestions

1. **Start with the Framework**: Read `framework/hyperframes/SKILL.md` to understand core concepts
2. **Explore Examples**: Check `python-ai-tutorial` or `ml-frameworks-guide` for reference
3. **Customize**: Use palettes and visual styles to create your own video themes

## 📄 License

MIT License
