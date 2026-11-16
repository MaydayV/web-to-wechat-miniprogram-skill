# 网页转微信小程序开发 Skill

一个用于 Codex 的网站研究与微信小程序全栈迁移 Skill。用户可以提供公开网站 URL、Web 源码仓库，或已有小程序工程。Skill 会先盘点网站解决的问题、页面与任务流程，再设计原创产品体验，并以微信小程序原生页面和组件实现。

本 Skill 不把网页嵌入 WebView，也不把工作限定为前端换皮。网站可以启发选题和高层功能；页面视觉、品牌、文案和内容由小程序重新设计。若功能依赖真实数据，还会检查 API、认证、服务端路由和数据层，并按需要适配现有后端。

## 能力范围

- **分层网站盘点**：优先检查站点地图、同源链接、HTML、路由、公开脚本、状态和数据请求；只在动态页面、表单分支或静态证据不足时控制浏览器补查。
- **原创产品设计**：从参考站提炼用户问题、选题和核心任务，整理成原创概念与改进点；不复制参考站的配色、布局、字体、图标、动效、文案、品牌或专有内容。
- **原生页面转换**：将 HTML/React/Vue 的结构、事件、列表、表单、路由和状态映射到 WXML/WXSS/JS/TS 或目标项目现有的小程序框架；检查 `app.json`、`miniprogramRoot` 和页面文件集合。
- **API 与后端适配**：追踪页面事件到请求封装、服务端路由、业务逻辑和数据库；识别列表、详情、筛选、分页、写入、状态变更、统计、上传和身份接口。优先复用现有 API，必要时适配后端，不凭界面猜 endpoint。
- **验证与恢复**：静态检查和微信开发者工具 CLI 优先；GUI/模拟器用于 CLI 无法覆盖的运行态问题。区分代码错误、DevTools 环境问题和服务端/API 故障。
- **心理测评边界**：可创建原创自我观察工具，但未经验证的内容不标成临床量表，不编造分数或诊断解释；敏感答案默认最小收集并优先本机处理。

## 工作流程

1. 确认 Web、API/后端和小程序各自的代码根目录，检查 Git 状态和项目约定。
2. 静态优先梳理页面、交互、数据和接口；浏览器只用于验证静态分析无法确认的动态状态。
3. 形成页面/API/状态映射，提炼原创产品方案和面向用户的改进点。
4. 用小程序原生能力实现主要用户闭环；需要真实业务逻辑时同时完成请求层和必要的服务端适配。
5. 运行与改动层级匹配的检查，报告本机静态检查、API 联调、DevTools/模拟器及真机证据。

## 按需选用工具

| 任务 | 优先方式 | 使用边界 |
| --- | --- | --- |
| 本地源码分析 | Shell、`rg`、Git 和项目文档 | 从调用点追到真实实现，保留已有未提交改动 |
| 公开网站结构 | HTTP/页面读取、站点地图和 HTML/脚本分析 | 遵守站点访问限制，不猜路径暴力抓取 |
| 动态页面/状态 | 可用的浏览器或 UI 自动化 | 只操作需要验证的页面和状态，不采集无关用户数据 |
| 微信平台行为 | 当前微信官方文档 | 对 API、基础库、域名、隐私等变化点查官方依据 |
| 小程序编译与运行 | 微信开发者工具 CLI `open`/`preview`，必要时 GUI/模拟器 | CLI 编译通过不等于真实运行通过；工具阻塞要单独归因 |
| API/后端 | 源码搜索、接口文档、OpenAPI/契约、项目现有测试工具 | 接口推断标待确认，不能让 Mock 冒充生产后端 |

Skill 会先检查当前环境实际可用的工具；不会假设每种工具都已安装或授权。

## 使用方式

将本仓库克隆到 Codex 可发现的 Skills 目录，或把本目录复制到该目录：

```bash
git clone https://github.com/MaydayV/web-to-wechat-miniprogram-skill.git ~/.codex/skills/web-to-wechat-miniprogram
```

之后可通过 Skill 自动匹配或显式调用 `web-to-wechat-miniprogram`。详细流程见 [SKILL.md](SKILL.md)；网站盘点、WXML 映射、API/后端与 DevTools 方法分别见 [迁移工作流](references/url-to-miniprogram-workflow.md) 和 [全栈/API 工作流](references/full-stack-and-api.md)。

## 文件结构

```text
SKILL.md
references/
  url-to-miniprogram-workflow.md
  full-stack-and-api.md
  source-analysis.md
```

`source-analysis.md` 只记录融合思路和来源链接。本公开仓库不包含那三个参考仓库的副本、源代码、脚本或测试夹具。

## 融合来源

- [launch-wechat-miniprogram](https://github.com/niuhuoshan/launch-wechat-miniprogram)：小程序项目阶段、状态、安全与验收方法。
- [miniprogram-skills](https://github.com/Sun-sunshine06/miniprogram-skills)：脚手架、CLI/GUI 验证、故障恢复、导航分组与文案精简。
- [my-skills](https://github.com/raidenfc/my-skills)：HTML 到 WXML 映射、页面交叉盘点、API 需求发现、请求层与接口契约治理。
