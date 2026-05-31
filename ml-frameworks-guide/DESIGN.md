# DESIGN.md — 机器学习框架指南视频

## Style Prompt
Data Drift (Refik Anadol 风格)。深黑背景上漂浮着电子紫与青色的数据流，科技感与沉浸感交织。文字稀疏精炼，字体纤细未来感。粒子聚合为信息，光线在帧间流动。整体氛围：在深空中阅读未来档案。

## Colors
- **Background**: `#0a0a0a` (deep black)
- **Foreground**: `#e8e8e8` (cool white)
- **Accent 1**: `#7c3aed` (electric purple)
- **Accent 2**: `#06b6d4` (cyan)
- **Muted**: `#3a3a3a` (cold grey)

## Typography
- **Headlines**: DM Sans, weight 800, tight tracking (-0.03em)
- **Body / Data**: IBM Plex Mono, weight 300, tabular-nums
- **Register**: Technical precision (mono) vs bold authority (display). DM Sans commands attention, IBM Plex Mono delivers data.

## Motion Rules
- Default easing: `sine.inOut` for ambient, `power2.out` for entrances, `power3.in` for exits
- Entrance speed: 0.4-0.7s (medium-slow, immersive)
- Ambient: slow scale pulse, position drift, opacity breathing
- Stagger: 0.08-0.15s between elements
- First animation offset: 0.2s minimum

## Transitions
- **Primary (60%)**: Grid Dissolve — 数据碎片化重组，契合ML主题
- **Accent (25%)**: Blur Crossfade — 流体过渡，沉浸感
- **Outro**: Color Dip to black — 收束感

## Background Layer
Every scene has:
1. Radial glow (purple or cyan tinted, breathing scale)
2. Ghost text (framework names at 4% opacity, large, slow drift)
3. Accent hairline rules with subtle pulse
4. Grid dot pattern at 3% opacity

## What NOT to Do
- No gradient text (banned AI tell)
- No purple-to-blue linear gradients
- No emoji
- No pure #000 or #fff
- No identical card grids repeated
- No Syne / Inter / Roboto / Poppins
- No exit animations except final scene
