# AI Conjugaison（多模型）
法语动词变位练习站点。零后端，API Key 仅存浏览器本地。

直链：https://a1batr055.github.io/AI_French_CONJUGAISON/

> ❗️必要条件：需科学上网。  
> 前端直连可能暴露 API Key，请自行评估风险。  
> 本项目与 README 由 AI 辅助生成。
> **建议减少每次生成词量**，以免等待时间过长或模型返回文本失败。

---

## 功能
- 分组词库：自建分组，动词可在分组间移动
- 练习出题：按 CEFR 等级与时态生成；每动词固定 6 题（六个人称）
- 变位表弹窗：Présent / Passé Composé / Imparfait / Futur Simple 等
- 多家 LLM：OpenRouter（含免费）/ OpenAI / Google Gemini / DeepSeek / 自定义

---

## 快速上手（建议用 OpenRouter 免费模型）
1. 在 openrouter.ai 注册并创建 API Key：  
   https://openrouter.ai/docs/quickstart
2. 打开本站 → “设置” → 选择 **OpenRouter** → 粘贴 Key。
3. 在“模型”选择任一 **:free** 免费模型 → 保存。
4. 切到“练习”，选择等级、时态与词源 → 生成题目。

常见免费模型（以目录实际为准）：
- `google/gemini-2.0-flash-exp:free`
- `openai/gpt-oss-20b:free`、`openai/gpt-oss-120b:free`
- `deepseek/deepseek-chat:free`
- `mistralai/mistral-small:free`

OpenRouter 免费额度（官方说明）：
- 约 20 次/分钟
- 日配额：余额 < \$10 → 50 次/天；余额 ≥ \$10 → 1000 次/天（仅 :free 模型）
参考：https://openrouter.ai/pricing

> 计数按“请求”计算（点一次“生成题目”=1 次；“查看变位表”=1 次）。

---

## 其他提供商
- OpenAI：需 OpenAI API Key
- Google Gemini：需 Google API Key（免费层配额/限速调整频繁）  
  参考：https://ai.google.dev/gemini-api/docs/rate-limits
- DeepSeek：需 DeepSeek API Key
- 自定义：填兼容 OpenAI 协议的 Base URL 与模型 ID

---

## 常见报错与处理（先尝试刷新、换节点、换流量）
- 429 / rate limit / quota：限流或额度耗尽 → 间隔 1–5 分钟重试、换模型或换时段；OpenRouter 余额 ≥ \$10 可获 1000 次/天  
  限制说明：https://openrouter.ai/docs/api/reference/limits  
  Gemini 限速参考：https://ai.google.dev/gemini-api/docs/rate-limits
- 401 / unauthorized：Key 无效/未授权 → 检查 Key、提供商与权限  
  认证说明：https://openrouter.ai/docs/api/reference/authentication
- 404 / model_not_found：模型下线或拼写错误 → 改用内置推荐/免费模型
- 400 / bad request：请求体不合规（Base URL、模型 ID 错）→ 恢复默认，仅改“提供商 + 模型”重试
- 5xx：上游不稳定 → 更换免费模型或稍后重试

OpenRouter Chat Completions 规范：  
https://openrouter.ai/docs/api/reference/overview

---

## 费用与安全
- OpenRouter 免费模型不收费，但受速率与日配额限制；非免费模型按标价计费：  
  https://openrouter.ai/pricing
- 纯前端：Key 与词库保存在浏览器 `localStorage`。避免在公共环境暴露 Key。
- 生产环境建议加后端代理，统一保管 Key 并做限流。

---

## FAQ
**Q：配额按题量还是请求计？**  
A：按“请求”计。见：https://openrouter.ai/docs/api/reference/limits

**Q：Gemini 频繁 429？**  
A：多为额度/限速触发；以官方 Rate limits 与控制台为准：  
https://ai.google.dev/gemini-api/docs/rate-limits

**Q：列表里没有想用的模型？**  
A：免费清单会变动；可用“自定义模型 ID”。（OpenRouter 兼容 OpenAI `/chat/completions` 协议。）  
FAQ：https://openrouter.ai/docs/faq

**Q：如何清除本地数据？**  
清空站点存储并刷新，或控制台执行：
```js
localStorage.removeItem('llm_settings');
localStorage.removeItem('verb_groups');
