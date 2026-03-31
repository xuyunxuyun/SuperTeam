<!--

SPDX-License-Identifier: CC-BY-NC-SA-4.0

本文件是“汉末废柴堆 · 超级团队组建系统”的一部分。

完整项目受 CC BY-NC-SA 4.0 许可证保护，详见根目录 LICENSE 文件。

本项目核心设计思想、架构方案、方法论受 NOTICE 文件独立保护。

个人可免费使用，严禁用于商业目的。

商业授权请联系：xxuuyyuunn@sina.com

-->

# 超级团队组建插件：文心雕文龙

**版本历史**

| **版本号** | **过程节点说明** | **修订人** | **修订日期** | **修订内容** |
| --- | --- | --- | --- | --- |
| V0.1.0 | 初稿创建 | 盘古开插件 | 2026-03-24 | 根据用户需求生成 |
| V0.1.1 | 样式固化 | 盘古开插件 | 2026-03-25 | 增加“企微群聊风”文档样式，将6种样式CSS规范固化至插件，确保输出一致性 |
| V0.1.2 | 样式固化 | 盘古开插件 | 2026-03-31 | 增加“科技展示风”文档样式，固定配色、色块、列表、表格、气泡、注释、代码等样式，确保输出一致性，增加公式支持 |
|  |  |  |  |  |

## **插件名称**

**文心雕文龙**

## **一、定位与价值**

这是一个集成在团队执行流程中的**文档格式化插件**。当用户需要保存或展示文档时，自动将团队产出的Markdown内容转换为高质量HTML文档，支持多种风格样式，用户可直接在浏览器查看或使用Word打开编辑。

**核心价值**：

- 让团队输出从“纯文本”升级为“高质量文档”
- 保留格式、便于保存、支持编辑
- 谁制作谁交付，不增加协作成本
- **样式规范固化**：所有风格样式已固化至插件，每次生成结果一致

**服务范围**：适用于会议纪要、技术方案、需求文档、复盘报告、通用文档、群聊实录等所有团队产出物。

## **二、插件启动流程**

### **启动条件**

本插件为**集成型插件**，不设单独激活指令。当用户在对话中提出以下关键词或表达此意向时，由当前执行任务的团队成员自动触发：

**触发词列表**：

- “展示文档”
- “输出文档”
- “保存文档”
- “下载文档”
- “给我一份正式版”
- “导出这个”
- “生成文档”

### **执行流程**

**步骤1：内容采集**

- 自动抓取当前对话中团队产出的核心内容
- 如有多个版本，以最新确认的版本为准
- 保留原有Markdown结构（标题、列表、表格、代码块、引用等）

**步骤2：文档类型识别**

- 根据内容特征自动判断文档类型，或询问用户确认
- 类型包括：会议纪要、技术方案、需求文档、复盘报告、通用文档、群聊实录
- 按以下推荐表为用户提供风格建议：

| 识别关键词 | 判定类型 | 推荐风格 |
| --- | --- | --- |
| 会议、纪要、讨论、同步、周会 | 会议纪要 | 商务正式风 |
| API、接口、架构、技术方案、代码 | 技术方案 | 技术文档风 |
| 需求、PRD、功能、用户故事、验收 | 需求文档 | 产品需求风 |
| 复盘、总结、反思、回顾、教训 | 复盘报告 | 复盘报告风 |
| 通用、说明、指南、手册 | 通用文档 | 简约阅读风 |
| 群聊、聊天记录、对话实录、@所有人 | 群聊实录 | 企微群聊风 |
| 路演、汇报、展示、AI、产品发布 | 对外展示 | 科技展示风 |

**步骤3：样式风格选择**

- 向用户展示6种风格选项，由用户选择
- 选项根据文档类型动态推荐，但用户可自由选择任一风格
- **样式规范已固化，每次选择同一风格输出结果完全一致**

**步骤4：HTML生成**

