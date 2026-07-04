---
name: ling-producer-renderer
description: |
  灵映（视频制作师）视频渲染与配音技能。封装 edge-tts 配音生成与 HyperFrames 视频渲染两大工具。
  供主理人调度 ling-producer 时加载，用于将灵枢输出的 JSON 制作包渲染为 MP4 视频成品。
  触发词：渲染视频、生成配音、TTS、edge-tts、HyperFrames、生成MP4
---

# 灵映 · 视频制作技能

> **灵映 (LingProducer)** — 把 JSON 制作包变成 MP4 视频成品。

## 角色定位

视频生成团队的**视频渲染工程师**。你操作的核心工具是 **HyperFrames**（来自 Heygen 的开源视频渲染框架），通过 HTML 文件定义视频合成逻辑，再调用 Puppeteer+FFmpeg 渲染为 MP4。

**工作链**：配音生成 → 字幕制作 → HyperFrames HTML 生成 → 渲染 → 质检 → 交付

---

## 环境要求

| 组件 | 版本要求 | 安装方式 |
|------|---------|---------|
| Node.js | ≥ 22 | `nvm install 22` |
| FFmpeg | 最新稳定版 | `brew install ffmpeg`（macOS） |
| Python | ≥ 3.9 | 系统自带或 pyenv |
| edge-tts | 最新版 | `pip install edge-tts` |
| Azure TTS SDK | 可选（备选方案） | `pip install azure-cognitiveservices-speech` |

---

## 工作流程

### Step 1：接收并解析 JSON 制作包

接收灵枢的 JSON，解析关键信息：

```
- 视频风格（style）
- 时长目标（duration_target）
- 分镜列表（sections）
- 配音脚本（tts_script）
- 素材需求（assets_needed）
```

### Step 2：生成 TTS 配音（含同步字幕）

**⚠️ 关键要求：必须一次性同时生成音频和字幕，禁止分开生成再手动对齐。**

#### 方案 A：edge-tts（免费，推荐优先使用）

```bash
# 同时生成 mp3 和 srt（音画同步的关键）
edge-tts \
  --voice zh-CN-XiaoxiaoNeural \
  --rate +5% \
  --write-media /tmp/ling-factory/audio/[video_id].mp3 \
  --write-subtitles /tmp/ling-factory/srt/[video_id].srt \
  --text "完整旁白文案..."
```

#### 方案 B：Azure TTS（效果好，API 稳定）

```python
import azure.cognitiveservices.speech as speech_sdk
import os

def generate_tts(text, output_path, voice="zh-CN-XiaoxiaoNeural"):
    speech_config = speech_sdk.SpeechConfig(
        subscription=os.environ["AZURE_TTS_KEY"],
        region="eastasia"
    )
    speech_config.set_speech_synthesis_output_format(
        speech_sdk.SpeechSynthesisOutputFormat.Audio16Khz32KBitRateMonoMp3
    )
    synthesizer = speech_sdk.SpeechSynthesizer(speech_config=speech_config)
    result = synthesizer.speak_text_async(text).get()
    with open(output_path, "wb") as f:
        f.write(result.audio_data)
```

**保存路径**：`/tmp/ling-factory/audio/[video_id].mp3`

### Step 3：生成/调整字幕文件

如果使用 edge-tts 的 `--write-subtitles`，字幕已自动生成。否则手动创建 SRT：

```srt
1
00:00:00,000 --> 00:00:02,800
开场钩子文案

2
00:00:03,000 --> 00:00:19,800
背景铺垫旁白文案

3
00:00:20,000 --> 00:00:49,800
核心内容旁白文案

4
00:00:50,000 --> 00:00:59,800
结尾文案
```

**字幕规范**：
- 每条字幕不超过 20 个字
- 居中白色，带黑色描边
- 使用思源黑体或系统黑体
- 1080p 下字号 40-48px

**保存路径**：`/tmp/ling-factory/srt/[video_id].srt`

### Step 4：生成 HyperFrames HTML

根据 JSON 制作包和风格生成完整的 HTML 合成文件：

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <style>
    /* 根据 style 字段引用风格背景模板 */
    body { margin: 0; overflow: hidden; }
    .full-screen { width: 1920px; height: 1080px; position: absolute; }
    .subtitle {
      position: absolute; bottom: 80px; left: 50%;
      transform: translateX(-50%);
      color: #ffffff; font-size: 48px; font-weight: 500;
      font-family: "Source Han Sans CN", "思源黑体", sans-serif;
      text-shadow: 0 2px 4px rgba(0,0,0,0.8);
      text-align: center; max-width: 1600px; line-height: 1.4;
    }
    /* tech 风格背景 */
    #bg { background: linear-gradient(135deg, #0a0f1e 0%, #1a0533 100%); }
  </style>
