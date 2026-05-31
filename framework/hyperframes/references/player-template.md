# 播放器预览模板

本模板用于生成可在浏览器中直接预览的 HTML 视频，包含播放控制和场景跳转功能。

## 核心特点

- **固定底部控制栏**：不遮挡主内容，位于视口最下方
- **场景跳转按钮**：点击可直接跳转到指定时间点
- **播放/暂停切换**：一键控制动画播放状态
- **顶部提示**：6秒后自动消失的操作提示

## 适用场景

当用户需要在浏览器中预览动画效果，或生成可交互的教学视频时使用此模板。

## 重要：底部留白 ⚠️

**播放器高度约 80-100px，必须为内容预留底部空间！**

场景的 `padding-bottom` 必须设置为 **至少 140px**，确保内容不被播放器遮挡：

```css
.scene {
  padding: 60px 80px 140px 80px; /* 顶部 左侧 底部(预留播放器空间) 右侧 */
  opacity: 0;
}
```

### 底部留白计算

- 播放器固定在 `bottom: 20px`
- 播放器内边距约 `16px * 2 = 32px`
- 按钮高度约 `10px * 2 + 36px ≈ 56px`
- **总占用高度 ≈ 108px**
- **建议 padding-bottom = 140px**（留有余量）

### 内容适配建议

为避免底部被遮挡，建议：

1. **调整字体大小**：标题 44-52px 即可，不需要太大
2. **减小卡片间距**：gap 从 32px 减至 20-24px
3. **精简内容**：每行显示 8-10 行代码，避免内容过密
4. **开场场景**：可单独设置更大的 `padding-bottom: 160px`

