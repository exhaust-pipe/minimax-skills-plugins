# MiniMax Skills

[English](./README.md)

> **Beta** — 本项目正在积极开发中。技能、API 和配置格式可能会在不另行通知的情况下变更。欢迎反馈和贡献。

此包现在是插件化仓库的一部分。此前位于仓库顶层 `skills/` 目录中的 MiniMax 技能，现在位于 `plugins/minimax-skills/skills/`。

面向 AI coding agents 的开发技能。接入你常用的 AI 编程工具，获得结构化、生产级质量的前端、全栈、Android、iOS 和着色器开发指导。

## 技能列表

| 技能&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | 简介 | 来源 |
|---------------------------------------|------|------|
| `frontend-dev` | 全栈前端开发，融合高级 UI 设计、电影级动画（Framer Motion、GSAP）、通过 MiniMax API 生成媒体资源（图片、视频、音频、音乐、TTS）、基于 AIDA 框架的说服力文案、生成艺术（p5.js、Three.js、Canvas）。技术栈：React / Next.js、Tailwind CSS。 | Official |
| `fullstack-dev` | 全栈后端架构与前后端集成。REST API 设计、认证流程（JWT、session、OAuth）、实时功能（SSE、WebSocket）、数据库集成（SQL / NoSQL）、生产环境加固与发布清单。引导式工作流：需求 → 架构 → 实现。 | Official |
| `android-native-dev` | 基于 Material Design 3 的 Android 原生应用开发。Kotlin / Jetpack Compose、自适应布局、Gradle 配置、无障碍（WCAG）、构建问题排查、性能优化与动效系统。 | Official |
| `ios-application-dev` | iOS 应用开发指南，涵盖 UIKit、SnapKit 和 SwiftUI。触控目标、安全区域、导航模式、Dynamic Type、深色模式、无障碍、集合视图，并符合 Apple HIG。 | Official |
| `flutter-dev` | Flutter 跨平台开发，涵盖 widget 模式、Riverpod/Bloc 状态管理、GoRouter 导航、性能优化和测试策略。 | Official |
| `react-native-dev` | React Native 与 Expo 开发指南，涵盖组件、样式、动画、导航、状态管理、表单、网络请求、性能优化、测试、原生能力和工程化（项目结构、部署、SDK 升级、CI/CD）。 | Official |
| `shader-dev` | 全面的 GLSL 着色器技术，用于创建惊艳的视觉效果，包括 ray marching、SDF 建模、流体模拟、粒子系统、程序化生成、光照、后处理等。兼容 ShaderToy。 | Official |
| `gif-sticker-maker` | 将照片（人物、宠物、物品、Logo）转换为 4 张带字幕的动画 GIF 贴纸。Funko Pop / Pop Mart 风格，基于 MiniMax Image & Video Generation API。 | Official |
| `minimax-pdf` | 使用基于 token 的设计系统生成、填写和重排 PDF 文档。支持 CREATE 从零生成精美 PDF（15 种封面风格）、FILL 填写现有表单字段、REFORMAT 将文档重排为新设计。输出可打印，排版和配色由文档类型推导。 | Official |
| `pptx-generator` | 生成、编辑和读取 PowerPoint 演示文稿。支持用 PptxGenJS 从零创建（封面、目录、内容、分节页、总结页）、通过 XML 工作流编辑现有 PPTX，或用 markitdown 提取文本。 | Official |
| `minimax-xlsx` | 打开、创建、读取、分析、编辑或验证 Excel/电子表格文件（.xlsx、.xlsm、.csv、.tsv）。涵盖通过 XML 模板从零创建 xlsx、用 pandas 读取分析、零格式损失编辑现有文件、公式重算、验证和专业财务格式化。 | Official |
| `minimax-docx` | 使用 OpenXML SDK（.NET）专业创建、编辑和格式化 DOCX 文档。三条流水线：从零创建新文档、填写/编辑现有文档内容，或应用模板格式并通过 XSD 验证 gate-check。 | Official |
| `vision-analysis` | 使用视觉 AI 模型分析、描述和提取图像信息。支持描述、OCR、UI mockup 审查、图表数据提取和物体检测。基于 MiniMax VL API，并以 OpenAI GPT-4V 作为 fallback。 | Community |
| `minimax-multimodal-toolkit` | 通过 MiniMax API 生成语音、音乐、视频和图片内容，是 MiniMax 多模态使用场景的统一入口。涵盖 TTS（文本转语音、声音克隆、声音设计、多段合成）、音乐（歌曲、纯音乐）、视频（文生视频、图生视频、首尾帧、主体参考、模板、长视频多场景）、图片（文生图、带角色参考的图生图），以及通过 FFmpeg 进行媒体处理（转换、拼接、裁剪、提取）。 | Official |
| `minimax-music-gen` | 使用 MiniMax Music API 生成人声歌曲、纯音乐和翻唱。两种模式：Basic（一句话输入，生成歌曲）和 Advanced Control（编辑歌词、细化 prompt、规划结构）。支持歌词生成、风格词表、流式播放和迭代反馈。 | Official |
| `buddy-sings` | 让你的 Claude Code pet（/buddy）唱一首个性化歌曲。根据宠物名称和个性生成并缓存独特声线，自动收集上下文（对话、记忆、git 历史）生成主题歌词，并通过 minimax-music-gen 生成音乐。 | Official |
| `minimax-music-playlist` | 通过分析你的音乐品味生成个性化歌单。构建品味画像（曲风、情绪、语言、声线偏好），规划主题曲目，生成歌曲和专辑封面，并根据反馈持续优化画像。 | Official |

## ⭐ Star History

[![Star History Chart](https://api.star-history.com/svg?repos=MiniMax-AI/skills&type=Date)](https://star-history.com/#MiniMax-AI/skills&Date)

## 致谢

本仓库中的部分技能受到开源社区作品启发或派生自这些作品。完整致谢见 [CREDITS_zh.md](../../CREDITS_zh.md)。

## 许可证

[MIT](../../LICENSE)
