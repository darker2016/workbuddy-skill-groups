# HyperFrames HTML 结构规范

> 被灵映技能引用，定义 HTML 合成文件的必要结构和属性。

## 必须元素

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
</head>
<!-- body 上必须有 data-composition-id、data-width、data-height -->
<body data-composition-id="main" data-width="1920" data-height="1080">

  <!-- 必须在 body 最前面注入 window.__hf 全局对象 -->
  <script>
    window.__hf = {
      duration: 60,       // 视频总时长（秒）
      seek: function(t){} // 时间跳转钩子（留空即可）
    };
  </script>

  <!-- 舞台容器 -->
  <div id="stage"
       data-composition-id="video-gen"
       data-start="0"
       data-width="1920"
       data-height="1080">

    <!-- 背景层（track-index=0） -->
    <div id="background" class="full-screen"
         data-start="0" data-duration="60" data-track-index="0">
      <!-- 背景样式内联 -->
    </div>

    <!-- 文字动画层（track-index=1） -->
    <div id="text-layer" data-start="0" data-duration="60" data-track-index="1">
      <!-- 各分镜字幕动画 -->
    </div>

    <!-- TTS 配音轨道（track-index=2） -->
    <audio id="tts-audio"
           data-start="0" data-duration="60" data-track-index="2"
           data-volume="1.0"
           src="/tmp/ling-factory/audio/[video_id].mp3">
    </audio>

    <!-- BGM 轨道（track-index=3，音量设低） -->
    <audio id="bgm-audio"
           data-start="0" data-duration="60" data-track-index="3"
           data-volume="0.2"
           src="/tmp/ling-factory/bgm/[style-music].mp3">
    </audio>

  </div>

</body>
</html>
```

## 关键 data 属性说明

| 属性 | 说明 | 示例 |
|------|------|------|
| `data-composition-id` | 合成 ID，body 和 stage 都要写 | `"video-gen"` |
| `data-width` / `data-height` | 分辨率 | `1920` / `1080` |
| `data-start` | 元素出现时间点（秒） | `0` |
| `data-duration` | 元素持续时长（秒） | `60` |
| `data-track-index` | 层级 Z-index（数字越大层级越高） | `0` / `1` |
| `data-volume` | 音频音量（0.0-1.0） | `1.0` |

## 常见渲染错误

| 错误 | 原因 | 解决 |
|------|------|------|
| `window.__hf not ready` | 缺少全局对象 | 在 body 第一个 script 注入 |
| 音频 404 | audio src 路径错误 | 用绝对路径，确认文件已生成 |
| 渲染超时 | HTML 语法错误 | 用浏览器打开 HTML 预览检查 |
| 黑屏 | data-composition-id 缺失 | body 和 stage 都加上该属性 |