## HTML 结构

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>视频标题</title>
  <script src="https://cdn.jsdelivr.net/npm/gsap@3.14.2/dist/gsap.min.js"></script>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    
    body {
      font-family: 'Inter', 'SF Pro Display', system-ui, -apple-system, sans-serif;
      background: #0a0a0f;
      color: #f8fafc;
      overflow: hidden;
    }
    
    [data-composition-id="main"] {
      width: 100vw;
      height: 100vh;
      position: relative;
      background: #0a0a0f;
      overflow: hidden;
    }
    
    /* ===== 场景通用样式 ===== */
    /* ⚠️ 关键：padding-bottom 必须 >= 140px，预留底部播放器空间 */
    .scene {
      position: absolute;
      inset: 0;
      display: flex;
      flex-direction: column;
      padding: 60px 80px 140px 80px;
      opacity: 0;
    }
    
    .scene.active { opacity: 1; }
    
    .section-header { margin-bottom: 30px; flex-shrink: 0; }
    .section-number { font-size: 16px; color: #00d4ff; font-weight: 600; letter-spacing: 0.15em; margin-bottom: 10px; }
    .section-title { font-size: 44px; font-weight: 700; color: #f8fafc; line-height: 1.2; }
    .section-subtitle { font-size: 20px; color: #94a3b8; margin-top: 10px; }
    
    /* 首个场景使用 opacity: 1 */
    .scene:first-child { opacity: 1; }
    
    /* ===== 播放控制面板 ===== */
    .player-controls {
      position: fixed;
      bottom: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(30, 41, 59, 0.95);
      border: 1px solid #00d4ff;
      border-radius: 12px;
      padding: 14px 20px;
      display: flex;
      gap: 10px;
      z-index: 9999;
      font-family: system-ui, sans-serif;
      flex-wrap: wrap;
      max-width: 90vw;
      justify-content: center;
      backdrop-filter: blur(10px);
    }
    
    .play-btn {
      background: linear-gradient(135deg, #00d4ff, #7c3aed);
      border: none;
      border-radius: 8px;
      padding: 10px 20px;
      color: #0a0a0f;
      font-weight: 600;
      cursor: pointer;
      font-size: 14px;
    }
    
    .scene-btn {
      background: rgba(0, 212, 255, 0.1);
      border: 1px solid rgba(0, 212, 255, 0.3);
      border-radius: 6px;
      padding: 8px 14px;
      color: #00d4ff;
      cursor: pointer;
      font-size: 12px;
      transition: all 0.2s;
    }
    
    .scene-btn:hover {
      background: rgba(0, 212, 255, 0.2);
      border-color: #00d4ff;
    }
    
    /* ===== 顶部提示 ===== */
    .player-tip {
      position: fixed;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0, 212, 255, 0.1);
      border: 1px solid rgba(0, 212, 255, 0.3);
      border-radius: 8px;
      padding: 12px 20px;
      color: #00d4ff;
      font-size: 14px;
      z-index: 9999;
      text-align: center;
    }
  </style>
</head>
<body>
  <div data-composition-id="main" data-width="1920" data-height="1080" data-start="0" data-duration="90">
    
    <!-- 场景 1: 开场 (0-5s) -->
    <div class="scene" id="scene-intro">
      <!-- 内容 -->
    </div>
    
    <!-- 场景 2: 内容 (5-18s) -->
    <div class="scene" id="scene-content">
      <!-- 内容 -->
    </div>
    
  </div>
  
  <script>
    window.__timelines = window.__timelines || {};
    
    const tl = gsap.timeline({ paused: true });
    
    // ===== GSAP 动画 =====
    // 场景切换使用 opacity 控制
    // 首个场景默认 opacity: 1
    // 使用 tl.set() 配合 opacity: 1 来切换场景
    
    // 场景 2 (示例: 5s 开始)
    tl.set("#scene-content", { opacity: 1 }, 5)
      .from("#scene-content .section-header > *", { y: 30, opacity: 0, duration: 0.6, stagger: 0.1 }, 5.2)
      // ... 更多动画
      .to("#scene-intro", { opacity: 0, duration: 0.5 }, 4.5); // 前一场景淡出
    
    window.__timelines["main"] = tl;
    
    // ===== 浏览器预览播放器 =====
    if (!window.__hyperframes) {
      const controls = document.createElement('div');
      controls.className = 'player-controls';
      
      const playBtn = document.createElement('button');
      playBtn.className = 'play-btn';
      playBtn.textContent = '▶ 播放';
      
      // 场景列表（根据实际内容调整）
      const scenes = [
        { name: '开场', time: 0 },
        { name: '内容', time: 5 }
      ];
      
      let isPlaying = false;
      playBtn.onclick = () => {
        if (isPlaying) {
          tl.pause();
          playBtn.textContent = '▶ 播放';
        } else {
          tl.play();
          playBtn.textContent = '⏸ 暂停';
        }
        isPlaying = !isPlaying;
      };
      
      controls.appendChild(playBtn);
      
      scenes.forEach((scene, i) => {
        const btn = document.createElement('button');
        btn.className = 'scene-btn';
        btn.textContent = `${i + 1}. ${scene.name}`;
        btn.onclick = () => {
          tl.pause();
          tl.time(scene.time);
          playBtn.textContent = '▶ 播放';
          isPlaying = false;
        };
        controls.appendChild(btn);
      });
      
      document.body.appendChild(controls);
      
      // 顶部提示
      const tip = document.createElement('div');
      tip.className = 'player-tip';
      tip.textContent = '💡 点击「播放」查看完整动画，或点击场景按钮跳转查看特定章节';
      document.body.appendChild(tip);
      
      setTimeout(() => {
        tip.style.opacity = '0';
        tip.style.transition = 'opacity 0.5s';
      }, 6000);
    }
  </script>
</body>
</html>
```

## 关键实现要点

### 1. 场景切换机制

使用 `opacity: 0` 隐藏所有场景，通过 GSAP `tl.set()` 配合 `opacity: 1` 在指定时间显示场景：

```js
// 场景 1 淡出
tl.to("#scene-intro", { opacity: 0, duration: 0.5 }, 4.5);

// 场景 2 显示
tl.set("#scene-content", { opacity: 1 }, 5)
  .from("#scene-content .section-header > *", { y: 30, opacity: 0, duration: 0.6 }, 5.2);
```

### 2. 首个场景处理

第一个场景默认 `opacity: 1`，确保页面加载时可见：

```css
.scene:first-child { opacity: 1; }
```

### 3. ⚠️ 控制面板定位与底部留白

固定在底部，不遮挡主内容。**关键：场景的 padding-bottom 必须 >= 140px**：

```css
/* 场景容器 - 底部预留播放器空间 */
.scene {
  padding: 60px 80px 140px 80px; /* 顶部 左右 底部 */
}

/* 播放器控制栏 */
.player-controls {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 9999;
}
```

### 4. 场景时间同步

播放器跳转时间与 GSAP timeline 时间对齐：

```js
btn.onclick = () => {
  tl.pause();
  tl.time(scene.time);  // 跳转到指定时间
};
```

## 自定义建议

- **配色**：根据 DESIGN.md 的配色方案调整按钮和面板颜色
- **布局**：控制面板最大宽度 90vw，支持换行适应小屏幕
- **场景按钮**：根据实际场景数量和名称动态生成
- **提示内容**：根据视频主题调整提示文案
- **内容紧凑度**：为避免被底部播放器遮挡，建议标题 44-52px、代码行高 1.6-1.8、卡片间距 20-24px

## 完整示例

参考项目：`C:\Users\宿心\WorkBuddy\Html2Video\python-ai-tutorial\index.html`（已针对底部留白优化）
