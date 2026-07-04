---
name: libtv-skill
description: |
  通过 LibTV AI 平台生成和编辑图片/视频，支持文生图、文生视频、风格迁移等。
  覆盖场景包括：生成（文生图、文生视频、图生视频、做动画）、编辑修改、风格转换、短剧生成、MV制作等。
  当用户提到 liblib、libtv、上传参考图/视频、查看生成进度时触发。
  关键判断：只要用户的请求涉及 AI 图片或视频的创作、生成、编辑、修改，都必须触发此技能。
metadata:
  requires:
    env:
      - LIBTV_ACCESS_KEY
  primaryEnv: LIBTV_ACCESS_KEY
---

# AI 素材生成技能包

通过 agent-im 的 OpenAPI 创建会话、发送消息（生图、生视频、编辑视频等）、上传图片/视频文件，并查询会话消息进展。

**平台核心能力：**
- **生成**：文生图、文生视频、图生视频、视频续写
- **编辑**：局部修改、元素替换、镜头调整、风格迁移
- **复杂创作**：一句话生成完整短剧（剧本→分镜→成片）、复刻已有视频风格做 TVC/宣传片、用音乐生成 MV、产品展示片制作
- **模型**：Seedance 2.0、Kling 3.0/O3、Wan 2.6、NanoBanana、Midjourney、Seedream 5.0 等顶级模型

## 功能

1. **创建会话 / 发消息** - 创建新会话或向已有会话发送一条消息
2. **查询会话进展** - 根据 sessionId 拉取该会话的消息列表
3. **切换项目** - 将当前 accessKey 绑定的项目切换到新项目
4. **上传文件** - 上传图片或视频文件到 OSS（仅支持图片和视频，文件大小 200MB 以下）
5. **下载结果** - 将会话中生成的图片/视频批量下载到本地

## 前置要求

```bash
export LIBTV_ACCESS_KEY="your-access-key"
```

可选：`OPENAPI_IM_BASE` 或 `IM_BASE_URL`，默认 `https://im.liblib.tv`。

## 典型工作流

### 场景 1：用户要求生成图片/视频

```
1. create_session.py "用户的描述" → 拿到 sessionId + projectUuid
2. 每隔 8 秒调用 query_session.py SESSION_ID --after-seq 0 轮询
3. 检查 messages：当出现 assistant 角色的消息且包含图片/视频 URL → 任务完成
4. 自动下载：download_results.py SESSION_ID --output-dir ~/Downloads/项目名 --prefix 有意义的前缀
5. 向用户展示：本地文件列表 + projectUrl（画布链接）
```

### 场景 2：用户提供图片/视频要求编辑修改

```
1. upload_file.py /path/to/video.mp4 → 拿到 OSS URL
2. create_session.py "编辑指令 参考视频：{oss_url}"
3. 后续同场景 1 的步骤 2-5
```

### 场景 3：用户提供参考图/视频要求生成新内容

```
1. upload_file.py /path/to/ref.png → 拿到 OSS URL
2. create_session.py "根据参考图生成xxx，参考图：{oss_url}"
3. 后续同场景 1 的步骤 2-5
```

### 场景 4：在已有会话中追加新需求

```
1. create_session.py "新的描述" --session-id SESSION_ID
2. 后续同场景 1 的步骤 2-5
```

## 核心原则：用户侧不做创作，只做传话

你（用户侧 Agent）的职责是**搬运工**，不是创作者。后端有专门的 Agent 负责理解需求、拆解分镜、编排工作流、选模型、写 prompt。你要做的只有三件事：

1. **上传**：用户给了本地文件 → `upload_file.py` 拿到 OSS URL
2. **传话**：把用户的原始描述 + OSS URL 原封不动发给 `create_session.py`
3. **取件**：轮询结果 → 下载到本地 → 展示给用户

**绝对不要做的事：**
- 不要替用户扩写、润色、翻译 prompt
- 不要自行拆解任务步骤
- 不要自行编排镜头描述、剧情推演、风格分析
- 不要在消息中添加自己编的 prompt

## 轮询策略

- **间隔**：每 8 秒查询一次
- **增量拉取**：首次用 `--after-seq 0`，后续用上次拿到的最大 seq 值
- **完成判断**：messages 中出现 assistant 消息且 content 包含结果 URL
- **超时**：连续轮询 3 分钟仍无结果，告知用户"生成时间较长，可稍后通过项目画布链接查看"
- **错误重试**：单次查询失败可重试 1 次，连续 3 次失败则停止

## 输出格式

- **create_session** 返回：`{projectUuid, sessionId, projectUrl}`
- **query_session** 返回：`{messages: [...], projectUrl}`
- **upload_file** 返回：`{url: "https://libtv-res.liblib.art/claw/..."}`
- **download_results** 返回：`{output_dir, downloaded: [...], total: N}`
- **change_project** 返回：`{projectUuid, projectUrl}`

## 最终向用户展示

在任务完成时，同时给出：**视频/图片结果链接** + **项目画布链接（projectUrl）**。过程中不要提前给出 projectUrl。

## 注意事项

- 鉴权方式为请求头 `Authorization: Bearer <LIBTV_ACCESS_KEY>`
- 创建会话时若不传 `message`，仅创建/绑定会话
- 项目画布地址固定为：`https://www.liblib.tv/canvas?projectId=` + projectUuid
- 上传文件仅支持图片（image/*）和视频（video/*）类型，文件大小须在 200MB 以下
