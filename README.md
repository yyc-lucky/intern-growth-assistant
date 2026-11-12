# AI 实习成长助手（Intern Assistant）

一个**单文件、零依赖、纯本地**的实习记录与成长沉淀工具：随手记一段话，AI 按 STAR 模型自动分区，确认后沉淀为简历素材、周报与知识库。所有数据只存在你自己的浏览器里。

> **第一次上传 GitHub？** 看 [保姆级操作步骤](docs/github-upload-guide.md)：从注册账号到生成在线网址，每一步点哪里都写清楚了。

<p align="center">
  <img src="docs/screenshot-home.png" width="24%" alt="首页">
  <img src="docs/screenshot-record.png" width="24%" alt="记一笔 · 分区预览">
  <img src="docs/screenshot-detail.png" width="24%" alt="记录详情 · 四栏">
  <img src="docs/screenshot-resume.png" width="24%" alt="简历素材">
</p>

## 特性

- **快速记录 + STAR 分区引擎**：写一段话，按语义线索逐句分到 S 情境 / T 任务 / A 行动 / R 结果四栏，全程四色区分；分错了点一下字母即可改判，也可在「调整分区」里逐句重排。
- **不编造成果**：R 只收录你写过的内容；原文里的数字若没归进结果，只作为候选卡，由你确认；「大概 / 可能」等含糊表述会被拦截提醒。
- **一键简历文案**：四栏自动去重后连成一段可直接粘贴进简历的话，不含任何 STAR 标签。
- **成长沉淀**：简历素材库、周报 / 月报生成、知识库、面试题整理、能力标签统计。
- **AI 助手**：内置对话入口，帮你把记录拼成周报草稿。
- **数据自主**：全部存在浏览器 localStorage，不上传任何服务器；支持 JSON 备份导出 / 导入。

## 快速开始

### 方式一：直接打开

下载 `index.html`，双击用浏览器打开即可（Chrome / Edge / Safari 均可）。无需安装、无需注册登录。

### 方式二：本地起服务

```bash
git clone https://github.com/<你的用户名>/intern-assistant.git
cd intern-assistant
python3 -m http.server 8080
# 打开 http://localhost:8080
```

### 部署到 GitHub Pages（可选）

仓库推送后：**Settings → Pages → Source 选「Deploy from a branch」→ Branch 选 main /(root) → Save**。
稍等片刻即可通过 `https://<你的用户名>.github.io/intern-assistant/` 在线访问。

## 如何推送到你的 GitHub

完整步骤见 **[docs/github-upload-guide.md](docs/github-upload-guide.md)**（含网页上传、命令行上传、Pages 开启、常见报错处理）。

最简版本——在 https://github.com/new 建一个**空仓库**（名称 `intern-assistant`，Public，不勾任何初始化选项），然后在本目录执行：

```bash
git init
git add .
git commit -m "feat: AI 实习成长助手 v1.0"
git branch -M main
git remote add origin https://github.com/<你的用户名>/intern-assistant.git
git push -u origin main
```

## 目录结构

```
intern-assistant/
├── index.html                    # 全部应用：页面 + 样式 + 逻辑都在这一个文件里
├── docs/                         # README 展示截图 + 上传教程
│   └── github-upload-guide.md
├── LICENSE
└── README.md
```

## 技术说明

- 单文件 SPA：HTML + Tailwind CSS（CDN）+ 原生 JavaScript，无构建步骤、无后端。
- STAR 分区引擎：本地规则（线索词 + 结构特征打分），规则透明、结果可人工纠正。
- 数据结构：`profile / internships / records / materials / knowledge / reports / interviews` 等，全部序列化在 localStorage（键名 `aiintern.v2`）。

## 隐私

所有记录、素材、个人信息仅保存在本机浏览器中，应用不包含任何网络请求上报或数据同步；清理浏览器数据会同时清掉记录，请定期在「我的 → 数据管理」导出备份。

## License

[MIT](LICENSE)