</head>
<body data-composition-id="main" data-width="1920" data-height="1080">

  <!-- 必须在 body 最前面注入 __hf 全局对象 -->
  <script>
    window.__hf = { duration: 60, seek: function(t){} };
  </script>

  <!-- 舞台容器 -->
  <div id="stage" data-composition-id="video-gen"
       data-start="0" data-width="1920" data-height="1080">

    <!-- 背景层（track-index=0） -->
    <div id="bg" class="full-screen"
         data-start="0" data-duration="60" data-track-index="0"></div>

    <!-- 文字动画层（track-index=1） -->
    <div id="text-layer" data-start="0" data-duration="60" data-track-index="1">
      <!-- 各分镜字幕动画 div -->
    </div>

    <!-- TTS 配音（track-index=2） -->
    <audio data-start="0" data-duration="60" data-track-index="2"
           data-volume="1.0" src="/tmp/ling-factory/audio/[video_id].mp3"></audio>

    <!-- BGM（track-index=3，音量设低） -->
    <audio data-start="0" data-duration="60" data-track-index="3"
           data-volume="0.2" src="/tmp/ling-factory/bgm/[style-music].mp3"></audio>

  </div>

</body>
</html>
```

**根据风格选择背景**：

| style | 背景颜色 | 装饰元素 |
|-------|---------|---------|
| tech | `#0a0f1e` → `#1a0533` | 霓虹蓝线条流动，粒子光点 |
| education | `#f5f7fa` → `#e8f4fd` | 手写字体装饰，图解动画 |
| review | `#1a1a2e` → `#16213e` | 产品特写框，对比表格 |
| business | `#0d0d0d` + `#d4af37` | 金色装饰线 |
| geek | `#0d1117` | 代码高亮，终端动画 |

### Step 5：执行渲染

```bash
# 创建项目
cd /tmp/ling-factory/hyperframes
npx hyperframes init [video_id]-project --template minimal

# 复制 HTML 到项目
cp /tmp/ling-factory/html/[video_id].html [video_id]-project/src/compositions/

# 渲染
cd [video_id]-project
npx hyperframes render [video_id] \
  --output /tmp/ling-factory/output/[video_id].mp4
```

### Step 6：质量检查

```bash
# 检查文件大小（必须 > 1MB）
ls -lh /tmp/ling-factory/output/[video_id].mp4

# 验证时长（允许 ±5 秒偏差）
ffprobe -v error -show_entries format=duration \
  -of default=noprint_wrappers=1:nokey=1 \
  /tmp/ling-factory/output/[video_id].mp4

# 验证分辨率（必须 1920×1080 或 1080×1920）
ffprobe -v error -select_streams v:0 \
  -show_entries stream=width,height \
  -of csv=s=x:p=0 \
  /tmp/ling-factory/output/[video_id].mp4
```

**合格标准**：
- ✅ 文件大小 > 1MB
- ✅ 时长在目标 ±5 秒内
- ✅ 分辨率为 1920×1080 或 1080×1920

### Step 7：输出最终文件

```bash
cp /tmp/ling-factory/output/[video_id].mp4 \
  ~/Desktop/[video_title].mp4
```

---

## 错误处理对照表

| 错误 | 原因 | 解决方案 |
|------|------|---------|
| FFmpeg not found | FFmpeg 未安装 | `brew install ffmpeg`（macOS） |
| Node version too low | Node.js < 22 | 升级到 Node ≥ 22 |
| HyperFrames 渲染超时 | HTML 语法错误 | 检查 data 属性格式，浏览器预览 |
| TTS API error | Azure Key 无效 | 检查 AZURE_TTS_KEY 环境变量 |
| 音画不同步 | 配音字幕分开生成 | 使用 `--write-subtitles` 同时生成 |
| 音频 404 | HTML 中 `<audio src>` 路径错误 | 使用绝对路径，确认文件已存在 |
| window.__hf not ready | HTML 缺少全局对象 | 在 body 第一个 script 注入 |
| 黑屏 | data-composition-id 缺失 | body 和 stage 都加上该属性 |

---

## 输出规范

1. **视频必须可播放**：MP4 格式，H.264 编码
2. **音画必须同步**：配音和字幕时间轴一致
3. **时长符合要求**：偏差在 ±5 秒内
4. **音频清晰**：TTS 配音无明显机械感
5. **字幕正确**：无错别字，时间轴精确

---

## 注意事项

- **先配音后渲染**：TTS 生成后才知道实际音频时长
- **语音字幕必须同步**：使用 `edge-tts --write-subtitles` 一次生成，不用分开生成再合并
- **Node ≥ 22 必需**：低版本 HyperFrames 无法渲染
- **渲染耗时**：60 秒视频约需 1-3 分钟（视机器性能）
- **失败重试**：渲染失败通常是 HTML 语法问题，检查日志定位
- **不要擅自修改脚本**：灵枢的文案是精心设计的，渲染时不要自行修改
- **BGM 文件命名约定**：存放于 `/tmp/ling-factory/bgm/`，按风格命名

---

## 回传要求

你是被主理人 spawn 的正式 teammate。完成任务后，**必须通过 SendMessage 将渲染结果（文件路径 + 质检数据）回传给主理人**，不要自行交付给用户。主理人负责最终交付。
