# AI_French_CONJUGASION
AI 法语变位大师（Gemini 版）

> **声明**：本仓库的 `index.html` 及本 README 由 AI 生成。  
> **模型限定**：仅使用 Google Gemini「免费」模型 `gemini-2.0-flash`。

一个零后端、单文件（`index.html`）的法语动词变位练习站点。  
在浏览器里调用 Gemini 生成题目与变位表，API Key 只保存在你的浏览器。

---

## 功能
- **分组词库**：自建多个分组，动词可在分组间移动。
- **练习出题（固定规则）**：选择「语言水平 → 练习时态 → 动词来源（分组 / 全库随机）」；开始后**每个动词出 6 题**（六个人称：Je、Tu、Il/Elle/On、Nous、Vous、Ils/Elles）。总题数 = 词数 × 6。
- **变位表弹窗**：支持 Présent / Passé Composé / Imparfait / Futur Simple。
- **纯前端**：只有一个 `index.html`，不用服务器。

---

## 快速开始（本地）
1. 下载本仓库，双击打开 `index.html`。  
2. 进入页面上方 **设置**：粘贴你的 Gemini **API Key**，点 **保存**。  
3. 打开 **词库**：  
   - 新建分组（可选）；  
   - 在当前分组添加动词。  
4. 打开 **练习**：按页面提示选择后，点 **生成题目** 开始。

> 如果双击本地文件打不开或加载不全，建议用 VS Code 的 **Live Server** 打开，或用 **GitHub Pages** 部署。

---

## 获取 API Key（免费）
1. 前往 Google AI Studio：<https://aistudio.google.com/app/apikey>  
2. 创建一个 Key（默认可用 **gemini-2.0-flash** 免费额度）。  
3. 回到本页 **设置** 粘贴保存即可。  
4. 本项目固定使用如下端点（无需改动源码）：https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateConten

---

## 隐私与安全
- **你的 API Key 不会上传**：仅存储在浏览器 `localStorage`。  
- 不要在公共电脑上长期保存 Key。建议为此项目单独生成、随时可停用的 Key。  
- 这是前端项目，访问者可以“查看源代码”。如需保护源码，可将仓库设为**私密**（Pages 仍可发布）。

---

## 常见问题（超简版）
- **400 / Key not valid**：Key 前后有空格或换行；重新粘贴保存。  
- **404 / Model not found**：改动了模型名或端点；请保持 `gemini-2.0-flash` 不变。  

---