- 按选定风格调用对应CSS规范生成完整HTML文档
- 内置响应式布局，适配电脑、平板、手机
- Word打开时保留基础格式和样式
- 若选择“企微群聊风”，自动按规则生成头像背景色，并识别发送者（导出者右对齐，其他人左对齐）

**步骤5：交付与提示**

- 直接在对话中输出HTML代码块
- 附保存提示：“复制以上代码 → 保存为 .html 文件 → 浏览器打开或Word编辑”

### **关键规则**

- **谁制作谁输出**：文档的制作者直接交付HTML，不经过其他团队中转
- **即时响应**：用户提出保存需求后立即生成
- **格式保留**：Markdown的标题层级、列表、表格、代码高亮、引用块全部保留
- **样式一致**：所有风格CSS规范已固化，保证每次生成结果一致
- **无侵入性**：不改变团队原有的工作流程，仅在用户需要时增加输出环节

## **三、核心能力**

### **能力清单**

1. **智能内容采集**：自动抓取当前对话中的核心产出内容
2. **文档类型识别**：根据内容特征判断文档类型，适配不同展示需求
3. **多风格HTML渲染**：内置6种文档风格，CSS规范固化，一键切换
4. **响应式布局**：自动适配不同设备屏幕尺寸
5. **Word兼容**：生成的HTML在Word中打开时保留基础格式

## **四、样式规范库**

### 风格1：商务正式风

**适用场景**：对外汇报、呈报领导、正式会议纪要

**设计原则**：庄重严肃、可打印、Times字体、页眉页脚

```css
/* 商务正式风 CSS 规范 — 固化版 */
body {
    font-family: 'Times New Roman', '宋体', SimSun, serif;
    line-height: 1.6;
    color: #1a2a3a;
    background: #ffffff;
    max-width: 1000px;
    margin: 40px auto;
    padding: 20px;
}
/* 页眉 */
.document-header {
    border-bottom: 2px solid #2c7cb6;
    padding-bottom: 12px;
    margin-bottom: 24px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
}
.company-name { font-size: 0.9rem; color: #5a6e7c; }
.doc-title { font-size: 1.2rem; font-weight: 600; color: #2c7cb6; }
/* 页脚 */
.document-footer {
    border-top: 1px solid #e0e6ed;
    margin-top: 48px;
    padding-top: 16px;
    font-size: 0.75rem;
    color: #8a9bb0;
    text-align: center;
}
/* 印章样式（可选） */
.stamp {
    display: inline-block;
    border: 2px solid #c2410c;
    color: #c2410c;
    padding: 4px 12px;
    border-radius: 30px;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 2px;
    background: #fffaf5;
}
/* 标题 */
h1 { font-size: 1.8rem; border-left: 4px solid #2c7cb6; padding-left: 16px; margin-top: 32px; color: #1e4663; }
h2 { font-size: 1.4rem; border-bottom: 2px solid #e6edf4; padding-bottom: 8px; margin-top: 28px; color: #2c5a7a; }
h3 { font-size: 1.2rem; margin-top: 20px; color: #3a6e8c; }
/* 表格 */
table { border-collapse: collapse; width: 100%; margin: 16px 0; }
th, td { border: 1px solid #d0dae8; padding: 10px 12px; text-align: left; }
th { background-color: #f0f4fa; font-weight: 600; }
tr:nth-child(even) { background-color: #fafcff; }
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 6px 0; line-height: 1.5; }
ul ul, ol ol { margin: 4px 0; }
/* 代码 */
code { background: #f2f4f8; padding: 2px 6px; border-radius: 4px; font-family: monospace; font-size: 0.9em; }
pre { background: #f6f8fa; padding: 16px; border-radius: 8px; overflow-x: auto; }
pre code { background: transparent; padding: 0; }
/* 引用 */
blockquote { border-left: 3px solid #2c7cb6; margin: 16px 0; padding-left: 16px; color: #4a627a; }
@media print {
    body { margin: 0; }
    .stamp { border-color: #999; color: #999; }
}
```

### 风格2：技术文档风

**适用场景**：研发内部、API文档、代码说明

