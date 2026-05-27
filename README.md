# java-ai-daily-insights
每日汇总最新的ai信息，各个大厂的最新招聘以及比赛信息

## Automation

- 每天 08:30 由 `java-ai-daily-insights.timer` 触发。
- 每次运行会生成一份新的 Markdown 文档：`reports/YYYY-MM-DD-总结核心内容.md`。
- 脚本会更新本 README 的报告索引，并自动 commit/push 到 GitHub。
- 如果模型 API 可用，报告会记录真实 token usage；如果 API 鉴权或网络失败，会使用本地模板 fallback，并记录模型 API token 为 0。

## Reports

- [2026-05-27 Java AI GitHub 工程化项目观察](reports/2026-05-27-java-ai-github-工程化项目观察.md)
- [2026-05-26 Java AI GitHub 工程化项目观察](reports/2026-05-26-java-ai-github-工程化项目观察.md)
