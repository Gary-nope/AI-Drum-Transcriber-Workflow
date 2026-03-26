# OpenDrumScribe: AI-Powered Drum Transcription Workflow 🥁
[English](#english) | [简体中文](#简体中文)

---

## 简体中文

这是一个完全免费、高准确度的 AI 鼓谱生成工作流。

市面上许多号称“一键生成”的音频转 MIDI 工具，在面对混杂了吉他、贝斯和人声的完整曲目时，往往会对架子鼓的幽灵音（Ghost Notes）和镲片延音产生大量误判。本项目旨在提供一套**开源工具链组合**，通过“先提取纯鼓轨，再进行 MIDI 转换与排版”的思路，以零成本获得极高可用性的架子鼓谱。

### 🛠️ 工具链与下载指引 (Tools & Downloads)

请避免从第三方网站下载，直接点击下方官方链接获取最新版本：

1. **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui)**
   * **用途:** 目前最顶级的开源 AI 音轨分离工具。用于将原曲中的架子鼓声音极度干净地剥离出来，排除其他频段干扰。
2. **[Basic Pitch](https://basicpitch.spotify.com/) (网页端) 或 [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **用途:** 将纯净的鼓点音频文件转化为初步的 MIDI 信号。
3. **[FL Studio](https://www.image-line.com/) 或 其他宿主软件 (DAW)**
   * **用途:** 利用钢琴卷帘窗（Piano Roll）对 AI 转换的 MIDI 进行视觉化微调与对轨。
4. **[MuseScore](https://musescore.org/)**
   * **用途:** 完全免费的专业打谱软件，用于将微调后的 MIDI 自动排版为标准打击乐五线谱。

### 🚀 使用操作流程 (Workflow)

**步骤一：提取纯净鼓轨**
1. 打开 UVR5，导入你需要扒谱的完整歌曲音频。
2. 在 `Process Method` 中选择 `MDX-Net` 或 `Demucs` 模型（推荐使用专门针对鼓点训练的 Demucs v4 HT 模型）。
3. 勾选分离出 `Drums`（鼓组）音轨，点击导出。你将得到一个只有纯粹打鼓声的音频文件。

**步骤二：音频转 MIDI**
1. 打开 Basic Pitch 网页端或加载 NeuralNote 插件。
2. 将上一步生成的纯鼓点音频拖入其中。
3. 软件解析完成后，直接导出为 `.mid` 格式文件。

**步骤三：MIDI 微调与对轨**
1. 打开 FL Studio，将原曲音频拖入一个轨道作为参考，将纯鼓点音频拖入另一个轨道。
2. 将生成的 MIDI 文件拖入对应的 MIDI 乐器轨，打开钢琴卷帘窗（Piano Roll）。
3. 播放音频，对照纯鼓声音轨的波形，手动修正 AI 偶尔漏判的底鼓（Kick）或误判的踩镲（Hi-hat）位置。

**步骤四：生成标准鼓谱**
1. 将修正完毕的完美 MIDI 文件导出。
2. 打开 MuseScore，导入该 MIDI 文件。
3. 软件会自动将其转换为标准的打击乐五线谱，你可以添加连音线、重音记号后直接打印为 PDF。

---

## English

This is a completely free, highly accurate AI drum transcription workflow.

Many "one-click" audio-to-MIDI tools struggle with complete tracks mixed with guitars, bass, and vocals, often misinterpreting drum ghost notes and cymbal sustains. This project provides an **open-source toolchain combination**. By adopting a "separate pure drum tracks first, then convert and format" approach, you can obtain highly usable drum sheet music at zero cost.

### 🛠️ Tools & Downloads

Please avoid downloading from third-party sites. Click the official links below for the latest releases:

1. **[Ultimate Vocal Remover (UVR5)](https://github.com/Anjok07/ultimatevocalremovergui)**
   * **Purpose:** The top-tier open-source AI stem separation tool. Used to cleanly extract the drum kit from the original song, eliminating frequency interference from other instruments.
2. **[Basic Pitch](https://basicpitch.spotify.com/) (Web) or [NeuralNote](https://github.com/DamRsn/NeuralNote)**
   * **Purpose:** Converts the isolated pure drum audio file into raw MIDI signals.
3. **[FL Studio](https://www.image-line.com/) or any DAW**
   * **Purpose:** Utilizes the Piano Roll for visual fine-tuning and syncing of the AI-converted MIDI.
4. **[MuseScore](https://musescore.org/)**
   * **Purpose:** A completely free, professional notation software used to automatically format the adjusted MIDI into standard percussion sheet music.

### 🚀 Step-by-Step Workflow

**Step 1: Extract the Pure Drum Track**
1. Open UVR5 and import your target song.
2. Under `Process Method`, select the `MDX-Net` or `Demucs` model (The Demucs v4 HT model trained specifically for drums is highly recommended).
3. Ensure the `Drums` stem is selected for separation, and export. You now have an audio file containing only the drums.

**Step 2: Audio to MIDI Conversion**
1. Open Basic Pitch in your browser or load the NeuralNote plugin.
2. Drop the pure drum audio from Step 1 into the interface.
3. Once processed, export the result as a `.mid` file.

**Step 3: MIDI Refinement & Syncing**
1. Open FL Studio. Import the original song into one track as a reference, and the pure drum audio into another.
2. Drag the generated MIDI file into a MIDI instrument track and open the Piano Roll.
3. Play back the audio. Compare it visually with the pure drum waveform and manually correct any misidentified kicks or hi-hats missed by the AI.

**Step 4: Generate Standard Sheet Music**
1. Export the perfected MIDI file.
2. Open MuseScore and import the MIDI.
3. The software will automatically translate it into standard drum notation. Add any necessary articulations or accents, and export as a PDF.
