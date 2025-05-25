<h1 align="center">欢迎使用&nbsp;&nbsp;Cursor Auto Helper 👋</h1>
<p>
  <img alt="Version" src="https://img.shields.io/badge/version-2.1.0-blue.svg?cacheSeconds=2592000" />
  <a href="#" target="_blank">
    <img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-yellow.svg" />
  </a>
  <img alt="Cursor Version" src="https://img.shields.io/badge/Cursor-0.49.6-blue.svg" />
</p>

> Cursor自动继续工具，Cursor自动重试，Cursor自动确认，Cursor用量统计，Cursor对话助手，Cursor增强工具，Cursor辅助工具，Cursor自动化工具，Cursor Auto Continue Tool，Cursor Auto Retry Tool，Cursor Auto Confirm Tool，Cursor Usage Statistics Tool，Cursor Efficiency Tool，Cursor Assistant Tool，Cursor Automation Tool，after 25 tool calls，Cursor Tool Call Limit🔧🤖🚀
> 

## 🏠 [Homepage](https://github.com/pen9un/cursor-auto-helper)

Cursor Auto Helper 是一款专为 Cursor IDE 打造的自动化增强工具，能够实时显示用量、自动处理 25 次对话限制、网络连接失败、确认提示等场景，让你的开发体验更加流畅。

