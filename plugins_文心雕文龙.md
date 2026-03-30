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
| :--- | :--- | :--- | :--- | :--- |
| V0.1.0 | 初稿创建 | 盘古开插件 | 2026-03-24 | 根据用户需求生成 |
| V0.1.1 | 样式固化 | 盘古开插件 | 2026-03-25 | 增加“企微群聊风”文档样式，将6种样式CSS规范固化至插件，确保输出一致性 |
|  |  |  |  |  |
|  |  |  |  |  |

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
- 按以下推荐表为用户提供风格建议：

| 文档类型 | 推荐风格 | 备选风格 |
| :--- | :--- | :--- |
| 会议纪要 | 商务正式风 | 简约阅读风 |
| 技术方案 | 技术文档风 | 商务正式风 |
| 需求文档 | 产品需求风 | 商务正式风 |
| 复盘报告 | 复盘报告风 | 商务正式风 |
| 通用文档 | 简约阅读风 | 商务正式风 |
| 群聊实录 | 企微群聊风 | 简约阅读风 |

**步骤3：样式风格选择**
- 向用户展示6种风格选项，由用户选择
- 选项根据文档类型动态推荐，但用户可自由选择任一风格
- **样式规范已固化，每次选择同一风格输出结果完全一致**

**步骤4：HTML生成**
- 按选定风格调用对应CSS规范生成完整HTML文档
- 内置响应式布局，适配电脑、平板、手机
- Word打开时保留基础格式和样式
- 若选择“企微群聊风”，自动按规则生成头像背景色

**步骤5：交付与提示**
- 直接在对话中输出HTML代码块
- 附保存提示：“复制以上代码 → 保存为 .html 文件 → 浏览器打开或Word编辑”

### 关键规则
- **谁制作谁输出**：文档的制作者直接交付HTML，不经过其他团队中转
- **即时响应**：用户提出保存需求后立即生成
- **格式保留**：Markdown的标题层级、列表、表格、代码高亮、引用块全部保留
- **样式一致**：所有风格CSS规范已固化，保证每次生成结果一致
- **无侵入性**：不改变团队原有的工作流程，仅在用户需要时增加输出环节

## 三、核心能力

### 能力清单
1. **智能内容采集**：自动抓取当前对话中的核心产出内容
2. **文档类型识别**：根据内容特征判断文档类型，适配不同展示需求
3. **多风格HTML渲染**：内置6种文档风格，CSS规范固化，一键切换
4. **响应式布局**：自动适配不同设备屏幕尺寸
5. **Word兼容**：生成的HTML在Word中打开时保留基础格式

## 四、样式规范库（固化版）

以下为6种风格的完整CSS规范，每次生成时严格遵循，确保输出一致性。

---

### 风格1：商务正式风

**适用场景**：会议纪要、汇报材料、正式文档

**设计原则**：白底黑字、庄重、标题带蓝色边框、表格条纹、适合打印

```css
/* 商务正式风 CSS 规范 */
body {
    font-family: 'Times New Roman', '宋体', SimSun, '微软雅黑', serif;
    line-height: 1.6;
    color: #1a2a3a;
    background: #ffffff;
    max-width: 1000px;
    margin: 40px auto;
    padding: 20px;
}
h1 {
    font-size: 1.8rem;
    border-left: 4px solid #2c7cb6;
    padding-left: 16px;
    margin-top: 32px;
    margin-bottom: 20px;
    color: #1e4663;
}
h2 {
    font-size: 1.4rem;
    border-bottom: 2px solid #e6edf4;
    padding-bottom: 8px;
    margin-top: 28px;
    color: #2c5a7a;
}
h3 {
    font-size: 1.2rem;
    margin-top: 20px;
    color: #3a6e8c;
}
table {
    border-collapse: collapse;
    width: 100%;
    margin: 16px 0;
}
th, td {
    border: 1px solid #d0dae8;
    padding: 10px 12px;
    text-align: left;
}
th {
    background-color: #f0f4fa;
    font-weight: 600;
}
tr:nth-child(even) {
    background-color: #fafcff;
}
code {
    background: #f2f4f8;
    padding: 2px 6px;
    border-radius: 4px;
    font-family: monospace;
}
pre {
    background: #f6f8fa;
    padding: 16px;
    border-radius: 8px;
    overflow-x: auto;
}
blockquote {
    border-left: 3px solid #2c7cb6;
    margin: 16px 0;
    padding-left: 16px;
    color: #4a627a;
}
@media print {
    body {
        margin: 0;
    }
    a {
        text-decoration: none;
    }
}
```

### 风格2：技术文档风

**适用场景**：API文档、技术方案、代码说明

**设计原则**：灰白配色、代码块深色高亮、等宽字体、专业感