**设计原则**：专业、代码友好、深色代码块、版本号表格

```css
/* 技术文档风 CSS 规范 — 固化版 */
body {
    font-family: 'SF Mono', 'Fira Code', 'Consolas', monospace;
    line-height: 1.5;
    background: #f9fafc;
    color: #1e2f3e;
    max-width: 1100px;
    margin: 30px auto;
    padding: 20px;
}
/* 版本号表格（固定样式） */
.version-table {
    width: 100%;
    border-collapse: collapse;
    background: white;
    margin: 20px 0;
}
.version-table th, .version-table td {
    border: 1px solid #cbd5e1;
    padding: 8px 12px;
}
.version-table th {
    background: #eef2ff;
    font-weight: 600;
}
/* 标题 */
h1 { font-size: 1.6rem; border-bottom: 2px solid #3b82f6; padding-bottom: 8px; color: #1e3a8a; font-weight: 600; }
h2 { font-size: 1.3rem; margin-top: 28px; color: #2563eb; }
h3 { font-size: 1.1rem; color: #3b82f6; }
/* 代码块 — 深色固定 */
pre {
    background: #1e293b;
    color: #e2e8f0;
    padding: 16px;
    border-radius: 10px;
    overflow-x: auto;
    font-size: 0.85rem;
    font-family: 'SF Mono', 'Fira Code', monospace;
}
code {
    background: #eef2ff;
    padding: 2px 6px;
    border-radius: 5px;
    font-family: monospace;
    font-size: 0.9em;
}
pre code {
    background: transparent;
    padding: 0;
    color: inherit;
}
/* 表格 */
table:not(.version-table) {
    border-collapse: collapse;
    width: 100%;
    background: white;
}
th, td {
    border: 1px solid #cbd5e1;
    padding: 8px 12px;
}
th {
    background: #eef2ff;
}
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 4px 0; }
/* 引用 */
blockquote {
    border-left: 3px solid #3b82f6;
    background: #f1f5f9;
    padding: 12px 16px;
    margin: 16px 0;
}
```

### 风格3：产品需求风

**适用场景**：PRD、需求文档、功能说明

**设计原则**：结构化、可追溯、用户故事框、验收标准色块

```css
/* 产品需求风 CSS 规范 — 固化版 */
body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    line-height: 1.5;
    background: #f5f7fb;
    color: #1f2f3e;
    padding: 32px 24px;
}
.document-container {
    max-width: 1000px;
    margin: 0 auto;
    background: white;
    border-radius: 24px;
    box-shadow: 0 8px 24px rgba(0,0,0,0.05);
    padding: 32px 40px;
}
/* 用户故事框 — 固定样式 */
.user-story {
    background: #f0f9ff;
    border-left: 4px solid #3b82f6;
    padding: 16px 20px;
    border-radius: 12px;
    margin: 20px 0;
}
.user-story::before {
    content: "📖 用户故事";
    display: block;
    font-weight: 600;
    color: #3b82f6;
    margin-bottom: 8px;
    font-size: 0.85rem;
}
/* 验收标准色块 — 固定样式 */
.acceptance-criteria {
    background: #fefce8;
    border-left: 4px solid #eab308;
    padding: 16px 20px;
    border-radius: 12px;
    margin: 20px 0;
}
.acceptance-criteria::before {
    content: "✅ 验收标准";
    display: block;
    font-weight: 600;
    color: #ca8a04;
    margin-bottom: 8px;
    font-size: 0.85rem;
}
/* 功能清单表格 */
.feature-table {
    width: 100%;
    border-collapse: collapse;
    background: white;
    border-radius: 12px;
    overflow: hidden;
    margin: 20px 0;
}
.feature-table th, .feature-table td {
    border: 1px solid #e2e8f0;
    padding: 12px;
    text-align: left;
}
.feature-table th {
    background: #f1f5f9;
    font-weight: 600;
}
/* 标题 */
h1 { font-size: 1.8rem; font-weight: 700; color: #0f172a; margin-bottom: 24px; }
h2 { font-size: 1.3rem; font-weight: 600; background: #f8fafc; padding: 10px 16px; border-radius: 12px; margin-top: 32px; color: #0f3b5c; }
h3 { font-size: 1.1rem; margin-top: 24px; color: #2563eb; }
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 6px 0; }
/* 代码 */
code { background: #f1f5f9; padding: 2px 6px; border-radius: 6px; font-family: monospace; }
```

