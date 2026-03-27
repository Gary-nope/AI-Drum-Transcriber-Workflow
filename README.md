# OpenDrumScribe: Fully Automated AI Drum Transcription Workflow 🥁
[English](#english) | [简体中文](#简体中文)

---

## 简体中文

这是一个完全免费、**全自动化**、高准确度的 AI 鼓谱生成工作流。

市面上多数音频转 MIDI 工具基于音高识别（Pitch-to-MIDI）原理，在面对无固定音高的架子鼓时会产生大量漏判和乱码。而传统的 DAW 瞬态切片方案又需要耗费大量时间进行人工分类。

本项目提供一套**双云端 AI 生产线**：利用音轨分离 AI 提取纯净鼓声，再利用专精于打击乐的深度学习模型进行语义分类，直接输出符合工业标准映射的架子鼓 MIDI（自动区分底鼓、军鼓、踩镲等）。全程零代码基础要求，不消耗本地硬件算力。

### 🛠️ 云端生产线工具链 (The AI Assembly Line)

本项目由两个核心阶段组成：

1. **Stage 1: 纯鼓声提取 (根据偏好二选一)**
   * **[Colab 纯鼓声提取器](./Colab-Drum-Extractor.ipynb) (强烈推荐):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/<你的仓库名>/blob/main/Colab-Drum-Extractor.ipynb)
     利用谷歌免费 GPU 算力运行 Demucs v4 模型。完全免费，无时长限制，分离质量极高。
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (极简网页端平替):** 开箱即用的在线分离网站。**局限：** 免费账户每日仅十几分钟处理额度，适合轻度尝鲜。
   * *(注：拥有高配显卡如 RTX 3060 以上的用户，也可使用本地端的 [UVR5](https://github.com/Anjok07/ultimatevocalremovergui) 完成此步骤。)*

2. **[Stage 2: 语义转录生成器 (Colab Omnizart Transcriber)](./Colab-Drum-To-MIDI-Omnizart.ipynb)**
   * [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/<你的仓库名>/blob/main/Colab-Drum-To-MIDI-Omnizart.ipynb)
   * **底层模型:** MCT Lab Omnizart (Drum Module)
   * **用途:** 上传你在 Stage 1 提取的纯净鼓声音频，AI 将自动进行瞬态捕捉与乐器语义分类，直接生成标准映射的 `.mid` 鼓谱文件。

### 🚀 全自动操作流程 (Workflow)

**步骤一：提纯鼓声音轨**
* **方法 A (Colab 云端提取 - 推荐):** 1. 点击 `Stage 1` 旁的 `Open in Colab` 徽章。
  2. 在顶部菜单栏点击 **代码执行程序 (Runtime)** -> **更改附加到运行时的类型**，硬件加速器选择 **T4 GPU** 并保存，点击右上角**连接**。
  3. 依次点击代码块运行：安装环境 -> 上传目标歌曲 -> 执行 AI 分离。
  4. 运行最后一块代码，下载生成的纯鼓声音轨 (`drums.wav`)。
* **方法 B (X-Minus 在线提取):** 打开网站上传音频，选择鼓组分离模型，处理完成后单独下载鼓声音轨（建议格式选 WAV）。

**步骤二：一键生成标准 MIDI**
1. 点击 `Stage 2` 旁的 `Open in Colab` 徽章。
2. 同样确保已切换至 **T4 GPU** 运行时并连接。
3. 运行环境初始化代码块（云端会自动构建隔离环境并拉取模型，需耐心等待几分钟直至打印 `AI Model Ready!`）。
4. 运行第二块代码，上传你在步骤一中准备好的 `drums.wav`。
5. 运行后续代码块，执行转换并下载最终生成的标准 `.mid` 文件。

**步骤三：打谱与应用**
拿到的 MIDI 文件已经具备了完美的标准打击乐映射（如 Kick=C3, Snare=D3, Hi-hat=F#3）：
* **制作人:** 直接将其拖入宿主软件（如 FL Studio, Ableton）的鼓机插件（如 FPC）中即可无缝发声。
* **鼓手:** 将其导入 [MuseScore](https://musescore.org/)，软件会自动排版为标准打击乐五线谱，添加记号后即可打印 PDF。

---

## English

This is a completely free, **fully automated**, and highly accurate AI drum transcription workflow.

Standard audio-to-MIDI tools rely on pitch detection, which fails miserably on unpitched percussion like drums. Traditional DAW transient slicing methods require tedious manual classification.

This project offers a **Dual-Cloud AI Assembly Line**: First, it isolates the drum track using a source separation AI. Then, it uses a deep learning model specifically trained for percussion to semantically classify the hits (Kick, Snare, Hi-hat, etc.), directly outputting a standard-mapped MIDI file. No coding required, runs entirely on free cloud GPUs.

### 🛠️ The AI Assembly Line

This workflow consists of two core stages:

1. **Stage 1: Pure Drum Extraction (Choose One)**
   * **[Colab Drum Extractor](./Colab-Drum-Extractor.ipynb) (Highly Recommended):** [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/<你的仓库名>/blob/main/Colab-Drum-Extractor.ipynb)
     Uses Google's free cloud GPU to run Demucs v4. No strict time limits and top-tier separation quality.
   * **[X-Minus Pro AI](https://x-minus.pro/ai) (Web Alternative):** Ready out of the box. **Limitation:** Free accounts are restricted to ~10 mins of audio processing per day.
   * *(Note: Users with high-end GPUs can also use the local [UVR5](https://github.com/Anjok07/ultimatevocalremovergui) client for this step.)*

2. **[Stage 2: Colab Omnizart Transcriber](./Colab-Drum-To-MIDI-Omnizart.ipynb)**
   * [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gary-nope/<你的仓库名>/blob/main/Colab-Drum-To-MIDI-Omnizart.ipynb)
   * **Powered by:** MCT Lab Omnizart
   * **Purpose:** Upload the isolated drum track from Stage 1, and the AI will automatically capture transients, classify the instruments semantically, and generate a standard-mapped `.mid` drum sheet file.

### 🚀 Step-by-Step Workflow

**Step 1: Extract the Pure Drum Track**
* **Method A (Cloud via Colab - Recommended):** 1. Click the `Open in Colab` badge next to `Stage 1`.
  2. Go to `Runtime` > `Change runtime type` > Select `T4 GPU` and save. Click `Connect` in the top right.
  3. Run the cells sequentially: Install environment -> Upload your target song -> Run AI separation.
  4. Run the final cell to download the isolated drum track (`drums.wav`).
* **Method B (Web via X-Minus):** Upload your audio, choose a drum isolation model, and download the isolated drum track (WAV format recommended).

**Step 2: Generate Standard MIDI**
1. Click the `Open in Colab` badge next to `Stage 2`.
2. Ensure you are using the **T4 GPU** runtime and connected.
3. Run the initialization cell (Wait a few minutes for the sandbox environment to build until it says `AI Model Ready!`).
4. Run the second cell to upload your extracted `drums.wav`.
5. Execute the transcription and download the generated `.mid` file.

**Step 3: Notation and Application**
The resulting MIDI file comes with perfect standard percussion mapping (e.g., Kick=C3, Snare=D3, Hi-hat=F#3):
* **For Producers:** Drag it directly into your DAW's drum machine plugin (e.g., FPC in FL Studio) for instant playback.
* **For Drummers:** Import it into [MuseScore](https://musescore.org/), and it will automatically format it into standard 5-line drum sheet music. Add articulations and export as PDF.
