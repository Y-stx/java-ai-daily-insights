# java-ai-daily-insights
每日汇总最新的 AI 信息、Java AI GitHub 工程化项目、大厂 AI / Java 招聘线索以及 AI 比赛信息。

## Automation

- 每天 08:30 由 `java-ai-daily-insights.timer` 触发。
- 每次运行会生成一份新的 Markdown 文档：`reports/YYYY-MM-DD-总结核心内容.md`。
- 脚本会更新本 README 的报告索引，并自动 commit/push 到 GitHub。
- 报告内容按固定模板生成：GitHub 热门开源项目、国内大厂招聘动态、行业比赛与活动、AI 应用工程师每日小任务、Java 开发者启发和 token 花费。
- 如果模型 API 可用，报告会记录真实 token usage；如果 API 鉴权或网络失败，会使用本地模板 fallback，并记录模型 API token 为 0。

## Model API

脚本默认调用 OpenAI-compatible `chat/completions` 接口，可通过环境变量适配自己的大模型 API。systemd 服务会读取 `/etc/java-ai-daily-insights.env`。

```bash
MODEL_API_BASE_URL=https://api.example.com
MODEL_API_MODEL=your-model-name
MODEL_API_KEY=your-api-key
```

如果使用 Anthropic Claude API：

```bash
MODEL_API_PROVIDER=anthropic
MODEL_API_BASE_URL=https://api.anthropic.com
MODEL_API_MODEL=claude-sonnet-4-20250514
MODEL_API_KEY=your-anthropic-api-key
```

常用配置：

- `MODEL_API_PROVIDER`：模型服务类型，支持 `openai` / `anthropic`；不配置时会根据 key 和 base URL 自动判断。
- `MODEL_API_ENDPOINT`：完整请求地址；配置后优先于 `MODEL_API_BASE_URL`，适合非标准路径。
- `MODEL_API_BASE_URL`：基础地址；OpenAI-compatible 会自动拼接 `/v1/chat/completions`，Anthropic 会自动拼接 `/v1/messages`。
- `MODEL_API_MODEL`：模型名称；兼容旧变量 `OPENAI_MODEL` 和 `ANTHROPIC_MODEL`。
- `MODEL_API_KEY`：API key；兼容旧变量 `OPENAI_API_KEY` 和 `ANTHROPIC_API_KEY`。
- `MODEL_API_AUTH_HEADER`：鉴权 header，默认 `Authorization`。
- `MODEL_API_AUTH_SCHEME`：鉴权前缀，默认 `Bearer`；如果服务要求直接传 key，可设为空字符串。
- `MODEL_API_TEMPERATURE`：默认 `0.4`。
- `MODEL_API_MAX_TOKENS`：Anthropic 输出上限，默认 `4096`。
- `MODEL_API_EXTRA_HEADERS_JSON`：额外请求头 JSON，例如 `{"HTTP-Referer":"https://example.com"}`。
- `MODEL_API_EXTRA_BODY_JSON`：额外请求体 JSON，例如 `{"max_tokens":4096}`。

## Reports

- [2026-05-28 2026-05-28 Java AI 每日情报](reports/2026-05-28-2026-05-28-java-ai-每日情报.md)
- [2026-05-27 2026-05-27 Java AI 每日情报](reports/2026-05-27-2026-05-27-java-ai-每日情报.md)
- [2026-05-27 Java AI GitHub 工程化项目观察](reports/2026-05-27-java-ai-github-工程化项目观察.md)
- [2026-05-26 Java AI GitHub 工程化项目观察](reports/2026-05-26-java-ai-github-工程化项目观察.md)