### 风格4：复盘报告风

**适用场景**：项目复盘、工作总结

**设计原则**：时间轴、问题-改进双栏、结论高亮

```css
/* 复盘报告风 CSS 规范 — 固化版 */
body {
    font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
    background: #fef9f0;
    color: #2c3e2f;
    padding: 40px 20px;
}
.report-container {
    max-width: 1000px;
    margin: 0 auto;
    background: #ffffffea;
    border-radius: 20px;
    padding: 32px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.05);
}
/* 标题 */
h1 {
    font-size: 2rem;
    border-left: 6px solid #c2410c;
    padding-left: 20px;
    color: #431407;
}
/* 时间轴 — 固定样式 */
.timeline {
    border-left: 3px solid #f97316;
    margin: 24px 0;
    padding-left: 24px;
}
.milestone {
    margin-bottom: 28px;
}
.milestone-date {
    font-weight: bold;
    color: #c2410c;
    display: block;
    margin-bottom: 8px;
}
/* 问题-改进双栏 — 固定样式 */
.two-columns {
    display: flex;
    gap: 24px;
    margin: 24px 0;
    flex-wrap: wrap;
}
.problem-box {
    flex: 1;
    background: #fff1f0;
    padding: 20px;
    border-radius: 16px;
}
.problem-box::before {
    content: "⚠️ 问题";
    display: block;
    font-weight: 700;
    color: #c2410c;
    margin-bottom: 12px;
}
.improve-box {
    flex: 1;
    background: #ecfdf5;
    padding: 20px;
    border-radius: 16px;
}
.improve-box::before {
    content: "📈 改进";
    display: block;
    font-weight: 700;
    color: #0d9488;
    margin-bottom: 12px;
}
/* 结论高亮框 */
.conclusion {
    background: #fffbeb;
    border-top: 4px solid #f97316;
    padding: 20px;
    margin-top: 32px;
    border-radius: 16px;
    font-weight: 500;
}
.conclusion::before {
    content: "🎯 关键结论";
    display: block;
    font-weight: 700;
    color: #f97316;
    margin-bottom: 12px;
}
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 6px 0; }
/* 表格 */
table { width: 100%; border-collapse: collapse; margin: 20px 0; }
th, td { border: 1px solid #e2e8f0; padding: 10px; }
th { background: #fef3e8; }
@media (max-width: 700px) {
    .two-columns { flex-direction: column; }
}
```

### 风格5：简约阅读风

**适用场景**：知识沉淀、个人笔记、长文阅读

**设计原则**：极简、沉浸、纯文字+留白、无任何装饰

```css
/* 简约阅读风 CSS 规范 — 固化版 */
body {
    font-family: 'Georgia', 'Times New Roman', serif;
    line-height: 1.8;
    background: #fefefe;
    color: #2c3e4e;
    max-width: 760px;
    margin: 48px auto;
    padding: 0 24px;
}
/* 无边框、无色块、无阴影 — 极简 */
h1 {
    font-size: 2rem;
    font-weight: 600;
    margin-top: 48px;
    margin-bottom: 24px;
    color: #1e4663;
    border-bottom: none;
}
h2 {
    font-size: 1.6rem;
    margin-top: 40px;
    color: #2c5a7a;
    border-bottom: none;
}
h3 {
    font-size: 1.3rem;
    margin-top: 32px;
    color: #3a6e8c;
}
p {
    margin-bottom: 1.4em;
}
/* 列表 — 极简，无额外装饰 */
ul, ol {
    margin: 16px 0;
    padding-left: 2em;
}
li {
    margin: 8px 0;
}
/* 引用 — 极简斜体 */
blockquote {
    font-style: italic;
    border-left: 2px solid #e2e8f0;
    padding-left: 24px;
    margin: 24px 0;
    color: #4b5565;
}
/* 代码 — 浅灰背景，无圆角 */
code {
    background: #f4f4f5;
    padding: 2px 5px;
    font-family: monospace;
    font-size: 0.9em;
    border-radius: 0;
}
pre {
    background: #f9fafb;
    padding: 20px;
    overflow-x: auto;
    border-radius: 0;
    border-left: 2px solid #e2e8f0;
}
/* 表格 — 极简，只有下边框 */
table {
    width: 100%;
    border-collapse: collapse;
    margin: 24px 0;
}
th, td {
    border-bottom: 1px solid #e2e8f0;
    padding: 12px;
    text-align: left;
}
th {
    font-weight: 600;
}
/* 无任何色块、无卡片、无阴影 */
```

