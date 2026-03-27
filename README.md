# OpenDrumScribe: The Pragmatic Drum Transcription Workflow 🥁
[English](#english) | [简体中文](#简体中文)

---

## 简体中文

本项目是一套务实、高效、零成本的架子鼓扒谱与 MIDI 生成工作流。

市面上多数号称“一键音频转 MIDI”的 AI 工具，在面对架子鼓（无固定音高打击乐）时，往往会产生大量错位、漏判和 BPM 混乱。与其陷入修复 AI 乱码的泥潭，本项目主张采用更符合音频工程逻辑的**实战降维打击方案**。

根据你的目标音频类型，本工作流分为两条明确的路径：

### 🛣️ 路径一：商业发行歌曲 (降维打击工作流)

如果你需要扒取的歌曲是已经在网络上发行的知名曲目，**请彻底放弃使用 AI 识别音频**。直接利用开源社区的力量获取由专业人类乐手制作的完美源文件。

**所需工具：**
* **数据源:** [Songsterr](https://www.songsterr.com/)
* **提取器:** [Songsterr Downloader](https://songsterr-downloader.com/) (开源免登录解析工具)
* **宿主软件:** FL Studio 或任何主流 DAW

**实操步骤：**
1. **获取源链接:** 在 Songsterr 搜索目标歌曲，复制该曲谱页面的浏览器网址 (URL)。
2. **免付费下载:** 打开 Songsterr Downloader，粘贴网址，直接下载该歌曲的 MIDI 格式或 `.gp` 源文件。
3. **导入 DAW 与避坑:**
   * 将 MIDI 文件拖入 FL Studio 的通道机架底部。**务必勾选 "Import to different channels"（导入至不同通道）**，以防乐器混叠。
   * 找到名称中带有 "Track 10", "Drums" 或 "Perc" 的第 10 通道（General MIDI 标准打击乐通道）。
   * 将该通道的音符全选并剪切，粘贴至你的专业鼓机插件（如 FPC）中。
4. **人工微调 (Mapping):**
   * 对照通用标准微调偶尔错位的按键：底鼓(C3/36)、军鼓(D3/38)、闭镲(F#3/42)、**开镲(A#3或Bb3/46)**。

---

### 🛣️ 路径二：未知音频/自制音频 (AI 提纯 + 触发器工作流)

如果你处理的是完全没有现成谱子的自录音频或极小众歌曲，请使用本工作流。它摒弃了极不稳定的 AI 转谱模型，采用“先无损提纯，再利用 DAW 实时触发”的工业级方案。

#### Stage 1: 纯鼓声提取 (The Extractor)
目标：剥离伴奏与人声，获取极其干净的纯鼓点 `.wav` 文件。

* **[Colab 纯鼓声提取脚本](./Colab-Drum-Extractor.ipynb) (推荐):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/AI-Drum-Transcriber-Workflow/blob/main/Colab-Drum-Extractor.ipynb)
  * 利用云端免费 GPU 运行 Demucs v4 模型，不吃本地配置。
* **[UVR5](https://github.com/Anjok07/ultimatevocalremovergui) (本地高配):** 顶级的本地音轨分离工具（需 GTX 1060 6GB 以上显卡）。
* **[X-Minus Pro](https://x-minus.pro/ai) (极简网页端):** 免安装直接可用，每日免费额度约十几分钟。

#### Stage 2: 鼓触发器实时转录 (Audio Trigger Workflow)
*(🚧 内容建设中 / Under Construction)*

> **技术预告:** 本模块将放弃传统的 Python 生成静态 MIDI 方案，转而记录如何使用 DAW 内部的“鼓触发器”插件（如 KTDrumTrigger 或 DSP Trigger Free）。通过在混音台设置频段阈值，让纯鼓声音频实时、精准地将瞬态转化为标准 MIDI 信号并录制入鼓机。

---

## English

This project is a pragmatic, efficient, and zero-cost drum transcription and MIDI generation workflow.

Most "one-click audio-to-MIDI" AI tools struggle heavily with unpitched percussion like drums, resulting in misaligned notes, missed ghost notes, and chaotic BPMs. Instead of fixing AI-generated garbage, this project advocates for **battle-tested audio engineering workflows**.

Choose your path based on your target audio:

### 🛣️ Path 1: Commercial / Known Tracks (The Bypass Workflow)

If you are transcribing a known, released song, **abandon AI audio recognition entirely**. Leverage the open-source community to grab perfect source files created by professional human musicians.

**Tools:**
* **Source:** [Songsterr](https://www.songsterr.com/)
* **Extractor:** [Songsterr Downloader](https://songsterr-downloader.com/) (Open-source parser)
* **DAW:** FL Studio or any standard DAW

**Steps:**
1. **Get URL:** Search for your song on Songsterr and copy the page URL.
2. **Bypass & Download:** Paste the URL into Songsterr Downloader and download the MIDI or `.gp` file directly.
3. **DAW Import & Routing:**
   * Drag the MIDI into the bottom of the FL Studio Channel Rack. **Crucial: Check "Import to different channels"** to prevent instrument overlapping.
   * Locate Channel 10 (named "Track 10", "Drums", or "Perc"), which is the General MIDI standard for percussion.
   * Cut all notes from this track and paste them into your dedicated drum machine plugin (e.g., FPC).
4. **Mapping Tweaks:**
   * Adjust any stray notes to standard GM mapping: Kick (C3/36), Snare (D3/38), Closed Hi-hat (F#3/42), **Open Hi-hat (A#3 or Bb3/46)**.

---

### 🛣️ Path 2: Unknown / Original Audio (AI Extraction + Trigger Workflow)

Use this workflow for self-recorded tracks or obscure audio with no existing tabs. It abandons unstable AI transcription models in favor of a "lossless extraction followed by real-time DAW triggering" industrial approach.

#### Stage 1: Pure Drum Extraction
Goal: Strip away backing tracks and vocals to obtain a perfectly clean `.wav` file of only the drums.

* **[Colab Drum Extractor Script](./Colab-Drum-Extractor.ipynb) (Recommended):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/AI-Drum-Transcriber-Workflow/blob/main/Colab-Drum-Extractor.ipynb)
  * Uses free cloud GPUs to run the Demucs v4 model. Perfect for low-spec PCs.
* **[UVR5](https://github.com/Anjok07/ultimatevocalremovergui) (Local Heavy-Duty):** Top-tier local stem separation (Requires GTX 1060 6GB VRAM or higher).
* **[X-Minus Pro](https://x-minus.pro/ai) (Web Alternative):** No installation required. Free limit is ~10 mins/day.

#### Stage 2: Real-time Audio Trigger Workflow
*(🚧 Under Construction)*

> **Preview:** This module will discard static Python MIDI generation. Instead, it will document how to use "Drum Trigger" plugins (like KTDrumTrigger or DSP Trigger Free) inside your DAW. By setting frequency thresholds on the mixer track, the pure drum audio will precisely and in real-time convert its transients into standard MIDI signals sent directly to your drum machine.
