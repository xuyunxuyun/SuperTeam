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

| **版本号** | **过程节点说明**    | **修订人** | **修订日期** | **修订内容**                                                 |
| :--------- | :------------------ | :--------- | :----------- | :----------------------------------------------------------- |
| V0.1.0     | 初稿创建            | 盘古开插件 | 2026-03-24   | 根据用户需求生成                                             |
| V0.1.1     | 样式固化            | 盘古开插件 | 2026-03-25   | 增加“企微群聊风”文档样式，将6种样式CSS规范固化至插件，确保输出一致性 |
| V0.1.2     | 样式固化            | 盘古开插件 | 2026-03-31   | 增加“科技展示风”文档样式，固定配色、色块、列表、表格、气泡、注释、代码等样式，确保输出一致性，增加公式支持 |
| V0.1.3     | 样式优化 + 图表增强 | 盘古开插件 | 2026-05-19   | 根据DeepSeek V4进行样式优化：统一字体栈、行高、圆角、阴影、间距系统；优化表格交替色及横滑适配；优化代码块配色；加强引用块边框；增加气泡底色fallback；增加Mermaid流程图渲染；增加智能图表转换（雷达图、玫瑰图）、数据→图表映射表、用户询问策略 |
| V0.1.4     | 效率优化            | 徐昀       | 2026-08-14   | 依赖库按需加载，提高效率；细节调整                           |

## 插件名称

**文心雕文龙**

## 一、定位与价值

这是一个集成在团队执行流程中的**文档格式化插件**。当用户需要保存或展示文档时，自动将团队产出的Markdown内容转换为高质量HTML文档，支持多种风格样式，用户可直接在浏览器查看或使用Word打开编辑。

**核心价值**：

- 让团队输出从“纯文本”升级为“高质量文档”
- 保留格式、便于保存、支持编辑
- 谁制作谁交付，不增加协作成本
- **样式规范固化**：所有风格样式已固化至插件，每次生成结果一致

**服务范围**：适用于会议纪要、技术方案、需求文档、复盘报告、通用文档、群聊实录等所有团队产出物。

## 二、插件启动流程

### 启动条件

本插件为**集成型插件**，不设单独激活指令。当用户在对话中提出以下关键词或表达此意向时，由当前执行任务的团队成员自动触发：

**触发词列表**：

- “展示文档”
- “输出文档”
- “保存文档”
- “下载文档”
- “给我一份正式版”
- “导出这个”
- “生成文档”

### 执行流程

**步骤1：内容采集**

- 自动抓取当前对话中团队产出的核心内容
- 如有多个版本，以最新确认的版本为准
- 保留原有Markdown结构（标题、列表、表格、代码块、引用等）

**步骤2：文档类型识别**

- 根据内容特征自动判断文档类型，或询问用户确认
- 类型包括：会议纪要、技术方案、需求文档、复盘报告、通用文档、群聊实录
- 按推荐表为用户提供风格建议

**步骤3：样式风格选择**

- 向用户展示7种风格选项，由用户选择
- 选项根据文档类型动态推荐，但用户可自由选择任一风格
- **样式规范已固化，每次选择同一风格输出结果完全一致**

**步骤4：HTML生成**

- 按选定风格调用对应CSS规范生成完整HTML文档
- 内置响应式布局，适配电脑、平板、手机
- Word打开时保留基础格式和样式
- 若选择“企微群聊风”，自动按规则生成头像背景色，并识别发送者
- 自动渲染文档中的Mermaid流程图
- **自动识别数据表格，按映射表推荐图表，必要时询问用户**

**步骤5：交付与提示**

- 直接在对话中输出HTML代码块
- 附保存提示

### 关键规则

- 谁制作谁输出
- 即时响应
- 格式保留
- 样式一致
- 无侵入性

## 三、核心能力

1. 智能内容采集
2. 文档类型识别
3. 多风格HTML渲染（7种）
4. 响应式布局
5. Word兼容
6. 公式渲染（KaTeX）
7. 流程图渲染（Mermaid）
8. **智能图表转换（含雷达图、玫瑰图）**
9. **数据→图表映射表**
10. **用户询问策略**

## 四、样式规范库

### 全局样式固化清单

以下元素的样式**在所有风格中都按统一规则生成**，保证基础体验一致：

| 元素                   | 固化规则                                                     |
| :--------------------- | :----------------------------------------------------------- |
| **字体栈**             | `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`（各风格可在此基础上增加专属字体） |
| **行高**               | 正文 `1.6`，标题 `1.4`                                       |
| **标题间距**           | `h1 margin-top: 2em, margin-bottom: 0.5em`；`h2/h3/h4` 依次递减 |
| **正文段落**           | `margin-bottom: 1.2em`                                       |
| **有序/无序列表**      | 缩进2em，二级4em，行距1.5                                    |
| **表格容器**           | 外层加 `.table-wrapper`，`overflow-x: auto`，底部加横滑提示条 |
| **表格样式**           | 表头背景 `#f5f7fa`，行交替色白 / `#fafbfd`，边框 `1px solid #e2e8f0` |
| **行内代码**           | 背景 `#f2f4f8`，圆角 `6px`，内边距 `2px 6px`                 |
| **代码块**             | 背景 `#1e1e2e`，颜色 `#e2e8f0`，圆角 `8px`，内边距 `16px`，字体 `'JetBrains Mono', 'SF Mono', monospace` |
| **引用/注释**          | 左边框 `4px solid`，背景 `#fafbfd`，内边距 `12px 16px`，圆角 `8px` |
| **图片**               | 最大宽度100%，圆角 `8px`，居中显示                           |
| **链接**               | 主色调，无下划线，hover加下划线                              |
| **卡片/容器**          | 圆角 `12px`，阴影 `0 4px 12px rgba(0,0,0,0.04)`              |
| **头像（企微群聊风）** | 圆角 `50%`，阴影 `0 1px 2px rgba(0,0,0,0.05)`                |
| **气泡（企微群聊风）** | 圆角 `12px`，内边距 `8px 14px`，`background-color` fallback 兼容邮件客户端 |