### 风格6：科技展示风

**适用场景**：对外汇报、AI产品发布、技术方案路演

**设计原则**：科技蓝调、渐变背景、微光效、可切换深色护眼模式

```css
/* 科技展示风 CSS 规范 — 固化版 */
:root {
    --tech-blue: #2563eb;
    --tech-blue-light: #3b82f6;
    --tech-blue-dark: #1e40af;
    --tech-bg-start: #f0f7ff;
    --tech-bg-end: #ffffff;
    --tech-text: #1e2f3e;
    --tech-card-bg: rgba(255,255,255,0.9);
    --tech-border: rgba(37,99,235,0.2);
}

body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    line-height: 1.6;
    background: linear-gradient(135deg, var(--tech-bg-start), var(--tech-bg-end));
    color: var(--tech-text);
    padding: 40px 24px;
}
.document-container {
    max-width: 1000px;
    margin: 0 auto;
    background: var(--tech-card-bg);
    backdrop-filter: blur(2px);
    border-radius: 32px;
    padding: 40px 48px;
    box-shadow: 0 20px 40px -12px rgba(0,0,0,0.1), 0 0 0 1px var(--tech-border);
}
/* 渐变标题 */
h1 {
    font-size: 2rem;
    font-weight: 700;
    background: linear-gradient(135deg, var(--tech-blue), var(--tech-blue-light));
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    margin-bottom: 24px;
    letter-spacing: -0.02em;
}
h2 {
    font-size: 1.5rem;
    font-weight: 600;
    border-left: 4px solid var(--tech-blue);
    padding-left: 16px;
    margin-top: 32px;
    color: var(--tech-blue-dark);
}
h3 {
    font-size: 1.25rem;
    font-weight: 500;
    margin-top: 24px;
    color: var(--tech-blue);
}
/* 科技感卡片 */
.tech-card {
    background: white;
    border-radius: 20px;
    padding: 20px 24px;
    margin: 20px 0;
    box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    border: 1px solid rgba(37,99,235,0.15);
}
/* 微光效果（用于强调） */
.glow {
    background: linear-gradient(120deg, rgba(37,99,235,0.05), rgba(59,130,246,0.02));
    border-radius: 20px;
    padding: 4px 12px;
    display: inline-block;
}
/* 表格 — 科技感边框 */
table {
    width: 100%;
    border-collapse: collapse;
    margin: 24px 0;
    background: white;
    border-radius: 16px;
    overflow: hidden;
}
th, td {
    border: 1px solid var(--tech-border);
    padding: 12px 16px;
    text-align: left;
}
th {
    background: linear-gradient(135deg, #f8fafc, #f1f5f9);
    font-weight: 600;
    color: var(--tech-blue-dark);
}
/* 列表 */
ul, ol {
    margin: 16px 0;
    padding-left: 2em;
}
li {
    margin: 8px 0;
}
/* 代码块 */
pre {
    background: #0f172a;
    color: #e2e8f0;
    padding: 20px;
    border-radius: 16px;
    overflow-x: auto;
    font-family: 'SF Mono', 'Fira Code', monospace;
    font-size: 0.85rem;
}
code {
    background: #eef2ff;
    padding: 2px 8px;
    border-radius: 12px;
    font-family: monospace;
    font-size: 0.9em;
}
pre code {
    background: transparent;
    padding: 0;
    color: inherit;
}
/* 引用 */
blockquote {
    border-left: 4px solid var(--tech-blue);
    background: rgba(37,99,235,0.05);
    padding: 16px 20px;
    border-radius: 16px;
    margin: 20px 0;
}
/* 深色护眼模式切换按钮 */
.dark-toggle {
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: var(--tech-blue);
    color: white;
    border: none;
    border-radius: 40px;
    padding: 10px 20px;
    font-size: 0.85rem;
    cursor: pointer;
    font-family: inherit;
    box-shadow: 0 2px 8px rgba(0,0,0,0.2);
    z-index: 1000;
}
.dark-toggle:hover {
    background: var(--tech-blue-dark);
}
/* 深色模式样式 */
body.dark-mode {
    --tech-bg-start: #0f172a;
    --tech-bg-end: #1e293b;
    --tech-text: #e2e8f0;
    --tech-card-bg: rgba(30,41,59,0.95);
    --tech-border: rgba(59,130,246,0.3);
    background: linear-gradient(135deg, #0f172a, #1e293b);
}
body.dark-mode .document-container {
    background: rgba(30,41,59,0.95);
}
body.dark-mode .tech-card {
    background: #1e293b;
}
body.dark-mode th {
    background: #0f172a;
    color: #94a3b8;
}
body.dark-mode code {
    background: #1e293b;
    color: #cbd5e1;
}
body.dark-mode blockquote {
    background: rgba(59,130,246,0.1);
}
@media (max-width: 700px) {
    .document-container { padding: 24px; }
}
```

