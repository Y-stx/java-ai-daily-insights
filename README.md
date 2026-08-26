# java-ai-daily-insights
每日汇总最新的 AI 信息、Java AI GitHub 工程化项目、大厂 AI / Java 招聘线索以及 AI 比赛信息。

## Automation

- 每天 08:30 由 `java-ai-daily-insights.timer` 触发。
- 每次运行会生成一篇新的 Markdown 学习文章：`reports/YYYY-MM-DD-文章标题.md`。
- 脚本会更新本 README 的报告索引，并自动 commit/push 到 GitHub。
- 文章面向中北大学软件学院大二升大三学生，包含原创标题、目录表、Markdown 图片、Mermaid 图、核心项目解读、最新信息分析、知识拆解和每日动手任务。
- 如果模型 API 可用，文章会调用模型生成；如果模型 API 不可用，脚本会使用本地模板生成同结构的 fallback 文章。

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

- [2026-08-26 2026-08-26 从 Spring AI 看 Java AI 工程化：面向中北大学软件学院大二升大三学生的学习文章](reports/2026-08-26-2026-08-26-从-spring-ai-看-java.md)
- [2026-08-25 2026-08-25 从 modelcontextprotocol/java-sdk 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-25-2026-08-25-从-modelcontextprotocol-java-sdk-看.md)
- [2026-08-24 2026-08-24 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-24-2026-08-24-从-alibaba-spring-ai-alibaba.md)
- [2026-08-23 2026-08-23 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-23-2026-08-23-从-alibaba-spring-ai-alibaba.md)
- [2026-08-22 2026-08-22 从 spring-projects/spring-ai 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-22-2026-08-22-从-spring-projects-spring-ai.md)
- [2026-08-21 2026-08-21 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-21-2026-08-21-从-langchain4j-langchain4j-看-java.md)
- [2026-08-20 2026-08-20 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-20-2026-08-20-从-langchain4j-langchain4j-看-java.md)
- [2026-08-19 2026-08-19 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-19-2026-08-19-从-langchain4j-langchain4j-看-java.md)
- [2026-08-18 2026-08-18 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-18-2026-08-18-从-langchain4j-langchain4j-看-java.md)
- [2026-08-17 2026-08-17 从 dromara/Sa-Token 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-17-2026-08-17-从-dromara-sa-token-看.md)
- [2026-08-16 2026-08-16 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-16-2026-08-16-从-langchain4j-langchain4j-看-java.md)
- [2026-08-15 2026-08-15 从 modelcontextprotocol/java-sdk 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-15-2026-08-15-从-modelcontextprotocol-java-sdk-看.md)
- [2026-08-14 2026-08-14 从 modelcontextprotocol/java-sdk 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-14-2026-08-14-从-modelcontextprotocol-java-sdk-看.md)
- [2026-08-13 2026-08-13 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-13-2026-08-13-从-alibaba-spring-ai-alibaba.md)
- [2026-08-12 2026-08-12 从 modelcontextprotocol/java-sdk 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-12-2026-08-12-从-modelcontextprotocol-java-sdk-看.md)
- [2026-08-11 2026-08-11 从 spring-projects/spring-ai 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-11-2026-08-11-从-spring-projects-spring-ai.md)
- [2026-08-10 2026-08-10 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-10-2026-08-10-从-langchain4j-langchain4j-看-java.md)
- [2026-08-09 2026-08-09 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-09-2026-08-09-从-langchain4j-langchain4j-看-java.md)
- [2026-08-08 2026-08-08 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-08-2026-08-08-从-langchain4j-langchain4j-看-java.md)
- [2026-08-07 2026-08-07 从 codenameone/CodenameOne 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-07-2026-08-07-从-codenameone-codenameone-看-java.md)
- [2026-08-06 2026-08-06 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-06-2026-08-06-从-spring-ai-看-java.md)
- [2026-08-05 2026-08-05 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-05-2026-08-05-从-spring-ai-看-java.md)
- [2026-08-04 2026-08-04 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-04-2026-08-04-从-spring-ai-看-java.md)
- [2026-08-03 2026-08-03 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-03-2026-08-03-从-spring-ai-看-java.md)
- [2026-08-02 2026-08-02 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-02-2026-08-02-从-spring-ai-看-java.md)
- [2026-08-01 2026-08-01 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-08-01-2026-08-01-从-alibaba-spring-ai-alibaba.md)
- [2026-07-31 2026-07-31 从 spring-projects/spring-ai 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-31-2026-07-31-从-spring-projects-spring-ai.md)
- [2026-07-30 2026-07-30 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-30-2026-07-30-从-alibaba-spring-ai-alibaba.md)
- [2026-07-29 2026-07-29 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-29-2026-07-29-从-spring-ai-看-java.md)
- [2026-07-28 2026-07-28 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-28-2026-07-28-从-langchain4j-langchain4j-看-java.md)
- [2026-07-27 2026-07-27 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-27-2026-07-27-从-spring-ai-看-java.md)
- [2026-07-26 2026-07-26 从 ShaftHQ/SHAFT_ENGINE 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-26-2026-07-26-从-shafthq-shaft-engine-看.md)
- [2026-07-25 2026-07-25 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-25-2026-07-25-从-langchain4j-langchain4j-看-java.md)
- [2026-07-24 2026-07-24 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-24-2026-07-24-从-spring-ai-看-java.md)
- [2026-07-23 2026-07-23 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-23-2026-07-23-从-alibaba-spring-ai-alibaba.md)
- [2026-07-22 2026-07-22 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-22-2026-07-22-从-alibaba-spring-ai-alibaba.md)
- [2026-07-21 2026-07-21 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-21-2026-07-21-从-langchain4j-langchain4j-看-java.md)
- [2026-07-20 2026-07-20 从 Spring AI 学 RAG 工程化：给大二升大三学生的 Java AI 学习文章](reports/2026-07-20-2026-07-20-从-spring-ai-学-rag.md)
- [2026-07-19 2026-07-19 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-19-2026-07-19-从-spring-ai-看-java.md)
- [2026-07-18 2026-07-18 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-18-2026-07-18-从-spring-ai-看-java.md)
- [2026-07-17 2026-07-17 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-17-2026-07-17-从-spring-ai-看-java.md)
- [2026-07-16 2026-07-16 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-16-2026-07-16-从-spring-ai-看-java.md)
- [2026-07-15 2026-07-15 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-15-2026-07-15-从-langchain4j-langchain4j-看-java.md)
- [2026-07-14 2026-07-14 从 langchain4j/langchain4j 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-14-2026-07-14-从-langchain4j-langchain4j-看-java.md)
- [2026-07-13 2026-07-13 从 modelcontextprotocol/java-sdk 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-13-2026-07-13-从-modelcontextprotocol-java-sdk-看.md)
- [2026-07-12 2026-07-12 从 Spring AI 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-12-2026-07-12-从-spring-ai-看-java.md)
- [2026-07-11 2026-07-11 从 alibaba/spring-ai-alibaba 看 Java AI 工程化：给大二升大三学生的学习文章](reports/2026-07-11-2026-07-11-从-alibaba-spring-ai-alibaba.md)
- [2026-07-11 2026-07-11 Java AI 每日情报](reports/2026-07-11-2026-07-11-java-ai-每日情报.md)
- [2026-07-10 2026-07-10 Java AI 每日情报](reports/2026-07-10-2026-07-10-java-ai-每日情报.md)
- [2026-07-09 2026-07-09 Java AI 每日情报](reports/2026-07-09-2026-07-09-java-ai-每日情报.md)
- [2026-07-08 2026-07-08 Java AI 每日情报](reports/2026-07-08-2026-07-08-java-ai-每日情报.md)
- [2026-07-07 2026-07-07 Java AI 每日情报](reports/2026-07-07-2026-07-07-java-ai-每日情报.md)
- [2026-07-06 2026-07-06 Java AI 每日情报](reports/2026-07-06-2026-07-06-java-ai-每日情报.md)
- [2026-07-05 2026-07-05 Java AI 每日情报](reports/2026-07-05-2026-07-05-java-ai-每日情报.md)
- [2026-07-04 2026-07-04 Java AI 每日情报](reports/2026-07-04-2026-07-04-java-ai-每日情报.md)
- [2026-07-03 2026-07-03 Java AI 每日情报](reports/2026-07-03-2026-07-03-java-ai-每日情报.md)
- [2026-07-02 2026-07-02 Java AI 每日情报](reports/2026-07-02-2026-07-02-java-ai-每日情报.md)
- [2026-07-01 2026-07-01 Java AI 每日情报](reports/2026-07-01-2026-07-01-java-ai-每日情报.md)
- [2026-06-30 2026-06-30 Java AI 每日情报](reports/2026-06-30-2026-06-30-java-ai-每日情报.md)
- [2026-06-29 2026-06-29 Java AI 每日情报](reports/2026-06-29-2026-06-29-java-ai-每日情报.md)
- [2026-06-28 2026-06-28 Java AI 每日情报](reports/2026-06-28-2026-06-28-java-ai-每日情报.md)
- [2026-06-27 2026-06-27 Java AI 每日情报](reports/2026-06-27-2026-06-27-java-ai-每日情报.md)
- [2026-06-26 2026-06-26 Java AI 每日情报](reports/2026-06-26-2026-06-26-java-ai-每日情报.md)
- [2026-06-25 2026-06-25 Java AI 每日情报](reports/2026-06-25-2026-06-25-java-ai-每日情报.md)
- [2026-06-24 2026-06-24 Java AI 每日情报](reports/2026-06-24-2026-06-24-java-ai-每日情报.md)
- [2026-06-23 2026-06-23 Java AI 每日情报](reports/2026-06-23-2026-06-23-java-ai-每日情报.md)
- [2026-06-22 2026-06-22 Java AI 每日情报](reports/2026-06-22-2026-06-22-java-ai-每日情报.md)
- [2026-06-21 2026-06-21 Java AI 每日情报](reports/2026-06-21-2026-06-21-java-ai-每日情报.md)
- [2026-06-20 2026-06-20 Java AI 每日情报](reports/2026-06-20-2026-06-20-java-ai-每日情报.md)
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
