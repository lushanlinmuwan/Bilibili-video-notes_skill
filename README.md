# B站学习视频笔记生成器 (bilibili-video-notes)

一键将B站学习视频自动转换为结构化学习笔记的豆包 Skill。

## ✨ 功能特点

- 🎬 **自动下载**：通过 PeanutDL 网站自动解析并下载 720P B站视频
- 🎵 **音频提取**：自动将视频转换为 MP3 音频文件
- 📝 **AI 智能纪要**：自动生成飞书智能纪要文档（带逐字稿）
- 📚 **结构化笔记**：整理为 Markdown 格式的学习笔记，重点突出、方便复习
- 🌐 **三种语言版本**：支持中文笔记、原语言笔记、双语对照三种模式
- 📦 **批量分P支持**：可批量处理B站合集的多个分P视频
- 📁 **自动整理**：视频、音频、笔记统一保存到指定文件夹

## 🎯 适用场景

- 语言学习类视频（西语、英语、日语等）
- 编程/技术教程
- 学术课程录屏
- 职业技能培训
- 任何你想快速总结并做笔记的B站学习视频

## 📋 完整工作流

```
B站链接 → 自动解析下载视频 → 提取MP3音频 → AI转写生成智能纪要 → 整理结构化Markdown笔记
```

1. **确认参数**：询问保存路径、处理范围、笔记语言版本
2. **下载视频**：通过 PeanutDL 网站自动解析下载 720P 视频
3. **提取音频**：从视频中分离音轨，生成 MP3 文件
4. **AI 智能纪要**：上传音频，自动生成飞书智能纪要文档
5. **整理笔记**：按照模板整理为结构化 Markdown 学习笔记
6. **交付产物**：视频 + 音频 + 笔记 + 在线纪要链接

## 🚀 安装方法

### 前提条件

- 已安装 **豆包办公模式（Doubao Work）**
- 已登录豆包账号

### 安装步骤

1. **下载本仓库**

   - 点击 `Code` → `Download ZIP` 下载压缩包
   - 或者 git clone：

     ```bash
     git clone https://github.com/你的用户名/bilibili-video-notes.git
     ```

2. **解压到正确目录**
   把整个 `bilibili-video-notes` 文件夹放到你的豆包 user_skills 目录下：

   ```
   # Windows 路径
   C:\Users\你的用户名\AppData\Local\Doubao\User Data\Default\.doubao\agent_mode\workspace\.user_skills\bilibili-video-notes
   ```

   ```
   # macOS 路径
   ~/Library/Application Support/Doubao/User Data/Default/.doubao/agent_mode/workspace/.user_skills/bilibili-video-notes
   ```

3. **重启豆包**
   重启豆包办公模式，Skill 会自动被识别加载。

## 📖 使用方法

### 基本用法

直接在豆包对话中发送B站视频链接 + 你的需求，例如：

```
帮我总结这个视频：
https://www.bilibili.com/video/BV1xxxxxxxxx/?p=1
```

或者更具体：

```
下载这个视频，转成MP3，然后给我做一份中英双语对照的学习笔记，保存到我的西语文件夹。
```

### 触发关键词

- "总结这个视频"
- "帮我做笔记"
- "提取字幕"
- "下载这个视频学习"
- "把这个视频转成MP3"

### 支持的笔记语言版本

| 版本        | 说明              | 适用场景          |
| --------- | --------------- | ------------- |
| **中文笔记**  | 全部中文，专业术语保留原文   | 快速掌握内容、技术类视频  |
| **原语言笔记** | 全部用视频原语言撰写      | 语言学习类视频，顺便练阅读 |
| **双语对照**  | 原语言 + 中文并排，三列表格 | 语言学习、精读场景     |

## 📁 文件结构

```
bilibili-video-notes/
├── SKILL.md                          # Skill 主入口（触发条件 + 核心流程）
├── README.md                         # 本文件
├── LICENSE                           # 开源协议
└── references/
    ├── download-workflow.md           # PeanutDL 下载详细步骤
    ├── note-template.md              # 学习笔记模板规范
    └── troubleshooting.md            # 常见问题处理手册
```

## 🎓 效果示例

以西班牙语初级课程第9集为例，生成的笔记包含：

- 按时间问候词汇表（中西对照 + 发音要点）
- 打招呼与告别用语
- 自我介绍表达
- 语法要点（动词变位、否定规则）
- 礼貌用语大全
- 学习建议与课程金句

## ❓ 常见问题

### Q: 为什么需要验证码？

A: PeanutDL 网站有人机验证，需要你手动完成一次，这是正常的反爬机制。

### Q: 下载的视频清晰度是多少？

A: 默认 720P 高清，取决于原视频的最高可用清晰度。

### Q: 支持其他平台吗？

A: 目前主要支持B站，PeanutDL 网站本身也支持抖音、TikTok，后续会扩展。

### Q: 批量分P怎么用？

A: 告诉豆包你要处理第几集到第几集，它会自动依次处理每一集。

## 🤝 贡献指南

欢迎提 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建你的功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交你的改动 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

## 📄 License

本项目采用 MIT 协议 - 详见 [LICENSE](LICENSE) 文件

## ⭐ 如果这个项目对你有帮助，欢迎点个Star！
