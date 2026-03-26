# OpenDrumScribe: AI-Powered Drum Transcription Workflow 🥁
[English](#english) | [简体中文](#简体中文)

---

## 简体中文

这是一个完全免费、高准确度的 AI 鼓谱生成工作流。

市面上许多号称“一键生成”的音频转 MIDI 工具，在面对混杂了吉他、贝斯和人声的完整曲目时，往往会对架子鼓的幽灵音（Ghost Notes）和镲片延音产生大量误判。本项目旨在提供一套**开源工具链与在线工具组合**，通过“先提取纯鼓轨，再进行 MIDI 转换与排版”的思路，以零成本获得极高可用性的架子鼓谱。

### 🛠️ 工具链与获取指引 (Tools & Downloads)

1. **分离纯鼓轨 (二选一):**
   * **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui) (本地进阶推荐):** 目前最顶级的开源 AI 音轨分离工具。分离极其干净，无时长限制，但软件体积庞大（需下载模型）且依赖本地电脑算力。
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (云端轻量平替):** 极其强大的在线音轨分离网站，无需安装即可分离各种乐器。**局限：** 免费账户每日仅有十几分钟的音频处理额度，适合轻度尝鲜或处理单首歌曲。
2. **[Basic Pitch](https://basicpitch.spotify.com/) (网页端) 或 [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **用途:** 将纯净的鼓点音频文件转化为初步的 MIDI 信号。
3. **宿主软件 (DAW, 如 FL Studio, Ableton Live 等)**
   * **用途:** 利用钢琴卷帘窗（Piano Roll）对 AI 转换的 MIDI 进行视觉化微调与对轨。
4. **[MuseScore](https://musescore.org/)**
   * **用途:** 完全免费的专业打谱软件，用于将微调后的 MIDI 自动排版为标准打击乐五线谱。

### 🚀 使用操作流程 (Workflow)

**步骤一：提取纯净鼓轨**
* **选项 A (使用 UVR5 本地处理):** 打开软件，导入完整歌曲音频。选择 `MDX-Net` 或 `Demucs` 模型。勾选分离出 `Drums`（鼓组）音轨并导出。
* **选项 B (使用 X-Minus Pro 在线处理):** 打开网站，上传你的目标音频。选择包含鼓组分离的 AI 模型进行处理。完成后，试听并单独下载只有鼓声（Drums）的纯净音轨。

**步骤二：音频转 MIDI**
1. 打开 Basic Pitch 网页端或加载 NeuralNote 插件。
2. 将上一步获取的纯鼓点音频拖入其中。
3. 软件解析完成后，直接导出为 `.mid` 格式文件。

**步骤三：MIDI 微调与对轨**
1. 打开你的 DAW，将原曲音频拖入一个轨道作为参考，将纯鼓点音频拖入另一个轨道。
2. 将生成的 MIDI 文件拖入对应的 MIDI 乐器轨，打开钢琴卷帘窗（Piano Roll）。
3. 播放音频，对照纯鼓声音轨的波形，手动修正 AI 偶尔漏判的底鼓（Kick）或误判的踩镲（Hi-hat）位置。

**步骤四：生成标准鼓谱**
1. 将修正完毕的完美 MIDI 文件导出。
2. 打开 MuseScore，导入该 MIDI 文件。
3. 软件会自动将其转换为标准的打击乐五线谱，你可以添加连音线、重音记号后直接打印为 PDF。

---

## English

This is a completely free, highly accurate AI drum transcription workflow.

Many "one-click" audio-to-MIDI tools struggle with complete tracks mixed with guitars, bass, and vocals, often misinterpreting drum ghost notes and cymbal sustains. This project provides an **open-source and cloud-based toolchain combination**. By adopting a "separate pure drum tracks first, then convert and format" approach, you can obtain highly usable drum sheet music at zero cost.

### 🛠️ Tools & Downloads

1. **Extract Pure Drum Track (Choose One):**
   * **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui) (Local/Advanced):** The top-tier open-source AI stem separation tool. Offers the cleanest extraction with no time limits, but requires a large download and relies on your local CPU/GPU.
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (Cloud/Lightweight Alternative):** A powerful online track separation tool. No installation required. **Limitation:** Free accounts are restricted to around 10+ minutes of audio processing per day. Best for light users or single-song projects.
2. **[Basic Pitch](https://basicpitch.spotify.com/) (Web) or [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **Purpose:** Converts the isolated pure drum audio file into raw MIDI signals.
3. **Any DAW (e.g., FL Studio, Ableton Live)**
   * **Purpose:** Utilizes the Piano Roll for visual fine-tuning and syncing of the AI-converted MIDI.
4. **[MuseScore](https://musescore.org/)**
   * **Purpose:** A completely free, professional notation software used to automatically format the adjusted MIDI into standard percussion sheet music.

### 🚀 Step-by-Step Workflow

**Step 1: Extract the Pure Drum Track**
* **Option A (Local via UVR5):** Open UVR5 and import your target song. Select the `MDX-Net` or `Demucs` model. Ensure the `Drums` stem is selected for separation, and export.
* **Option B (Cloud via X-Minus Pro):** Open the website and upload your audio file. Choose an AI model that separates the drum track. Once processed, preview and download only the isolated Drums audio file.

**Step 2: Audio to MIDI Conversion**
1. Open Basic Pitch in your browser or load the NeuralNote plugin.
2. Drop the pure drum audio from Step 1 into the interface.
3. Once processed, export the result as a `.mid` file.

**Step 3: MIDI Refinement & Syncing**
1. Open your DAW. Import the original song into one track as a reference, and the pure drum audio into another.
2. Drag the generated MIDI file into a MIDI instrument track and open the Piano Roll.
3. Play back the audio. Compare it visually with the pure drum waveform and manually correct any misidentified kicks or hi-hats missed by the AI.

**Step 4: Generate Standard Sheet Music**
1. Export the perfected MIDI file.
2. Open MuseScore and import the MIDI.
3. The software will automatically translate it into standard drum notation. Add any necessary articulations or accents, and export as a PDF.
