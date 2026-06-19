# java-ai-daily-insights
每日汇总最新的 AI 信息、Java AI GitHub 工程化项目、大厂 AI / Java 招聘线索以及 AI 比赛信息。

## Automation

- 每天 08:30 由 `java-ai-daily-insights.timer` 触发。
- 每次运行会生成一份新的 Markdown 文档：`reports/YYYY-MM-DD-总结核心内容.md`。
- 脚本会更新本 README 的报告索引，并自动 commit/push 到 GitHub。
- 报告内容按固定模板生成：GitHub 热门开源项目、国内大厂招聘动态、行业比赛与活动、AI 应用工程师每日小任务和 Java 开发者启发。
- 如果模型 API 可用，报告会调用模型生成；如果模型 API 鉴权失败，脚本会停止生成，避免提交重复的本地 fallback 报告。

## Model API

脚本默认调用 OpenAI-compatible `chat/completions` 接口，可通过环境变量适配自己的大模型 API。systemd 服务会读取 `/etc/java-ai-daily-insights.env`。

```bash
MODEL_API_BASE_URL=https://api.example.com
MODEL_API_MODEL=your-model-name
MODEL_API_KEY=your-api-key
```

如果使用 Codex/OpenAI-compatible API，即使 token 是 `sk-ant-` 格式，也应显式声明
`MODEL_API_PROVIDER=openai`，并使用该服务提供的 `/v1` 兼容地址：

```bash
MODEL_API_PROVIDER=openai
MODEL_API_BASE_URL=https://dm-fox.rjj.cc/codex/v1
MODEL_API_MODEL=gpt-5.5
MODEL_API_KEY=your-codex-api-key
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

- [2026-06-19 2026-06-19 Java AI 每日情报](reports/2026-06-19-2026-06-19-java-ai-每日情报.md)
- [2026-06-18 2026-06-18 Java AI 每日情报](reports/2026-06-18-2026-06-18-java-ai-每日情报.md)
- [2026-06-17 2026-06-17 Java AI 每日情报](reports/2026-06-17-2026-06-17-java-ai-每日情报.md)
- [2026-06-16 2026-06-16 Java AI 每日情报](reports/2026-06-16-2026-06-16-java-ai-每日情报.md)
- [2026-06-15 2026-06-15 Java AI 每日情报](reports/2026-06-15-2026-06-15-java-ai-每日情报.md)
- [2026-06-14 一、GitHub 热门开源项目](reports/2026-06-14-一-github-热门开源项目.md)
- [2026-06-13 2026-06-13 Java AI 每日情报](reports/2026-06-13-2026-06-13-java-ai-每日情报.md)
- [2026-06-12 2026-06-12 Java AI 每日情报](reports/2026-06-12-2026-06-12-java-ai-每日情报.md)
- [2026-06-11 2026-06-11 Java AI 每日情报](reports/2026-06-11-2026-06-11-java-ai-每日情报.md)
- [2026-06-10 2026-06-10 Java AI 每日情报](reports/2026-06-10-2026-06-10-java-ai-每日情报.md)
- [2026-06-09 2026-06-09 Java AI 每日情报](reports/2026-06-09-2026-06-09-java-ai-每日情报.md)
- [2026-06-08 2026-06-08 Java AI 每日情报](reports/2026-06-08-2026-06-08-java-ai-每日情报.md)
- [2026-06-07 2026-06-07 Java AI 每日情报](reports/2026-06-07-2026-06-07-java-ai-每日情报.md)
- [2026-06-06 2026-06-06 Java AI 每日情报](reports/2026-06-06-2026-06-06-java-ai-每日情报.md)
- [2026-06-05 2026-06-05 Java AI 每日情报](reports/2026-06-05-2026-06-05-java-ai-每日情报.md)
- [2026-06-04 2026-06-04 Java AI 每日情报](reports/2026-06-04-2026-06-04-java-ai-每日情报.md)
- [2026-06-03 2026-06-03 Java AI 每日情报](reports/2026-06-03-2026-06-03-java-ai-每日情报.md)
- [2026-06-02 2026-06-02 Java AI 每日情报](reports/2026-06-02-2026-06-02-java-ai-每日情报.md)
- [2026-06-01 2026-06-01 Java AI 每日情报](reports/2026-06-01-2026-06-01-java-ai-每日情报.md)
- [2026-05-31 2026-05-31 Java AI 每日情报](reports/2026-05-31-2026-05-31-java-ai-每日情报.md)
- [2026-05-30 2026-05-30 Java AI 每日情报](reports/2026-05-30-2026-05-30-java-ai-每日情报.md)
- [2026-05-29 2026-05-29 Java AI 每日情报](reports/2026-05-29-2026-05-29-java-ai-每日情报.md)
- [2026-05-28 2026-05-28 Java AI 每日情报](reports/2026-05-28-2026-05-28-java-ai-每日情报.md)
- [2026-05-27 2026-05-27 Java AI 每日情报](reports/2026-05-27-2026-05-27-java-ai-每日情报.md)
- [2026-05-27 Java AI GitHub 工程化项目观察](reports/2026-05-27-java-ai-github-工程化项目观察.md)
- [2026-05-26 Java AI GitHub 工程化项目观察](reports/2026-05-26-java-ai-github-工程化项目观察.md)
