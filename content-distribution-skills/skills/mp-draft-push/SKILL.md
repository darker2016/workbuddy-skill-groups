---
name: mp-draft-push
description: 将现成的文章内容发布到微信公众号草稿箱。当用户说"发布文章"、"发布到草稿箱"、"publish to draft"、"推送到公众号"时触发。
metadata:
  requires:
    env:
      - WECHAT_APPID
      - WECHAT_SECRET
---

# 微信公众号草稿箱发布技能

## 功能说明

接收调用方提供的文章内容，上传封面图（可选），并将文章发布到微信公众号草稿箱。

**不负责**：内容采集、AI 写作、图片生成。

## 所需参数

| 参数 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `title` | string | ✅ | 文章标题（不超过 64 字节，约 21 个中文字符） |
| `digest` | string | ✅ | 文章摘要（显示在分享卡片上） |
| `content_html` | string | ✅ | 文章正文 HTML（使用内联样式） |
| `cover_image_path` | string | ❌ | 封面图本地路径（可选） |

## 执行流程

```
1. 接收参数
       ↓
2. 获取 access_token
       ↓
3. 上传封面图到微信素材库（获取 thumb_media_id）
       ↓
4. 创建草稿（发布到草稿箱）
       ↓
5. 提示用户前往后台检查
```

## 配置信息

- **AppID**: `WECHAT_APPID`（环境变量）
- **AppSecret**: `WECHAT_SECRET`（环境变量）
- **作者**: `WECHAT_AUTHOR`（可选，默认 `koo AI`）

获取 AppID 和 AppSecret：
1. 前往 [微信开发者平台](https://developers.weixin.qq.com/platform/)，微信扫码登录
2. 点击「我的业务 → 公众号/服务号」，进入对应账号详情页
3. 在详情页即可查看 AppID 和 AppSecret

## 封面图处理优先级

若调用方没有提供 `cover_image_path`：
1. **优先使用 `gen_image` 工具生成封面图**：根据文章标题和主题生成 900×383 比例封面
2. 若不可用，检查 `DEFAULT_COVER_URL` 环境变量
3. 均不可用：草稿不含封面

## 注意事项

1. **中文编码**：JSON 必须用 `ensure_ascii=False`，`jq` 默认已处理
2. **标题长度**：最多 64 字节（约 21 个中文字符）
3. **access_token**：有效期 2 小时，每次需重新获取
4. **图片域名**：文章内图片只能使用微信返回的 `mmbiz.qpic.cn` URL
5. 所有样式必须内联（`style="..."`），微信会过滤 `<style>` 标签

## 操作命令

```bash
# 获取 access_token
TOKEN=$(get_wechat_token)

# 上传封面图
MEDIA_RESPONSE=$(upload_wechat_image "$TOKEN" "$cover_image_path")
THUMB_MEDIA_ID=$(echo "$MEDIA_RESPONSE" | jq -r '.media_id')

# 创建草稿
jq -n \
    --arg title "$title" \
    --arg author "${WECHAT_AUTHOR:-koo AI}" \
    --arg digest "$digest" \
    --arg content "$content_html" \
    --arg thumb_media_id "$THUMB_MEDIA_ID" \
    '{
        articles: [{
            title: $title,
            author: $author,
            digest: $digest,
            content: $content,
            thumb_media_id: $thumb_media_id,
            need_open_comment: 1,
            only_fans_can_comment: 0
        }]
    }' > /tmp/draft.json

DRAFT_RESPONSE=$(create_draft "$TOKEN" "/tmp/draft.json")
```

## HTML 内联样式参考

```html
<section style="font-family: -apple-system, sans-serif; line-height: 1.8; color: #333; padding: 15px;">
  <p style="margin-bottom: 20px;">段落内容</p>
  <h2 style="border-bottom: 1px solid #eee; padding-bottom: 8px;">标题</h2>
  <p style="text-align: center; margin: 25px 0;">
    <img src="{mmbiz_img_url}" style="max-width: 100%; border-radius: 6px;">
  </p>
  <blockquote style="background: #f6f8fa; border-left: 4px solid #ddd; padding: 12px 16px;">
    引用内容
  </blockquote>
</section>
```
