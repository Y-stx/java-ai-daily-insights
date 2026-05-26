<!-- generated_at: 2026-05-26T19:26:43+08:00 -->

# Java AI GitHub 工程化项目观察

> 日期：2026-05-26
> 生成模式：本地模板 fallback

## GitHub 项目观察

### 1. langchain4j/langchain4j
- 描述：LangChain4j is an idiomatic, open-source Java library for building LLM-powered applications on the JVM. It offers a unified API over popular LLM providers and vector stores, and makes implementing tool calling (including MCP support), agents and RAG easy. It integrates seamlessly with enterprise Java frameworks like Quarkus and Spring Boot.
- 语言：Java
- Star：12112
- 最近更新：2026-05-26T09:12:24Z
- 原始链接：https://github.com/langchain4j/langchain4j

### 2. spring-projects/spring-ai
- 描述：An Application Framework for AI Engineering
- 语言：Java
- Star：8795
- 最近更新：2026-05-26T06:44:08Z
- 原始链接：https://github.com/spring-projects/spring-ai

### 3. alibaba/spring-ai-alibaba
- 描述：Agentic AI Framework for Java Developers
- 语言：Java
- Star：9757
- 最近更新：2026-05-24T10:22:45Z
- 原始链接：https://github.com/alibaba/spring-ai-alibaba

### 4. microsoft/semantic-kernel
- 描述：Integrate cutting-edge LLM technology quickly and easily into your apps
- 语言：C#
- Star：27982
- 最近更新：2026-05-25T19:43:04Z
- 原始链接：https://github.com/microsoft/semantic-kernel

### 5. modelcontextprotocol/java-sdk
- 描述：The official Java SDK for Model Context Protocol servers and clients. Maintained in collaboration with Spring AI
- 语言：Java
- Star：3438
- 最近更新：2026-05-26T09:00:53Z
- 原始链接：https://github.com/modelcontextprotocol/java-sdk

### 6. safishamsi/graphify
- 描述：AI coding assistant skill (Claude Code, Codex, OpenCode, Cursor, Gemini CLI, and more). Turn any folder of code, SQL schemas, R scripts, shell scripts, docs, papers, images, or videos into a queryable knowledge graph. App code + database schema + infrastructure in one graph.
- 语言：Python
- Star：53989
- 最近更新：2026-05-26T11:24:04Z
- 原始链接：https://github.com/safishamsi/graphify

### 7. zinja-coder/jadx-mcp-server
- 描述：MCP server for JADX-AI Plugin
- 语言：Python
- Star：627
- 最近更新：2026-05-26T11:22:03Z
- 原始链接：https://github.com/zinja-coder/jadx-mcp-server

### 8. windmill-labs/windmill
- 描述：Open-source developer platform to power your entire infra and turn scripts into webhooks, workflows and UIs. Fastest workflow engine (13x vs Airflow). Open-source alternative to Retool and Temporal.
- 语言：HTML
- Star：16582
- 最近更新：2026-05-26T11:21:55Z
- 原始链接：https://github.com/windmill-labs/windmill

## Java AI 工程趋势

1. Spring 生态仍是 Java 团队接入大模型能力的主要入口，重点关注模型抽象、向量库、工具调用和 RAG 的工程化封装。
2. LangChain4j、Spring AI、MCP Java SDK 代表三类不同切入点：应用编排、Spring 标准化集成、工具协议互联。
3. 真正上线时需要优先处理权限、审计、限流、失败重试、成本观测和数据边界，而不是只停留在 demo 级调用。

## 今天建议关注的行动项

1. 对比 LangChain4j 与 Spring AI 在当前项目技术栈中的接入成本。
2. 为已有内部系统梳理可暴露给 AI 的安全工具接口，提前评估 MCP server/client 的适配价值。
3. 为每日生成流程保留 token usage、数据来源和失败 fallback 记录，便于后续成本复盘。

## Token 使用

- prompt_tokens: 0
- completion_tokens: 0
- total_tokens: 0
- 说明：模型 API 未成功调用，原因：<urlopen error [Errno 101] Network is unreachable>。本次由本地模板生成，因此没有模型 API token 花费。
