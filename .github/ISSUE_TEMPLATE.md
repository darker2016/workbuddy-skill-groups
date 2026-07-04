name: 移除请求 / Removal request（版权 / DMCA）
description: 原始作者发现自己作品被错误收录 / 需要修改 / 需要移除
labels: [removal, legal]
body:
  - type: markdown
    attributes:
      value: |
        感谢你联系本仓库维护者。我们尊重第三方版权，会在 **5 个工作日内** 对核实请求做出响应。
  - type: input
    id: contact
    attributes:
      label: 联系方式
      description: 邮箱或其他能联系到你的方式（不公开，仅供我们核实请求真实性）
      placeholder: you@example.com
    validations:
      required: true
  - type: input
    id: original_link
    attributes:
      label: 原始作品链接
      description: 你在哪个平台发布了原始作品 / 你的工作室链接
      placeholder: https://github.com/your/repo 或 WorkBuddy 个人页链接
    validations:
      required: true
  - type: textarea
    id: description
    attributes:
      label: 具体问题描述
      description: 请说明哪些目录 / 文件涉及你的版权，以及你期望的修改（署名修正 / 内容移除 / 替换内容 等）。
    validations:
      required: true
  - type: checkboxes
    id: confirmation
    attributes:
      label: 声明确认
      options:
        - label: 我确认我是原始作品作者或其合法授权代表，上述信息真实有效
          required: true
        - label: 我已知晓本仓库按 MIT 许可证开源；署名修正不会改变许可证类型
          required: false