### 风格1：商务正式风

**适用场景**：对外汇报、呈报领导、正式会议纪要

**设计原则**：庄重严肃、可打印、Times字体、页眉页脚

```css
/* 商务正式风 CSS 规范 — V0.1.3优化版 */
body {
    font-family: 'Times New Roman', '宋体', SimSun, 'Georgia', serif;
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
/* 印章样式 */
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
h1 { font-size: 1.8rem; border-left: 4px solid #2c7cb6; padding-left: 16px; margin-top: 2em; margin-bottom: 0.5em; color: #1e4663; }
h2 { font-size: 1.4rem; border-bottom: 2px solid #e6edf4; padding-bottom: 8px; margin-top: 1.6em; margin-bottom: 0.5em; color: #2c5a7a; }
h3 { font-size: 1.2rem; margin-top: 1.2em; margin-bottom: 0.5em; color: #3a6e8c; }
p { margin-bottom: 1.2em; }
/* 表格容器 + 横滑 */
.table-wrapper { overflow-x: auto; margin: 20px 0; border-radius: 12px; }
.table-wrapper::after {
    content: "← 左右滑动查看更多 →";
    display: block;
    text-align: center;
    font-size: 0.7rem;
    color: #8a9bb0;
    padding-top: 8px;
}
table { border-collapse: collapse; width: 100%; min-width: 500px; }
th, td { border: 1px solid #d0dae8; padding: 10px 12px; text-align: left; }
th { background-color: #f0f4fa; font-weight: 600; }
tr:nth-child(even) { background-color: #fafcff; }
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 6px 0; line-height: 1.5; }
ul ul, ol ol { margin: 4px 0; padding-left: 2em; }
/* 代码 */
code { background: #f2f4f8; padding: 2px 6px; border-radius: 6px; font-family: 'JetBrains Mono', 'SF Mono', monospace; font-size: 0.9em; }
pre { background: #1e1e2e; color: #e2e8f0; padding: 16px; border-radius: 8px; overflow-x: auto; }
pre code { background: transparent; padding: 0; color: inherit; }
/* 引用 */
blockquote { border-left: 4px solid #2c7cb6; background: #fafbfd; margin: 16px 0; padding: 12px 16px; border-radius: 8px; color: #4a627a; }
/* 卡片容器 */
.card, .container { border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.04); }
@media print {
    body { margin: 0; }
    .table-wrapper::after { content: none; }
    .stamp { border-color: #999; color: #999; }
}
```

### 风格2：技术文档风

**适用场景**：研发内部、API文档、代码说明

**设计原则**：专业、代码友好、深色代码块、版本号表格

```css
/* 技术文档风 CSS 规范 — V0.1.3优化版 */
body {
    font-family: 'SF Mono', 'JetBrains Mono', 'Fira Code', 'Consolas', monospace;
    line-height: 1.6;
    background: #f9fafc;
    color: #1e2f3e;
    max-width: 1100px;
    margin: 30px auto;
    padding: 20px;
}
/* 版本号表格 */
.version-table {
    width: 100%;
    border-collapse: collapse;
    background: white;
    margin: 20px 0;
    border-radius: 12px;
    overflow: hidden;
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
h1 { font-size: 1.6rem; border-bottom: 2px solid #3b82f6; padding-bottom: 8px; margin-top: 2em; margin-bottom: 0.5em; color: #1e3a8a; font-weight: 600; }
h2 { font-size: 1.3rem; margin-top: 1.6em; margin-bottom: 0.5em; color: #2563eb; }
h3 { font-size: 1.1rem; margin-top: 1.2em; margin-bottom: 0.5em; color: #3b82f6; }
p { margin-bottom: 1.2em; }
/* 表格容器 */
.table-wrapper { overflow-x: auto; margin: 20px 0; border-radius: 12px; }
.table-wrapper::after {
    content: "← 左右滑动查看更多 →";
    display: block;
    text-align: center;
    font-size: 0.7rem;
    color: #8a9bb0;
    padding-top: 8px;
}
table:not(.version-table) {
    border-collapse: collapse;
    width: 100%;
    min-width: 500px;
    background: white;
    border-radius: 12px;
    overflow: hidden;
}
th, td {
    border: 1px solid #cbd5e1;
    padding: 8px 12px;
}
th {
    background: #eef2ff;
}
tr:nth-child(even) {
    background: #fafbfd;
}
/* 代码块 — 浅色优化（V0.1.3） */
pre {
    background: #1e1e2e;
    color: #e2e8f0;
    padding: 16px;
    border-radius: 8px;
    overflow-x: auto;
    font-size: 0.85rem;
    font-family: 'JetBrains Mono', 'SF Mono', 'Fira Code', monospace;
}
code {
    background: #eef2ff;
    padding: 2px 6px;
    border-radius: 6px;
    font-family: 'JetBrains Mono', 'SF Mono', monospace;
    font-size: 0.9em;
}
pre code {
    background: transparent;
    padding: 0;
    color: inherit;
}
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 4px 0; }
ul ul, ol ol { padding-left: 2em; }
/* 引用 */
blockquote {
    border-left: 4px solid #3b82f6;
    background: #f1f5f9;
    padding: 12px 16px;
    margin: 16px 0;
    border-radius: 8px;
}
/* 卡片容器 */
.card, .container { border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.04); }
```