**视频演示：** [Cursor Auto Helper 演示视频](https://www.bilibili.com/video/BV1cajKzCEzv/)

提示词质量高，项目需求规划的好，这个程序就可以让 Cursor 在无需人工干预的情况下自动完成一个项目。

> ⚠️ **版本限制**：目前仅在 Cursor 0.49.6 版本上开发测试通过，其他版本可能存在兼容性问题。

## 🚀 使用说明

欢迎Star支持，如有问题请提 [Issues](https://github.com/pen9un/cursor-auto-helper/issues)。

<img src="./resource/image/cursor-auto-helper-2.png" alt="cursor-auto-helper" />

### 📝 配置文件说明

配置文件 `config.ini` 用于自定义自动化行为，支持以下配置项：

#### 基础配置
```ini
[common]
log_enable = true     # 是否启用日志，如不想记录日志可改为false

[cursor]
path = C:\Path\To\Cursor.exe  # Cursor IDE安装路径，程序会自动查找Cursor路径，找不到时会有提示，修改此项即可
```

#### 自动动作配置
每个自动动作以 `action名称.` 为前缀，支持以下字段：

- `type`：动作类型
  - `click`：点击按钮
  - `input_and_submit`：输入并提交

- `text` / `text_list`：匹配的文本内容
  - `text`：单个字符串
  - `text_list`：| 分隔的多个字符串，页面内容包含任一项即触发

- `button_selector`：需要点击的按钮的CSS选择器（仅`click`类型需要）
- `button_text`：按钮文本内容（可选，进一步限定按钮）
- `input_box_selector`：输入框的CSS选择器（`input_and_submit`类型需要）
- `input_content`：需要自动输入的内容
- `submit_btn_selector`：提交按钮的CSS选择器
- `delay`：动作执行前的延迟（毫秒），可用于等待页面渲染

##### 配置示例
```ini
[auto_actions]
# 连接失败自动重试
action_retry.type = "click"
action_retry.text = "Connection failed. If the problem persists, please check your internet connection or VPN"
action_retry.button_selector = "div.anysphere-secondary-button"
action_retry.button_text = "Try again"
action_retry.delay = 3000

# after 25 tool calls
action_continue.type = "input_and_submit"
action_continue.text_list = "agent after 25 tool calls"
action_continue.input_box_selector = ".full-input-box.undefined"
action_continue.input_content = "请继续"
action_continue.submit_btn_selector = ".codicon-arrow-up-two"
action_continue.delay = 1000

# 自动确认继续
action_need_continue.type = "input_and_submit"
action_need_continue.text_list = "是否需要|是否继续|需要我|请告诉我"
action_need_continue.input_box_selector = ".full-input-box.undefined"
action_need_continue.input_content = "请继续后续开发，并实时记录更新开发进度"
action_need_continue.submit_btn_selector = ".codicon-arrow-up-two"
action_need_continue.delay = 1000
```

> **注意：**
> 1. 每个 action 的名称（如`action_retry`、`action_continue`）可自定义，但同一 action 的所有字段前缀需一致
> 2. CSS 选择器建议用浏览器开发者工具定位，确保准确
> 3. 配置文件修改后需要重启程序才能生效

## 🌟 特色优势

### 🔥 智能自动化
- **自动继续**：自动处理25次对话限制
- **自动重试**：网络连接失败自动重试
- **自动确认**：智能处理确认提示
- **实时统计**：对话用量实时监控

### 🚀 高度自定义
- **场景配置**：支持自定义自动化场景
- **灵活规则**：可配置的自动化规则
- **智能匹配**：支持多种匹配模式
- **实时监控**：页面内容实时监控

### 💡 强大日志系统
- **多级别日志**：DEBUG/INFO/SUCCESS/WARNING/ERROR/CRITICAL
- **彩色输出**：终端彩色日志显示
- **文件记录**：按日期生成日志文件
- **实时面板**：可拖拽的日志显示面板

### 🔒 版本兼容
- **稳定版本**：基于 Cursor 0.49.6 开发
- **功能验证**：核心功能完整测试
- **性能优化**：针对特定版本优化
- **持续更新**：跟进 Cursor 版本更新

## 🌟 主要功能

### 🤖 自动继续对话
- **25次限制**：自动处理 Cursor 25 次对话限制
- **智能识别**：自动识别 "agent after 25 tool calls" 提示
- **自动继续**：自动输入并提交继续指令
- **连续对话**：支持多轮连续对话

### 🎨 自动重试连接
- **网络异常**：自动检测网络连接失败
- **智能重试**：自动点击重试按钮
- **状态监控**：实时监控连接状态
- **自动恢复**：网络恢复自动继续

### 📱 自动确认提示
- **智能识别**：自动识别确认提示场景
- **场景匹配**：支持多种确认场景
- **自动确认**：自动处理确认提示
- **自定义响应**：支持自定义确认内容

### 🛍️ 用量统计
- **实时统计**：对话次数实时统计
- **用量监控**：Cursor 用量实时监控
- **数据记录**：用量数据自动记录
- **统计展示**：用量数据可视化展示

## 🔮效果展示

### 🤖 自动继续对话

<img src="./resource/image/auto-continue.png" alt="auto-continue" />

### 🚀 Cursor自动完成程序展示

从项目需求到完整实现，全程无需人工干预：

<img src="./resource/image/auto-complete.png" alt="auto-complete" />

## 🎯 应用场景

### 💼 长对话开发
- 自动处理 25 次对话限制
- 支持连续长对话开发
- 自动继续对话流程
- 提升开发效率

### 👥 网络不稳定
- 自动处理网络异常
- 智能重试连接
- 自动恢复对话
- 保证开发连续性

### 🏢 确认场景
- 自动处理确认提示
- 智能识别确认场景
- 自动确认继续
- 减少人工干预

确认场景示例：

<img src="./resource/image/confirm-continue.png" alt="confirm-continue" />

### 📚 用量监控
- 实时统计对话次数
- 监控Cursor用量
- 记录使用数据
- 优化使用效率

终端用量显示：

<img src="./resource/image/cursor-auto-helper-1.png" alt="cursor-auto-helper-1" />

Cursor IDE 用量显示：

<img src="./resource/image/cursor-auto-helper-logs.png" alt="cursor-auto-helper-logs" />

## 📖更新日志

- 2025-05-21 发布 v2.1 版本，重构架构，支持多平台，增加实时显示用量功能等
- 2025-04-25 完成 v1.0 版本，自动处理 25 次对话限制、网络连接失败、确认提示等场景
- 2025-04-20 项目启动

## 🤝作者

👤 **pen9un**

* Website: https://github.com/pen9un/
* Github: [@pen9un](https://github.com/pen9un)

## ❤️支持

如果觉得此项目有用，请点一个免费的小 ⭐️⭐️

## ✨Star History

[![Star History Chart](https://api.star-history.com/svg?repos=pen9un/cursor-auto-helper&type=Date)](https://star-history.com/#pen9un/cursor-auto-helper&Date)

## 💹 访问量统计

![Visitor Count](https://profile-counter.glitch.me/pen9un/count.svg) 