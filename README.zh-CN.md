# dsh-hcom

[English](README.md) | 简体中文

让 [DeepSeek Harness（DSH）](https://github.com/deepseek-ai/deepseek-harness) 会话和同一台机器上已接入 [hcom](https://github.com/aannoo/hcom) 的 Claude Code、Codex 等会话互发消息。例如，你可以让 DSH 问 Claude Code 一个 Bug 怎么复现，再在 DSH 里收取对方的回复，省去来回复制。插件由本项目独立维护。

## 安装

安装 hcom 0.7.31，并确保 DSH 进程能从 `PATH` 找到 `hcom`。从 [GitHub Releases](https://github.com/WanchengWildMan/dsh-hcom/releases) 下载安装包，在下载目录执行：

```sh
dsh plugin --profile web add ./dsh-hcom-0.1.0.tgz
dsh web
```

## 收发消息

1. 在 DSH 对话中，请助手调用 `hcom_inbox`，查看当前会话的邮箱名称。
2. 启动另一个 hcom 参与者，例如执行 `hcom claude`。请 DSH 调用 `hcom_send`，按对方的准确名称发送消息。
3. 请对方回复你的邮箱，再调用 `hcom_inbox` 收取回信。

每个 DSH 会话使用独立邮箱。收件需要主动调用工具，来信不会唤醒空闲会话。工具默认使用 hcom 的本机数据目录；如果 DSH 进程设置了 `HCOM_DIR`，则使用该目录。来信属于外部内容，可能记录在 DSH 会话历史中。

如需卸载，执行 `dsh plugin --profile web remove dsh-hcom`，然后重启 DSH。