### 风格3：产品需求风

**适用场景**：PRD、需求文档、功能说明

**设计原则**：结构化、可追溯、用户故事框、验收标准色块

```css
/* 产品需求风 CSS 规范 — V0.1.3优化版 */
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Inter', 'Segoe UI', sans-serif;
    line-height: 1.6;
    background: #f5f7fb;
    color: #1f2f3e;
    padding: 32px 24px;
}
.document-container {
    max-width: 1000px;
    margin: 0 auto;
    background: white;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.04);
    padding: 32px 40px;
}
/* 用户故事框 */
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
/* 验收标准色块 */
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
tr:nth-child(even) {
    background: #fafbfd;
}
/* 表格容器 */
.table-wrapper { overflow-x: auto; margin: 20px 0; border-radius: 12px; }
.table-wrapper::after {
    content: "← 左右滑动查看更多 →";
    display: block;
    text-align: center;
    font-size: 0.7rem;
    color: #8a9bb0;
    padding-top: 8px;
}
table { min-width: 500px; }
/* 标题 */
h1 { font-size: 1.8rem; font-weight: 700; color: #0f172a; margin-top: 2em; margin-bottom: 0.5em; }
h2 { font-size: 1.3rem; font-weight: 600; background: #f8fafc; padding: 10px 16px; border-radius: 12px; margin-top: 1.6em; margin-bottom: 0.5em; color: #0f3b5c; }
h3 { font-size: 1.1rem; margin-top: 1.2em; margin-bottom: 0.5em; color: #2563eb; }
p { margin-bottom: 1.2em; }
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 6px 0; }
ul ul, ol ol { padding-left: 2em; }
/* 代码 */
code { background: #f1f5f9; padding: 2px 6px; border-radius: 6px; font-family: 'JetBrains Mono', monospace; }
pre { background: #1e1e2e; color: #e2e8f0; padding: 16px; border-radius: 8px; overflow-x: auto; }
pre code { background: transparent; padding: 0; color: inherit; }
/* 卡片容器 */
.card { border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.04); }
```

### 风格4：复盘报告风

**适用场景**：项目复盘、工作总结

**设计原则**：时间轴、问题-改进双栏、结论高亮

```css
/* 复盘报告风 CSS 规范 — V0.1.3优化版 */
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    line-height: 1.6;
    background: #fef9f0;
    color: #2c3e2f;
    padding: 40px 20px;
}
.report-container {
    max-width: 1000px;
    margin: 0 auto;
    background: #ffffffea;
    border-radius: 12px;
    padding: 32px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.04);
}
/* 标题 */
h1 {
    font-size: 2rem;
    border-left: 6px solid #c2410c;
    padding-left: 20px;
    margin-top: 1em;
    margin-bottom: 0.5em;
    color: #431407;
}
h2 { margin-top: 1.6em; margin-bottom: 0.5em; }
h3 { margin-top: 1.2em; margin-bottom: 0.5em; }
p { margin-bottom: 1.2em; }
/* 时间轴 */
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
/* 问题-改进双栏 */
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
    border-radius: 12px;
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
    border-radius: 12px;
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
    border-radius: 12px;
    font-weight: 500;
}
.conclusion::before {
    content: "🎯 关键结论";
    display: block;
    font-weight: 700;
    color: #f97316;
    margin-bottom: 12px;
}
/* 表格容器 */
.table-wrapper { overflow-x: auto; margin: 20px 0; border-radius: 12px; }
.table-wrapper::after {
    content: "← 左右滑动查看更多 →";
    display: block;
    text-align: center;
    font-size: 0.7rem;
    color: #8a9bb0;
    padding-top: 8px;
}
table { width: 100%; border-collapse: collapse; min-width: 500px; margin: 20px 0; border-radius: 12px; overflow: hidden; }
th, td { border: 1px solid #e2e8f0; padding: 10px; }
th { background: #fef3e8; }
tr:nth-child(even) { background: #fef9f0; }
/* 列表 */
ul, ol { margin: 12px 0; padding-left: 2em; }
li { margin: 6px 0; }
ul ul, ol ol { padding-left: 2em; }
/* 代码 */
code { background: #f1f5f9; padding: 2px 6px; border-radius: 6px; }
pre { background: #1e1e2e; color: #e2e8f0; padding: 16px; border-radius: 8px; overflow-x: auto; }
pre code { background: transparent; padding: 0; }
@media (max-width: 700px) {
    .two-columns { flex-direction: column; }
}
```

### 风格5：简约阅读风

**适用场景**：知识沉淀、个人笔记、长文阅读

**设计原则**：极简、沉浸、纯文字+留白、无任何装饰