```jsx
/* 深色模式切换 JS — 固化在科技展示风HTML中 */
<script>
(function() {
    const toggle = document.createElement('button');
    toggle.className = 'dark-toggle';
    toggle.innerText = '🌙 护眼夜间模式';
    document.body.appendChild(toggle);
    toggle.addEventListener('click', () => {
        document.body.classList.toggle('dark-mode');
        toggle.innerText = document.body.classList.contains('dark-mode') ? '☀️ 日间模式' : '🌙 护眼夜间模式';
    });
})();
</script>
```

### 风格7：企微群聊风

**适用场景**：群聊记录、对话复盘

**设计原则**：真实群聊感、发送者右对齐、其他人左对齐、头像色相自动生成

```css
/* 企微群聊风 CSS 规范 — 固化版 */
body {
    background-color: #f5f7fa;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    padding: 24px 16px;
    line-height: 1.5;
    color: #1f2f3e;
}
.group-chat {
    max-width: 800px;
    margin: 0 auto;
    background-color: #ffffff;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
    overflow: hidden;
}
.chat-header {
    padding: 16px 20px;
    background: #ffffff;
    border-bottom: 1px solid #e9edf2;
    display: flex;
    align-items: baseline;
    flex-wrap: wrap;
    gap: 8px;
}
.group-name { font-size: 1.2rem; font-weight: 600; color: #1f2f3e; }
.group-members { font-size: 0.75rem; color: #8a9bb0; }
.chat-type { font-size: 0.7rem; background: #eef2f6; padding: 2px 8px; border-radius: 12px; color: #5e6f8d; margin-left: auto; }
.messages-list { padding: 16px 20px 24px; background: #ffffff; }
.message { display: flex; margin-bottom: 20px; align-items: flex-start; gap: 12px; }
/* 发送者（导出者）右对齐 */
.message.self { flex-direction: row-reverse; }
/* 其他人左对齐 */
.message.other { flex-direction: row; }
/* 头像 — 背景色由JS动态生成 */
.avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    font-weight: 500;
    flex-shrink: 0;
    box-shadow: 0 1px 2px rgba(0,0,0,0.05);
}
.msg-content { max-width: 70%; display: flex; flex-direction: column; }
.message.self .msg-content { align-items: flex-end; }
.meta { display: flex; align-items: baseline; gap: 8px; margin-bottom: 4px; flex-wrap: wrap; }
.name { font-weight: 600; font-size: 0.85rem; color: #2c3e50; }
.time { font-size: 0.7rem; color: #8a9bb0; }
/* 气泡 — 左右不同色 */
.bubble {
    padding: 8px 14px;
    border-radius: 12px;
    font-size: 0.9rem;
    line-height: 1.45;
    color: #1e2f3e;
    word-break: break-word;
    display: inline-block;
    max-width: 100%;
}
.message.other .bubble { background-color: #f2f4f8; }
.message.self .bubble { background-color: #d9e8ff; }
/* 引用回复 */
.quote-ref {
    background: #eef2f6;
    border-left: 3px solid #7c9bcb;
    padding: 6px 12px;
    border-radius: 8px;
    margin-bottom: 8px;
    font-size: 0.8rem;
    color: #5e6f8d;
}
.quote-name { font-weight: 600; margin-right: 6px; color: #2c5a7a; }
/* 系统消息 */
.system-message {
    background-color: #f8f9fc;
    padding: 8px 16px;
    border-radius: 20px;
    font-size: 0.75rem;
    color: #6c86a3;
    text-align: center;
    margin: 16px 0;
    border: 1px solid #eef2f8;
}
.mention { background: #fff0db; color: #c76b1c; padding: 0 4px; border-radius: 12px; font-weight: 500; font-size: 0.8rem; display: inline-block; margin-right: 4px; }
@media print {
    body { background: white; }
    .group-chat { box-shadow: none; border: 1px solid #ddd; }
    .avatar { background: #eef2fa !important; color: black; border: 1px solid #ccc; }
    .bubble { border: 1px solid #ccc; background: #fafafa !important; }
    .message.self .bubble { background: #f0f0f0 !important; }
}
@media (max-width: 600px) {
    .messages-list { padding: 12px; }
    .msg-content { max-width: 85%; }
}
```

