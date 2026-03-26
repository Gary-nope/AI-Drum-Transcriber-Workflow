# OpenDrumScribe: AI-Powered Drum Transcription Workflow 🥁
[English](#english) | [简体中文](#简体中文)

---

## 简体中文

这是一个完全免费、高准确度的 AI 鼓谱生成工作流。

市面上许多号称“一键生成”的音频转 MIDI 工具，在面对混杂了吉他、贝斯和人声的完整曲目时，往往会对架子鼓的幽灵音（Ghost Notes）和镲片延音产生大量误判。本项目旨在提供一套**涵盖本地算力与云端方案的开源工具链组合**，通过“先提取纯鼓轨，再进行 MIDI 转换与排版”的思路，以零成本获得极高可用性的架子鼓谱。

### 🛠️ 工具链与获取指引 (Tools & Downloads)

1. **分离纯鼓轨 (根据你的硬件情况三选一):**
   * **[Google Colab 极简提取脚本](./Colab-Drum-Extractor.ipynb) (强烈推荐):** 本项目提供的开箱即用云端脚本。利用谷歌免费 GPU 算力运行开源分离模型。**优势：** 不吃本地电脑配置（低配轻薄本救星），无严格时长限制，分离质量极高。
   * **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui) (适合高配主机):** 顶级的本地 AI 音轨分离客户端。
     > **⚠️ UVR5 硬件与系统要求注意：**
     > * **算力警告：** 这些 AI 模型计算量极大，转换时间很大程度上取决于你的硬件。
     > * **显卡要求：** GPU 转换的最低要求为 **Nvidia GTX 1060 6GB**，推荐使用至少 **8GB 显存** 的显卡。低于此配置容易触发显存溢出。
     > * **AMD 支持：** 目前支持的 AMD Radeon 显卡有限（AMD 用户需前往官方仓库寻找面向 AMD GPU 的专用工作分支）。
     > * **系统与依赖：** 仅兼容 64 位平台。依赖 FFmpeg 处理非 wav 音频文件，依赖 Rubber Band Library 实现时间拉伸和音高移位选项。
     > * **人性化设计：** 应用关闭时会自动记住你的设置。
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (极简网页端):** 强大的在线分离网站。**局限：** 免费账户每日仅十几分钟额度。

2. **[Basic Pitch](https://basicpitch.spotify.com/) (网页端) 或 [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **用途:** 将纯净鼓点音频转化为初步的 MIDI 信号。
3. **宿主软件 (DAW, 如 FL Studio, Ableton 等)**
   * **用途:** 利用钢琴卷帘窗（Piano Roll）视觉化微调与对轨 AI 转换的 MIDI。
4. **[MuseScore](https://musescore.org/)**
   * **用途:** 将微调后的 MIDI 自动排版为标准打击乐五线谱。

### 🚀 使用操作流程 (Workflow)

**步骤一：提取纯净鼓轨**
* **方法 A (Colab 云端 - 推荐):** 点击本仓库的 `Colab-Drum-Extractor.ipynb`，并在 Google Colab 中打开。依次运行代码块：安装环境 -> 上传歌曲 -> 执行分离。完成后在左侧文件夹下载分离出的 `drums.wav`。
* **方法 B (UVR5 本地):** 打开软件导入音频。选择 `MDX-Net` 或 `Demucs` 模型。勾选分离出 `Drums` 音轨并导出。
* **方法 C (X-Minus 在线):** 打开网站上传音频。选择鼓组分离模型，试听并下载鼓声音轨。

**步骤二：音频转 MIDI**
1. 打开 Basic Pitch 网页端或加载 NeuralNote 插件。
2. 将纯鼓点音频拖入，解析完成后导出为 `.mid` 文件。

**步骤三：MIDI 微调与对轨**
1. 在 DAW 中将原曲与纯鼓点音频分轨导入对齐。
2. 将生成的 MIDI 拖入乐器轨，打开钢琴卷帘窗。
3. 对照纯鼓声波形，手动修正偶尔漏判的底鼓（Kick）或误判的踩镲（Hi-hat）。

**步骤四：生成标准鼓谱**
1. 导出修正完毕的完美 MIDI。
2. 导入 MuseScore，自动转换为五线谱，添加记号后打印即可。

---

## English

This is a completely free, highly accurate AI drum transcription workflow.

Many "one-click" audio-to-MIDI tools struggle with complete tracks, often misinterpreting ghost notes and cymbal sustains. This project provides an **open-source toolchain combination (Local & Cloud)**. By separating pure drum tracks first, then converting and formatting, you can obtain highly usable drum sheet music at zero cost.

### 🛠️ Tools & Downloads

1. **Extract Pure Drum Track (Choose based on your hardware):**
   * **[Colab Drum Extractor](./Colab-Drum-Extractor.ipynb) (Highly Recommended):** The out-of-the-box cloud script provided in this repo. Uses Google's free GPU. **Pros:** Perfect for low-spec PCs, no strict time limits.
   * **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui) (For High-End PCs):** The ultimate local AI stem separation client.
     > **⚠️ UVR5 Hardware & System Requirements:**
     > * **Compute Heavy:** These models are computationally intensive. Conversion time heavily depends on your hardware.
     > * **GPU Minimum:** Nvidia GTX 1060 6GB is the minimum for GPU conversion. At least 8GB of VRAM is recommended.
     > * **AMD Support:** Limited support for AMD Radeon GPUs (AMD users should look for the specific working branch).
     > * **System & Dependencies:** Compatible only with 64-bit platforms. Depends on FFmpeg for non-wav files and the Rubber Band Library for time-stretching/pitch-shifting.
     > * **Misc:** Automatically remembers your settings when closed.
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (Web Minimalist):** Free accounts are restricted to ~10 mins/day.

2. **[Basic Pitch](https://basicpitch.spotify.com/) (Web) or [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **Purpose:** Converts the isolated pure drum audio file into raw MIDI signals.
3. **Any DAW (e.g., FL Studio, Ableton Live)**
   * **Purpose:** Utilizes the Piano Roll for visual fine-tuning of the AI-converted MIDI.
4. **[MuseScore](https://musescore.org/)**
   * **Purpose:** Formats the adjusted MIDI into standard percussion sheet music.

### 🚀 Step-by-Step Workflow

**Step 1: Extract the Pure Drum Track**
* **Method A (Cloud via Colab - Recommended):** Open `Colab-Drum-Extractor.ipynb` from this repo in Google Colab. Run the cells sequentially: Install -> Upload Song -> Separate. Download `drums.wav` from the files pane.
* **Method B (Local via UVR5):** Import audio. Select `MDX-Net` or `Demucs` model. Extract the `Drums` stem and export.
* **Method C (Web via X-Minus):** Upload audio. Choose a drum isolation model. Download the drum track.

**Step 2: Audio to MIDI Conversion**
1. Drop the pure drum audio into Basic Pitch or NeuralNote.
2. Export the result as a `.mid` file.

**Step 3: MIDI Refinement & Syncing**
1. Open your DAW. Import the original song and pure drum audio.
2. Drag the MIDI file into an instrument track and open the Piano Roll.
3. Manually correct misidentified kicks or hi-hats by comparing with the drum waveform.

**Step 4: Generate Standard Sheet Music**
1. Export the perfected MIDI file.
2. Import the MIDI into MuseScore for automatic standard drum notation.