```css
/* 简约阅读风 CSS 规范 — V0.1.3优化版 */
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
    margin-top: 2em;
    margin-bottom: 0.5em;
    color: #1e4663;
    border-bottom: none;
}
h2 {
    font-size: 1.6rem;
    margin-top: 1.6em;
    margin-bottom: 0.5em;
    color: #2c5a7a;
    border-bottom: none;
}
h3 {
    font-size: 1.3rem;
    margin-top: 1.2em;
    margin-bottom: 0.5em;
    color: #3a6e8c;
}
p {
    margin-bottom: 1.4em;
}
/* 表格容器 — 极简但保留功能 */
.table-wrapper { overflow-x: auto; margin: 24px 0; }
table { width: 100%; border-collapse: collapse; min-width: 500px; }
th, td { border-bottom: 1px solid #e2e8f0; padding: 12px; text-align: left; }
th { font-weight: 600; }
/* 无交替色 */
/* 列表 */
ul, ol {
    margin: 16px 0;
    padding-left: 2em;
}
li {
    margin: 8px 0;
}
ul ul, ol ol {
    padding-left: 2em;
}
/* 引用 — 极简斜体 */
blockquote {
    font-style: italic;
    border-left: 2px solid #e2e8f0;
    padding-left: 24px;
    margin: 24px 0;
    color: #4b5565;
    background: transparent;
}
/* 代码块 — 极简浅灰 */
code {
    background: #f4f4f5;
    padding: 2px 5px;
    font-family: 'JetBrains Mono', 'SF Mono', monospace;
    font-size: 0.9em;
    border-radius: 4px;
}
pre {
    background: #f9fafb;
    padding: 20px;
    overflow-x: auto;
    border-radius: 0;
    border-left: 2px solid #e2e8f0;
}
pre code {
    background: transparent;
    padding: 0;
}
/* 无任何色块、无卡片、无阴影 */
```

### 风格6：科技展示风

**适用场景**：对外汇报、AI产品发布、技术方案路演

**设计原则**：科技蓝调、渐变背景、微光效、可切换深色护眼模式