```jsx
/* 头像背景色生成 + 发送者识别 JS — 固化版 */
<script>
(function() {
    // 哈希函数
    function hashCode(str) {
        let hash = 0;
        for (let i = 0; i < str.length; i++) {
            hash = ((hash << 5) - hash) + str.charCodeAt(i);
            hash |= 0;
        }
        return Math.abs(hash);
    }
    // 为所有头像设置背景色
    document.querySelectorAll('.avatar').forEach(avatar => {
        if (avatar.style.backgroundColor) return;
        const name = avatar.getAttribute('data-name') || avatar.innerText;
        if (name) {
            const hash = hashCode(name);
            const hue = hash % 360;
            avatar.style.backgroundColor = `hsl(${hue}, 30%, 70%)`;
        }
    });
    // 发送者识别：如果消息的data-sender等于导出者，则添加self类
    // 导出者由生成文档时传入，默认为当前用户
    const currentUser = document.body.getAttribute('data-current-user') || '我';
    document.querySelectorAll('.message').forEach(msg => {
        const sender = msg.getAttribute('data-sender');
        if (sender === currentUser) {
            msg.classList.add('self');
            msg.classList.remove('other');
        } else {
            msg.classList.add('other');
            msg.classList.remove('self');
        }
    });
})();
</script>
```

## 五、全局样式固化清单

以下元素的样式**在所有风格中都按统一规则生成**，保证基础体验一致：

| 元素 | 固化规则 |
| --- | --- |
| **有序列表** | 1. 2. 3. 缩进2em，行距1.5 |
| **无序列表** | • 二级 - 三级 ◦ 缩进逐级2em |
| **表格** | 表头背景#f5f7fa，行交替色白/#fafbfd，边框1px solid #e2e8f0 |
| **行内代码** | 背景#f2f4f8，圆角4px，内边距2px 6px |
| **代码块** | 背景#1e293b，颜色#e2e8f0，圆角10px，内边距16px，等宽字体 |
| **引用/注释** | 左边框3px，背景#fafbfd，斜体（简约风除外） |
| **图片** | 最大宽度100%，圆角8px，居中 |
| **链接** | 主色调，无下划线，hover加下划线 |