```css
/* 技术文档风 CSS 规范 */
body {
    font-family: 'SF Mono', 'Fira Code', 'Consolas', monospace;
    line-height: 1.5;
    background: #f9fafc;
    color: #1e2f3e;
    max-width: 1100px;
    margin: 30px auto;
    padding: 20px;
}
h1 {
    font-size: 1.6rem;
    border-bottom: 2px solid #3b82f6;
    padding-bottom: 8px;
    color: #1e3a8a;
    font-weight: 600;
}
h2 {
    font-size: 1.3rem;
    margin-top: 28px;
    color: #2563eb;
}
h3 {
    font-size: 1.1rem;
    color: #3b82f6;
}
pre {
    background: #1e293b;
    color: #e2e8f0;
    padding: 16px;
    border-radius: 10px;
    overflow-x: auto;
    font-size: 0.85rem;
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
table {
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
blockquote {
    border-left: 3px solid #3b82f6;
    background: #f1f5f9;
    padding: 12px 16px;
    margin: 16px 0;
}
```

### 风格3：产品需求风

**适用场景**：PRD、需求文档、功能说明

**设计原则**：卡片式布局、用户故事框、验收标准色块、清晰层级

```css
/* 产品需求风 CSS 规范 */
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
h1 {
    font-size: 1.8rem;
    font-weight: 700;
    color: #0f172a;
    margin-bottom: 24px;
}
h2 {
    font-size: 1.3rem;
    font-weight: 600;
    background: #f8fafc;
    padding: 10px 16px;
    border-radius: 12px;
    margin-top: 32px;
    color: #0f3b5c;
}
.user-story {
    background: #f0f9ff;
    border-left: 4px solid #3b82f6;
    padding: 16px 20px;
    border-radius: 12px;
    margin: 20px 0;
}
.acceptance-criteria {
    background: #fefce8;
    border-left: 4px solid #eab308;
    padding: 16px 20px;
    border-radius: 12px;
    margin: 20px 0;
}
table {
    width: 100%;
    border-collapse: collapse;
    background: white;
    border-radius: 12px;
    overflow: hidden;
}
th, td {
    border: 1px solid #e2e8f0;
    padding: 12px;
    text-align: left;
}
th {
    background: #f1f5f9;
}
code {
    background: #f1f5f9;
    padding: 2px 6px;
    border-radius: 6px;
}
```

### 风格4：复盘报告风

**适用场景**：项目复盘、工作总结、复盘报告

**设计原则**：时间轴布局、问题-改进双栏、醒目结论框、反思感

```css
/* 复盘报告风 CSS 规范 */
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
h1 {
    font-size: 2rem;
    border-left: 6px solid #c2410c;
    padding-left: 20px;
    color: #431407;
}
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
}
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
.improve-box {
    flex: 1;
    background: #ecfdf5;
    padding: 20px;
    border-radius: 16px;
}
.conclusion {
    background: #fffbeb;
    border-top: 4px solid #f97316;
    padding: 20px;
    margin-top: 32px;
    border-radius: 16px;
    font-weight: 500;
}
@media (max-width: 700px) {
    .two-columns {
        flex-direction: column;
    }
}
```

### 风格5：简约阅读风

**适用场景**：长文档、通用文档、知识沉淀

**设计原则**：宽版式、舒适行距、护眼配色、适合长时间阅读

```css
/* 简约阅读风 CSS 规范 */
body {
    font-family: -apple-system, 'Georgia', 'Times New Roman', serif;
    line-height: 1.75;
    background: #fefefe;
    color: #2c3e4e;
    max-width: 860px;
    margin: 48px auto;
    padding: 0 24px;
}
h1 {
    font-size: 2rem;
    font-weight: 600;
    margin-top: 48px;
    margin-bottom: 24px;
    color: #1e4663;
    border-bottom: 1px solid #e2e8f0;
    padding-bottom: 12px;
}
h2 {
    font-size: 1.5rem;
    margin-top: 40px;
    color: #2c5a7a;
}
h3 {
    font-size: 1.25rem;
    margin-top: 32px;
    color: #3a6e8c;
}
p {
    margin-bottom: 1.2em;
}
blockquote {
    font-style: italic;
    border-left: 3px solid #cbd5e1;
    padding-left: 24px;
    color: #4b5565;
}
code {
    background: #f4f4f5;
    padding: 2px 6px;
    border-radius: 8px;
    font-size: 0.9em;
}
pre {
    background: #f9fafb;
    padding: 20px;
    border-radius: 16px;
    overflow-x: auto;
}
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
```

### 风格6：企微群聊风

**适用场景**：群聊记录、对话复盘、团队讨论存档

**设计原则**：企业微信风格：圆头像(汉字)、左右气泡、时间戳、引用回复、系统消息

**头像背景色生成算法**：