```css
/* 科技展示风 CSS 规范 — V0.1.3优化版 */
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
    font-family: -apple-system, BlinkMacSystemFont, 'Inter', 'Segoe UI', sans-serif;
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
    border-radius: 12px;
    padding: 40px 48px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.04), 0 0 0 1px var(--tech-border);
}
/* 渐变标题 */
h1 {
    font-size: 2rem;
    font-weight: 700;
    background: linear-gradient(135deg, var(--tech-blue), var(--tech-blue-light));
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    margin-top: 1em;
    margin-bottom: 0.5em;
    letter-spacing: -0.02em;
}
h2 {
    font-size: 1.5rem;
    font-weight: 600;
    border-left: 4px solid var(--tech-blue);
    padding-left: 16px;
    margin-top: 1.6em;
    margin-bottom: 0.5em;
    color: var(--tech-blue-dark);
}
h3 {
    font-size: 1.25rem;
    font-weight: 500;
    margin-top: 1.2em;
    margin-bottom: 0.5em;
    color: var(--tech-blue);
}
p { margin-bottom: 1.2em; }
/* 科技感卡片 */
.tech-card {
    background: white;
    border-radius: 12px;
    padding: 20px 24px;
    margin: 20px 0;
    box-shadow: 0 4px 12px rgba(0,0,0,0.04);
    border: 1px solid var(--tech-border);
}
/* 微光效果 */
.glow {
    background: linear-gradient(120deg, rgba(37,99,235,0.05), rgba(59,130,246,0.02));
    border-radius: 12px;
    padding: 4px 12px;
    display: inline-block;
}
/* 表格容器 */
.table-wrapper { overflow-x: auto; margin: 24px 0; border-radius: 12px; }
.table-wrapper::after {
    content: "← 左右滑动查看更多 →";
    display: block;
    text-align: center;
    font-size: 0.7rem;
    color: #8a9bb0;
    padding-top: 8px;
}
table { width: 100%; border-collapse: collapse; min-width: 500px; background: white; border-radius: 12px; overflow: hidden; }
th, td { border: 1px solid var(--tech-border); padding: 12px 16px; text-align: left; }
th { background: linear-gradient(135deg, #f8fafc, #f1f5f9); font-weight: 600; color: var(--tech-blue-dark); }
tr:nth-child(even) { background: #fafbfd; }
/* 列表 */
ul, ol { margin: 16px 0; padding-left: 2em; }
li { margin: 8px 0; }
ul ul, ol ol { padding-left: 2em; }
/* 代码块 */
pre {
    background: #1e1e2e;
    color: #e2e8f0;
    padding: 20px;
    border-radius: 8px;
    overflow-x: auto;
    font-family: 'JetBrains Mono', 'SF Mono', 'Fira Code', monospace;
    font-size: 0.85rem;
}
code {
    background: #eef2ff;
    padding: 2px 8px;
    border-radius: 8px;
    font-family: 'JetBrains Mono', monospace;
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
    border-radius: 12px;
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
/* 深色模式样式 — V0.1.3表格对比度优化 */
body.dark-mode {
    --tech-bg-start: #0f172a;
    --tech-bg-end: #1e293b;
    --tech-text: #f1f5f9;
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
body.dark-mode table {
    background: #1e293b;
}
body.dark-mode td {
    color: #f1f5f9;
}
body.dark-mode tr:nth-child(even) {
    background: #253141;
}
body.dark-mode tr:hover {
    background: rgba(59,130,246,0.1);
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

```html
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
/* 企微群聊风 CSS 规范 — V0.1.3优化版 */
body {
    background-color: #f5f7fa;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    padding: 24px 16px;
    line-height: 1.6;
    color: #1f2f3e;
}
.group-chat {
    max-width: 800px;
    margin: 0 auto;
    background-color: #ffffff;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.04);
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
.message.self { flex-direction: row-reverse; }
.message.other { flex-direction: row; }
/* 头像 */
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
/* 气泡 — 带fallback底色 */
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
.message.other .bubble {
    background-color: #f2f4f8;
    background: #f2f4f8;
}
.message.self .bubble {
    background-color: #d9e8ff;
    background: #d9e8ff;
}
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

```html
/* 头像背景色生成 + 发送者识别 JS — 固化版 */
<script>
(function() {
    function hashCode(str) {
        let hash = 0;
        for (let i = 0; i < str.length; i++) {
            hash = ((hash << 5) - hash) + str.charCodeAt(i);
            hash |= 0;
        }
        return Math.abs(hash);
    }
    document.querySelectorAll('.avatar').forEach(avatar => {
        if (avatar.style.backgroundColor) return;
        const name = avatar.getAttribute('data-name') || avatar.innerText;
        if (name) {
            const hash = hashCode(name);
            const hue = hash % 360;
            avatar.style.backgroundColor = `hsl(${hue}, 30%, 70%)`;
        }
    });
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

## 五、各风格差异化清单

| 风格       | 字体                     | 主色    | 背景           | 专属样式类                                         | 特殊优化                |
| :--------- | :----------------------- | :------ | :------------- | :------------------------------------------------- | :---------------------- |
| 商务正式风 | Times / 宋体 / Georgia   | #2c7cb6 | 纯白           | `.stamp` `.document-header`                        | 可打印优化              |
| 技术文档风 | JetBrains Mono / SF Mono | #3b82f6 | #f9fafc        | `.version-table`                                   | 浅色代码块              |
| 产品需求风 | Inter / 系统字体         | #3b82f6 | #f5f7fb        | `.user-story` `.acceptance-criteria`               | 双色块                  |
| 复盘报告风 | Segoe UI / 系统字体      | #f97316 | #fef9f0        | `.timeline` `.two-columns` `.conclusion`           | 双栏布局                |
| 简约阅读风 | Georgia / Times          | 无      | #fefefe        | 无                                                 | 极简无装饰              |
| 科技展示风 | Inter / 系统字体         | #2563eb | 渐变白→#f0f7ff | `.tech-card` `.glow` `.dark-toggle`                | 深色模式+表格对比度优化 |
| 企微群聊风 | 系统默认                 | 无      | #f5f7fa        | `.bubble` `.avatar` `.quote-ref` `.system-message` | 发送者识别+气泡fallback |

## 六、公式渲染支持

本插件生成的HTML文档已内置 **KaTeX 数学公式渲染引擎**，用户无需额外配置即可正常显示 LaTeX 公式。

**支持的公式格式**：
- 行间公式：`$$ 公式内容 $$`
- 行内公式：`$ 公式内容 $`

**渲染特性**：
- 自动识别并渲染页面中所有公式
- 长公式自动支持横向滚动，不破坏页面布局
- 兼容所有7种文档风格

**技术说明**：
生成的HTML文件已包含以下CDN引用（优先使用阿里云镜像，国内访问更快）：

| 资源     | CDN地址                                                      |
| :------- | :----------------------------------------------------------- |
| 样式表   | `https://registry.npmmirror.com/katex/0.16.10/files/dist/katex.min.css` |
| 核心库   | `https://registry.npmmirror.com/katex/0.16.10/files/dist/katex.min.js` |
| 自动渲染 | `https://registry.npmmirror.com/katex/0.16.10/files/dist/contrib/auto-render.min.js` |

**备选方案**：若上述地址失效，自动回退至 `https://unpkg.com/katex@0.16.10/dist/...`

用户保存为 `.html` 文件后，用浏览器打开即可直接查看公式效果。

## 七、Mermaid 流程图渲染支持

本插件生成的HTML文档已内置 **Mermaid 流程图渲染引擎**，用户无需额外配置即可正常显示流程图、时序图、甘特图、类图、状态图、实体关系图、用户旅程图、饼图、需求图等。

**支持的图表类型**：

| 图表类型   | Mermaid 关键字        | 适用场景                      |
| :--------- | :-------------------- | :---------------------------- |
| 流程图     | `graph` / `flowchart` | 业务流程、决策分支、算法逻辑  |
| 时序图     | `sequenceDiagram`     | 交互流程、API调用、跨系统协作 |
| 甘特图     | `gantt`               | 项目排期、任务计划、进度追踪  |
| 类图       | `classDiagram`        | 系统设计、UML建模、代码结构   |
| 状态图     | `stateDiagram-v2`     | 状态机、生命周期、流程节点    |
| 实体关系图 | `erDiagram`           | 数据库设计、表关系、数据建模  |
| 用户旅程图 | `journey`             | 用户体验、产品流程、触点分析  |
| 饼图       | `pie`                 | 数据占比、统计分布、资源分配  |
| 需求图     | `requirementDiagram`  | 需求追踪、验收标准、功能依赖  |

**使用方式**：

在文档的Markdown内容中，直接使用标准的Mermaid代码块：

````markdown
```mermaid
graph TD
    A[用户需求] --> B{可行性评估}
    B -->|可行| C[立项开发]
    B -->|不可行| D[需求调整]
    C --> E[交付验收]
````

**渲染特性**：

- 自动识别页面中所有 ` ```mermaid ` 代码块并渲染
- 支持响应式布局，图表自动适配容器宽度
- 长图/复杂图表支持横向滚动，不破坏页面布局
- 兼容所有7种文档风格
- 深色模式下自动调整图表颜色对比度（科技展示风）

**技术说明**：
生成的HTML文件已包含以下CDN引用（优先使用阿里云镜像）：

| 资源   | CDN地址                                                      |
| :----- | :----------------------------------------------------------- |
| 核心库 | `https://registry.npmmirror.com/mermaid/11.0.0/files/dist/mermaid.min.js` |

**备选方案**：若上述地址失效，自动回退至 `https://unpkg.com/mermaid@11/dist/mermaid.min.js`

并已内置以下初始化配置：

```javascript
mermaid.initialize({
    startOnLoad: true,
    theme: 'base',
    themeVariables: {
        'primaryColor': '#2563eb',
        'primaryBorderColor': '#1e40af',
        'primaryTextColor': '#ffffff',
        'lineColor': '#3b82f6',
        'secondaryColor': '#f0f7ff',
        'tertiaryColor': '#ffffff'
    },
    flowchart: {
        useMaxWidth: true,
        htmlLabels: true,
        curve: 'basis',
        padding: 15
    },
    securityLevel: 'loose'
});
```

用户保存为 `.html` 文件后，用浏览器打开即可直接查看流程图渲染效果。

**注意**：如果文档中不需要流程图，Mermaid 库不会影响页面加载速度（懒加载机制）。

## 八、智能图表转换（增强版）

### 8.1 数据 → 图表映射表（固化规则）

| 数据形态                        | 推荐图表            | 决策规则 / 触发条件        |
| :------------------------------ | :------------------ | :------------------------- |
| 多行多列 + 3~8个指标            | **雷达图**          | 强调同一组对象的多个维度   |
| 分类 + 数值 + 周期性（月/小时） | **玫瑰图**          | 角度=时间/类别，半径=数值  |
| 两列（分类+数值）               | 饼图 / 柱状图       | 看占比→饼图；看排名→柱状图 |
| 多行时间（≥3个时间点）          | 折线图              | 趋势                       |
| 多分类 + 多数值（组数≤8）       | 分组柱状图 / 雷达图 | 想对比轮廓时优先雷达图     |
| 多行多列纯数值                  | 热力图（可选）      | 相关性/密度分析            |

### 8.2 雷达图专项规则

- **指标维度 ≤ 8**：直接渲染雷达图
- **指标维度 > 8**：弹出提示：“维度过多（当前X维），雷达图可读性下降，建议转条形图或拆分”
- **系列数 ≤ 3**：清晰可读
- **系列数 > 3**：推荐改为分组柱状图

### 8.3 玫瑰图专项规则

- **角度维度 ≥ 4**：效果明显
- **角度维度 ≤ 3**：不建议使用（推荐饼图或柱状图）
- **数值差异过大**：自动使用对数刻度或提示用户

### 8.4 自然语言 → 图表映射

| 用户说法                         | 目标图表        |
| :------------------------------- | :-------------- |
| 能力对比 / 技能评分 / 综合素质   | 雷达图          |
| 24小时分布 / 按月分布 / 角度强弱 | 玫瑰图          |
| 占比 / 份额 / 百分之多少         | 饼图            |
| 趋势 / 变化 / 逐月 / 逐周        | 折线图          |
| 对比 / 排名 / 谁高谁低           | 柱状图 / 条形图 |

### 8.5 询问策略（强用户体验）

**原则**：

- 高置信场景：直接出图（不询问）
- 中等置信场景：推荐 + 让用户确认
- 低置信场景：主动询问意图

**询问话术示例（嵌入HTML）**：

```text
📊 检测到数据表格：
   - 3个维度（性能、价格、外观）
   - 2个产品（A、B）

💡 推荐图表：
   ✅ 雷达图（适合多指标对比）
   ✅ 分组柱状图（适合直观对比数值）

请选择：
1️⃣ 雷达图
2️⃣ 分组柱状图
3️⃣ 不转换，保持表格
4️⃣ 本次文档不再询问
```

**玫瑰图专用询问**：

```text
🌹 检测到数据适合做玫瑰图：
   - 角度维度：月份（1~12月）
   - 强度维度：销售额

是否渲染为玫瑰图（半径代表销售额）？
[是] [否，保持表格] [不再询问]
```

### 8.6 技术实现

- 图表渲染库：**ECharts**（支持雷达图、玫瑰图、柱状图、折线图、饼图）
- CDN（优先使用阿里云镜像）：`https://registry.npmmirror.com/echarts/5.5.0/files/dist/echarts.min.js`
- **备选方案**：若上述地址失效，自动回退至 `https://unpkg.com/echarts@5/dist/echarts.min.js`
- 所有图表响应式，支持移动端手势
- 玫瑰图、雷达图默认最小宽度 300px，支持点击放大

### 8.7 与现有风格的兼容

- 图表主题跟随文档风格（科技展示风下使用科技蓝配色）
- 深色模式下图表自动适配深色主题
- 不破坏原有表格结构（原始表格保留在图表下方，可折叠）

## 九、智能交互增强

本插件生成的HTML文档内置两大智能交互功能，让文档从“静态阅读”升级为“动态浏览”，极大提升用户体验。

### 9.1 导航目录（Table of Contents）

**功能说明**：根据文档标题层级（H1/H2/H3）自动生成目录树，支持点击跳转、平滑滚动、当前位置高亮。

**目录样式规则**：

| 设备               | 目录位置     | 默认状态         | 交互方式                         |
| :----------------- | :----------- | :--------------- | :------------------------------- |
| 桌面（宽度>768px） | 左侧边栏     | 固定显示，可收起 | 点击标题跳转，滚动时高亮当前章节 |
| 平板（宽度≤768px） | 顶部折叠菜单 | 默认收起         | 点击汉堡菜单展开                 |
| 手机（宽度≤480px） | 底部抽屉     | 默认收起         | 点击按钮或上滑展开               |

**目录层级规则**：

- 显示 H1、H2、H3 三级标题
- H1 作为一级目录（加粗，缩进0）
- H2 作为二级目录（缩进1级，20px）
- H3 作为三级目录（缩进2级，40px，默认可折叠）

**技术实现**：

```javascript
// 目录生成函数
function generateTOC() {
    const headings = document.querySelectorAll('h1, h2, h3');
    if (headings.length < 2) return;
    
    // 为每个标题生成唯一ID
    headings.forEach((heading, index) => {
        if (!heading.id) {
            const text = heading.textContent.trim();
            const id = `heading-${index}-${text.replace(/\s+/g, '-').slice(0, 30)}`;
            heading.id = id;
        }
    });
    
    // 构建目录HTML
    let tocHTML = '<div class="toc-container"><div class="toc-header"><span class="toc-title">📑 目录</span><button class="toc-toggle">收起</button></div><ul class="toc-list">';
    headings.forEach((heading, index) => {
        const level = parseInt(heading.tagName[1]);
        const indent = (level - 1) * 20;
        tocHTML += `<li class="toc-item level-${level}" style="margin-left: ${indent}px">
                        <a href="#${heading.id}" class="toc-link">${heading.textContent}</a>
                    </li>`;
    });
    tocHTML += '</ul></div>';
    
    // 注入到页面顶部
    const container = document.querySelector('.report-container, .document-container, body > div:first-child');
    if (container && !document.querySelector('.toc-container')) {
        container.insertAdjacentHTML('afterbegin', tocHTML);
    }
}

// 平滑滚动 + 高亮当前章节
function initTOCInteraction() {
    document.querySelectorAll('.toc-link').forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            const targetId = link.getAttribute('href').substring(1);
            const target = document.getElementById(targetId);
            if (target) {
                target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                history.pushState(null, null, `#${targetId}`);
            }
        });
    });
    
    // 滚动时高亮当前章节
    window.addEventListener('scroll', () => {
        const headings = document.querySelectorAll('h1, h2, h3');
        let current = '';
        headings.forEach(heading => {
            const rect = heading.getBoundingClientRect();
            if (rect.top <= 100 && rect.bottom >= 0) {
                current = heading.id;
            }
        });
        document.querySelectorAll('.toc-link').forEach(link => {
            link.classList.remove('active');
            if (link.getAttribute('href') === `#${current}`) {
                link.classList.add('active');
            }
        });
    });
}
```

**固化的CSS样式**：

```css
/* 导航目录样式 — 固化版 */
.toc-container {
    background: #f8fafc;
    border-radius: 12px;
    padding: 16px 20px;
    margin-bottom: 32px;
    border: 1px solid #e2e8f0;
}
.toc-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 12px;
    padding-bottom: 8px;
    border-bottom: 1px solid #e2e8f0;
}
.toc-title {
    font-weight: 700;
    font-size: 1rem;
    color: #1e4663;
}
.toc-toggle {
    background: none;
    border: none;
    color: #3b82f6;
    cursor: pointer;
    font-size: 0.8rem;
}
.toc-list {
    list-style: none;
    margin: 0;
    padding: 0;
}
.toc-item {
    margin: 8px 0;
    line-height: 1.4;
}
.toc-link {
    text-decoration: none;
    color: #4a5568;
    font-size: 0.9rem;
    display: block;
    padding: 4px 0;
    transition: color 0.2s;
}
.toc-link:hover {
    color: #2563eb;
    text-decoration: underline;
}
.toc-link.active {
    color: #2563eb;
    font-weight: 600;
    border-left: 3px solid #2563eb;
    padding-left: 8px;
}
/* 移动端适配 */
@media (max-width: 768px) {
    .toc-container {
        position: sticky;
        top: 0;
        z-index: 100;
        background: rgba(255,255,255,0.95);
        backdrop-filter: blur(8px);
    }
    .toc-list {
        max-height: 0;
        overflow: hidden;
        transition: max-height 0.3s ease;
    }
    .toc-list.expanded {
        max-height: 500px;
        overflow-y: auto;
    }
}
```

### 9.2 智能超链接

**功能说明**：自动识别文档中的内部引用（如“详见第3章”、“参考‘需求分析’”、“如图2所示”），创建锚点跳转链接，方便用户快速定位相关内容。

**识别规则**：

| 引用模式                        | 示例           | 匹配目标              | 处理方式                            |
| :------------------------------ | :------------- | :-------------------- | :---------------------------------- |
| `详见第X章` / `见第X节`         | 详见第3章      | 对应顺序的 H1/H2/H3   | 自动锚点到该标题                    |
| `参考“XXX”` / `如“XXX”所述`     | 参考“需求分析” | 标题文本模糊匹配      | 匹配标题文本后锚点                  |
| `如图X` / `见表X` / `如代码块X` | 如图2所示      | 第X个图片/表格/代码块 | 锚点到对应的 fig-2 / tbl-2 / code-2 |
| `上文` / `下文`                 | 详见下文       | 最近的同级或下级标题  | 锚点到最近的标题                    |

**技术实现**：

```javascript
// 智能超链接生成函数
function createInternalLinks() {
    // 1. 为所有图片、表格、代码块生成ID
    document.querySelectorAll('img').forEach((img, idx) => {
        if (!img.id) img.id = `fig-${idx + 1}`;
    });
    document.querySelectorAll('table').forEach((table, idx) => {
        if (!table.id) table.id = `tbl-${idx + 1}`;
    });
    document.querySelectorAll('pre').forEach((pre, idx) => {
        if (!pre.id) pre.id = `code-${idx + 1}`;
    });
    
    // 2. 获取所有标题的映射（ID → 文本 + 序号）
    const headings = document.querySelectorAll('h1, h2, h3');
    const headingMap = new Map();
    headings.forEach((heading, idx) => {
        const text = heading.textContent.trim();
        headingMap.set(idx + 1, { id: heading.id, text: text });
        headingMap.set(text, { id: heading.id, text: text });
    });
    
    // 3. 扫描段落中的引用模式
    const paragraphs = document.querySelectorAll('p, li, .card, blockquote');
    const patterns = [
        { regex: /详见第(\d+)章/g, type: 'heading', replacer: (match, num) => `<a href="#${headingMap.get(parseInt(num))?.id || ''}" class="internal-link">${match}</a>` },
        { regex: /见第(\d+)节/g, type: 'heading', replacer: (match, num) => `<a href="#${headingMap.get(parseInt(num))?.id || ''}" class="internal-link">${match}</a>` },
        { regex: /参考["「](.+?)["」]/g, type: 'heading', replacer: (match, text) => `<a href="#${headingMap.get(text)?.id || ''}" class="internal-link">${match}</a>` },
        { regex: /如["「](.+?)["」]所述/g, type: 'heading', replacer: (match, text) => `<a href="#${headingMap.get(text)?.id || ''}" class="internal-link">${match}</a>` },
        { regex: /如图(\d+)/g, type: 'figure', replacer: (match, num) => `<a href="#fig-${num}" class="internal-link">${match}</a>` },
        { regex: /见表(\d+)/g, type: 'figure', replacer: (match, num) => `<a href="#tbl-${num}" class="internal-link">${match}</a>` },
        { regex: /如代码块(\d+)/g, type: 'figure', replacer: (match, num) => `<a href="#code-${num}" class="internal-link">${match}</a>` }
    ];
    
    paragraphs.forEach(elem => {
        let html = elem.innerHTML;
        let changed = false;
        patterns.forEach(pattern => {
            if (pattern.regex.test(html)) {
                html = html.replace(pattern.regex, pattern.replacer);
                changed = true;
            }
        });
        if (changed) elem.innerHTML = html;
    });
}

