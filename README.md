# OpenDrumScribe: AI-Powered Drum Transcription Workflow 🥁
[English](#english) | [简体中文](#简体中文)

---

## 简体中文

这是一个完全免费、高准确度的 AI 鼓谱生成工作流。

市面上多数音频转 MIDI 工具在面对完整混音曲目时，会对架子鼓的幽灵音（Ghost Notes）和镲片产生大量误判。本项目提供一套**涵盖本地算力与云端方案的开源工具链组合**，核心思路为：“先提取纯鼓轨，再进行 MIDI 转换与排版”，从而以零成本获得高可用性的架子鼓谱。

### 🛠️ 工具链与获取指引 (Tools & Downloads)

1. **分离纯鼓轨 (根据你的硬件情况三选一):**
   * **[Google Colab 极简提取脚本](./Colab-Drum-Extractor.ipynb) (强烈推荐):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/AI-Drum-Transcriber-Workflow/blob/main/Colab-Drum-Extractor.ipynb)
     利用谷歌免费 GPU 算力运行开源分离模型。不吃本地电脑配置，无严格时长限制，分离质量极高。
   * **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui) (适合高配主机):** 顶级的本地 AI 音轨分离客户端。
     > **⚠️ UVR5 硬件要求：** GPU 转换最低要求 Nvidia GTX 1060 6GB，推荐 8GB 以上显存。低于此配置易触发显存溢出 (OOM)。仅兼容 64 位平台。
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (极简网页端):** 强大的在线分离网站。免费账户每日仅十几分钟处理额度。

2. **[Basic Pitch](https://basicpitch.spotify.com/) 或 [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **用途:** 将纯净鼓点音频转化为初步的 MIDI 信号。
3. **宿主软件 (DAW, 如 FL Studio, Ableton 等)**
   * **用途:** 利用钢琴卷帘窗（Piano Roll）视觉化微调与对轨 AI 转换的 MIDI。
4. **[MuseScore](https://musescore.org/)**
   * **用途:** 将微调后的 MIDI 自动排版为标准打击乐五线谱。

### 🚀 使用操作流程 (Workflow)

**步骤一：提取纯净鼓轨**
* **方法 A (Colab 云端 - 推荐):** 1. 点击上方的 `Open in Colab` 徽章。
  2. 在顶部菜单栏点击 **代码执行程序 (Runtime)** -> **更改附加到运行时的类型**，硬件加速器选择 **T4 GPU** 并保存。点击右上角**连接 (Connect)**。
  3. 依次点击代码块左侧的 `▶` 按钮：安装环境 -> 上传歌曲 -> 执行分离。
  4. 运行最后一块代码，浏览器将自动下载分离出的纯鼓声音轨 (`drums.wav`)。
* **方法 B (UVR5 本地):** 导入音频，选择 `MDX-Net` 或 `Demucs` 模型，勾选分离 `Drums` 音轨并导出。
* **方法 C (X-Minus 在线):** 上传音频，选择鼓组分离模型，试听并下载鼓声音轨。

**步骤二：音频转 MIDI**
1. 将纯鼓点音频拖入 Basic Pitch 网页端或 NeuralNote 插件。
2. 解析完成后导出为 `.mid` 文件。

**步骤三：MIDI 微调与对轨**
1. 在 DAW 中将原曲与纯鼓点音频分轨导入对齐。
2. 将生成的 MIDI 拖入乐器轨，打开钢琴卷帘窗。
3. 对照纯鼓声波形，手动修正偶尔漏判的底鼓或误判的踩镲。

**步骤四：生成标准鼓谱**
1. 导出修正完毕的 MIDI 文件。
2. 导入 MuseScore，自动转换为五线谱，添加连音线和记号后导出。

---

## English

This is a completely free, highly accurate AI drum transcription workflow.

Many "one-click" audio-to-MIDI tools struggle with complete mixed tracks, often misinterpreting ghost notes and cymbal sustains. This project provides an **open-source toolchain combination (Local & Cloud)**. By adopting a "separate pure drum tracks first, then convert and format" approach, you can obtain highly usable drum sheet music at zero cost.

### 🛠️ Tools & Downloads

1. **Extract Pure Drum Track (Choose based on your hardware):**
   * **[Colab Drum Extractor](./Colab-Drum-Extractor.ipynb) (Highly Recommended):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/<你的仓库名>/blob/main/Colab-Drum-Extractor.ipynb)
     Uses Google's free cloud GPU. Perfect for low-spec PCs, no strict time limits, and offers top-tier separation quality.
   * **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui) (For High-End PCs):** The ultimate local AI stem separation client.
     > **⚠️ UVR5 Hardware Requirements:** Nvidia GTX 1060 6GB is the minimum for GPU conversion. At least 8GB of VRAM is recommended. Lower specs may trigger Out of Memory (OOM) crashes. Compatible only with 64-bit platforms.
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (Web Minimalist):** A powerful online tool. Free accounts are restricted to ~10 mins/day.

2. **[Basic Pitch](https://basicpitch.spotify.com/) or [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **Purpose:** Converts the isolated pure drum audio file into raw MIDI signals.
3. **Any DAW (e.g., FL Studio, Ableton Live)**
   * **Purpose:** Utilizes the Piano Roll for visual fine-tuning of the AI-converted MIDI.
4. **[MuseScore](https://musescore.org/)**
   * **Purpose:** Formats the adjusted MIDI into standard percussion sheet music.

### 🚀 Step-by-Step Workflow

**Step 1: Extract the Pure Drum Track**
* **Method A (Cloud via Colab - Recommended):** 1. Click the `Open in Colab` badge above.
  2. Go to `Runtime` > `Change runtime type` > Select `T4 GPU` and save. Click `Connect` in the top right.
  3. Run the cells sequentially by clicking the `▶` button: Install -> Upload Song -> Separate.
  4. Run the final cell to download the isolated `drums.wav`.
* **Method B (Local via UVR5):** Import audio. Select `MDX-Net` or `Demucs` model. Extract the `Drums` stem and export.
* **Method C (Web via X-Minus):** Upload audio. Choose a drum isolation model. Download the drum track.

**Step 2: Audio to MIDI Conversion**
1. Drop the pure drum audio into Basic Pitch or NeuralNote.
2. Export the result as a `.mid` file.

**Step 3: MIDI Refinement & Syncing**
1. Open your DAW. Import the original song and pure drum audio.
2. Drag the MIDI file into an instrument track and open the Piano Roll.
3. Manually correct misidentified kicks or hi-hats by comparing visually with the pure drum waveform.

**Step 4: Generate Standard Sheet Music**
1. Export the perfected MIDI file.
2. Import the MIDI into MuseScore for automatic standard drum notation. Add necessary articulations and export.