- 根据发言人姓名（取第一个汉字）计算哈希值
- 公式：`hue = (hashCode(name) % 360)`
- `saturation: 30%`（柔和，不刺眼）
- `lightness: 70%`（浅色，打印友好）
- 示例：曹植 → 计算得 hue=142°，背景色 `hsl(142, 30%, 70%)`

```css
/* 企微群聊风 CSS 规范 */
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
.group-name {
    font-size: 1.2rem;
    font-weight: 600;
    color: #1f2f3e;
}
.group-members {
    font-size: 0.75rem;
    color: #8a9bb0;
}
.chat-type {
    font-size: 0.7rem;
    background: #eef2f6;
    padding: 2px 8px;
    border-radius: 12px;
    color: #5e6f8d;
    margin-left: auto;
}
.messages-list {
    padding: 16px 20px 24px;
    background: #ffffff;
}
.message {
    display: flex;
    margin-bottom: 20px;
    align-items: flex-start;
    gap: 12px;
}
.message.other {
    flex-direction: row;
}
.message.self {
    flex-direction: row-reverse;
}
.avatar {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
    font-weight: 500;
    flex-shrink: 0;
    box-shadow: 0 1px 2px rgba(0,0,0,0.05);
    /* 背景色由JS按规则动态生成，不在此处固定 */
}
.msg-content {
    max-width: 70%;
    display: flex;
    flex-direction: column;
}
.message.self .msg-content {
    align-items: flex-end;
}
.meta {
    display: flex;
    align-items: baseline;
    gap: 8px;
    margin-bottom: 4px;
    flex-wrap: wrap;
}
.name {
    font-weight: 600;
    font-size: 0.85rem;
    color: #2c3e50;
}
.time {
    font-size: 0.7rem;
    color: #8a9bb0;
}
.bubble {
    background-color: #f2f4f8;
    padding: 8px 14px;
    border-radius: 12px;
    font-size: 0.9rem;
    line-height: 1.45;
    color: #1e2f3e;
    word-break: break-word;
    display: inline-block;
    max-width: 100%;
}
.message.self .bubble {
    background-color: #d9e8ff;
}
.quote-ref {
    background: #eef2f6;
    border-left: 3px solid #7c9bcb;
    padding: 6px 12px;
    border-radius: 8px;
    margin-bottom: 8px;
    font-size: 0.8rem;
    color: #5e6f8d;
}
.quote-name {
    font-weight: 600;
    margin-right: 6px;
    color: #2c5a7a;
}
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
.mention {
    background: #fff0db;
    color: #c76b1c;
    padding: 0 4px;
    border-radius: 12px;
    font-weight: 500;
    font-size: 0.8rem;
    display: inline-block;
    margin-right: 4px;
}
@media print {
    body {
        background: white;
        padding: 0;
    }
    .group-chat {
        box-shadow: none;
        border: 1px solid #ddd;
    }
    .avatar {
        background: #eef2fa !important;
        color: black;
        border: 1px solid #ccc;
    }
    .bubble {
        border: 1px solid #ccc;
        background: #fafafa !important;
    }
    .message.self .bubble {
        background: #f0f0f0 !important;
    }
}
@media (max-width: 600px) {
    .messages-list {
        padding: 12px;
    }
    .msg-content {
        max-width: 85%;
    }
}
```

## 五、插件退出与知识沉淀

### 退出机制

- 本插件为**集成型插件**，不设退出机制
- 每次完成文档输出后自动进入待命状态
- 下一次用户提出保存需求时再次激活

### 知识沉淀

- 生成的HTML文档内容不自动入库
- 用户自行保存.html文件后，可按团队规范归档
- **样式规范已固化**，后续生成同一风格结果完全一致，便于统一存档

## 六、关键原则

| 原则             | 说明                                     |
| :--------------- | :--------------------------------------- |
| **谁制作谁输出** | 文档的制作者直接交付HTML，不增加协作链路 |
| **格式优先**     | 保留Markdown原有结构，确保内容不丢失     |
| **用户主导**     | 风格由用户选择，不自动决定               |
| **即插即用**     | 不改变团队原有流程，仅在需要时介入       |
| **Word兼容**     | 确保生成的HTML可在Word中打开编辑         |
| **响应式**       | 自动适配电脑、平板、手机                 |
| **样式固化**     | 6种风格CSS规范已固化，每次生成结果一致   |
| **头像统一**     | 企微群聊风头像按规则生成，保证一致性     |

## 七、加载方式

检索本插件的设定信息进行融合，加载到系统中。确保团队成员在输出文档时，能够自动启用文档样式转换能力，并严格遵循固化的CSS规范。

**加载后效果**：

- 展示“**文心雕文龙**已加载”
- 当用户在对话中提出“展示文档/保存文档”等需求时，当前执行任务的成员将自动输出格式化的HTML文档，并支持选择6种固化的样式风格。