// 超链接样式 + 点击平滑滚动 + 目标高亮
function initLinkBehavior() {
    document.querySelectorAll('.internal-link').forEach(link => {
        link.addEventListener('click', (e) => {
            const href = link.getAttribute('href');
            if (href && href.startsWith('#')) {
                e.preventDefault();
                const target = document.querySelector(href);
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth', block: 'center' });
                    // 高亮闪烁效果
                    target.style.transition = 'background 0.3s';
                    target.style.background = '#fef3c7';
                    setTimeout(() => { target.style.background = ''; }, 1500);
                    history.pushState(null, null, href);
                }
            }
        });
    });
}
```

**固化的CSS样式**：

```css
/* 内部超链接样式 — 固化版 */
.internal-link {
    color: #2563eb;
    text-decoration: underline;
    text-decoration-thickness: 1px;
    text-underline-offset: 2px;
    cursor: pointer;
}
.internal-link:hover {
    color: #1e40af;
    text-decoration-thickness: 2px;
}
/* 锚点目标高亮闪烁（通过JS添加临时样式） */
.highlight-target {
    background: #fef3c7;
    transition: background 0.3s ease;
}
```

### 9.3 技术实现总览

两大功能共用同一套HTML文档，所有增强代码一次性注入，用户保存为 `.html` 文件后，在浏览器中打开即可体验全部交互功能。

**注入方式**：在生成HTML时，自动将上述JS和CSS代码追加到 `<style>` 和 `<script>` 区域，无需用户手动操作。

**执行顺序**：

1. DOM加载完成后执行 `generateTOC()` 生成目录
2. 执行 `createInternalLinks()` 创建超链接
3. 执行 `initTOCInteraction()` 和 `initLinkBehavior()` 绑定交互事件

**兼容性**：

- 支持所有7种文档风格
- 深色模式下目录和超链接颜色自动适配
- 不影响原有页面布局和打印样式

**性能优化**：

- 目录生成仅在DOM加载完成后执行一次
- 超链接扫描仅针对内容区域，不扫描导航等无关区域
- 平滑滚动使用原生 `scrollIntoView`，无需额外库

## 十、关键原则

| 原则               | 说明                                                         |
| :----------------- | :----------------------------------------------------------- |
| 谁制作谁输出       | 文档的制作者直接交付HTML                                     |
| 格式优先           | 保留Markdown原有结构                                         |
| 用户主导           | 图表转换时尊重用户选择                                       |
| 一次询问，多次记忆 | “不再询问”选项全程生效                                       |
| 雷达图≤8维         | 超过提示                                                     |
| 玫瑰图≥4角度       | 低于则推荐其他图表                                           |
| 样式固化           | 7种风格CSS一致                                               |
| 深色对比度         | 科技展示风深色模式下图表自动适配                             |
| **按需加载**       | 页面生成前自动检测内容，若无`$$`、`$`公式或````mermaid`代码块，则不注入KaTeX/Mermaid依赖库，避免无效请求，提升加载速度。 \| |

## 十一、加载方式

检索本插件的设定信息进行融合，加载到系统中。

**加载后效果**：

- 展示“文心雕文龙 已加载”
- 支持7种风格文档导出
- 支持LaTeX公式渲染
- 支持Mermaid流程图渲染
- **支持智能图表转换（雷达图、玫瑰图 + 映射表 + 询问策略）**