## 六、各风格差异化清单

| 风格 | 字体 | 主色 | 背景 | 专属样式类 |
| --- | --- | --- | --- | --- |
| 商务正式风 | Times / 宋体 | #2c7cb6 | 纯白 | `.company-header` `.stamp` |
| 技术文档风 | SF Mono / Consolas | #3b82f6 | #f9fafc | `.version-table` `.code-dark` |
| 产品需求风 | Inter | #3b82f6 | #f5f7fb | `.user-story` `.acceptance` |
| 复盘报告风 | Segoe UI | #f97316 | #fef9f0 | `.timeline` `.two-columns` `.conclusion` |
| 简约阅读风 | Georgia | 无（黑白灰） | #fefefe | 无任何装饰类 |
| 科技展示风 | Inter / SF Pro | #2563eb | 渐变白→#f0f7ff | `.tech-card` `.glow` `.dark-toggle` |
| 企微群聊风 | 系统默认 | 无主色 | #f5f7fa | `.bubble` `.avatar` `.quote-ref` `.system-msg` |

## 七、核心能力

1. **智能内容采集**：自动抓取当前对话中的核心产出内容
2. **文档类型识别**：根据关键词匹配判定文档类型，适配不同展示需求
3. **7种风格HTML渲染**：内置7种文档风格，CSS规范固化，一键切换
4. **响应式布局**：自动适配不同设备屏幕尺寸
5. **Word兼容**：生成的HTML在Word中打开时保留基础格式
6. **发送者识别**：企微群聊风自动识别导出者，实现发送者右对齐
7. **深色模式切换**：科技展示风内置深色护眼模式，一键切换

## 八、公式渲染支持

本插件生成的HTML文档已内置 **KaTeX 数学公式渲染引擎**，用户无需额外配置即可正常显示 LaTeX 公式。

**支持的公式格式**：

- 行间公式：`$$ 公式内容 $$`
- 行内公式：`$ 公式内容 $`

**渲染特性**：

- 自动识别并渲染页面中所有公式
- 长公式自动支持横向滚动，不破坏页面布局
- 兼容所有7种文档风格

**技术说明**：
生成的HTML文件已包含以下CDN引用：

| 资源 | CDN地址 |
| --- | --- |
| 样式表 | `https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/katex.min.css` |
| 核心库 | `https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/katex.min.js` |
| 自动渲染 | `https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/contrib/auto-render.min.js` |

用户保存为 `.html` 文件后，用浏览器打开即可直接查看公式效果。

## 九、关键原则

| 原则 | 说明 |
| --- | --- |
| **谁制作谁输出** | 文档的制作者直接交付HTML，不增加协作链路 |
| **格式优先** | 保留Markdown原有结构，确保内容不丢失 |
| **用户主导** | 风格由用户选择，不自动决定 |
| **即插即用** | 不改变团队原有流程，仅在需要时介入 |
| **Word兼容** | 确保生成的HTML可在Word中打开编辑 |
| **响应式** | 自动适配电脑、平板、手机 |
| **样式固化** | 7种风格CSS规范已固化，每次生成结果一致 |
| **头像统一** | 企微群聊风头像按规则生成，保证一致性 |
| **发送者识别** | 导出者右对齐，其他人左对齐，还原真实群聊感 |

## 十、加载方式

检索本插件的设定信息进行融合，加载到系统中。确保团队成员在输出文档时，能够自动启用文档样式转换能力，并严格遵循固化的CSS规范。

**加载后效果**：

- 展示“**文心雕文龙**已加载”
- 当用户在对话中提出“展示文档/保存文档”等需求时，当前执行任务的成员将自动输出格式化的HTML文档，并支持选择6种固化的样式风格。