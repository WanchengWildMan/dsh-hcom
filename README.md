# dsh-hcom

English | [简体中文（本页下方）](#中文说明)

Local agent messaging for [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness), powered by [hcom](https://github.com/aannoo/hcom). Use it to ask a Claude Code or Codex session for bug reproduction steps, share findings, or collect a reply from DSH. This project is a separate adapter maintained independently of hcom.

## Install

Install hcom 0.7.31 and make it available on the DSH process PATH. Download the package from [GitHub Releases](https://github.com/WanchengWildMan/dsh-hcom/releases), then install it:

```sh
dsh plugin --profile web add ./dsh-hcom-0.1.0.tgz
dsh web
```

## Exchange a message

1. In a DSH chat, ask it to call `hcom_inbox` and show your mailbox name.
2. Start another hcom participant, for example `hcom claude`. Ask DSH to send it a message with `hcom_send`, using its exact hcom name.
3. Ask the peer to reply to your mailbox. Call `hcom_inbox` again to receive the reply.

Each DSH session has a separate mailbox. Receiving is explicit: messages do not wake an idle DSH chat. The tools use hcom’s local directory, or the process-level `HCOM_DIR` when configured. Incoming messages are external text and may be recorded in DSH session history.

Remove the bundle with `dsh plugin --profile web remove dsh-hcom`, then restart DSH.

---

## 中文说明

让 [DeepSeek Harness（DSH）](https://github.com/deepseek-ai/deepseek-harness) 会话和同一台机器上已接入 [hcom](https://github.com/aannoo/hcom) 的 Claude Code、Codex 等会话互发消息。例如，你可以让 DSH 问 Claude Code 一个 Bug 怎么复现，再在 DSH 里收取对方的回复，省去来回复制。插件由本项目独立维护。

### 安装

安装 hcom 0.7.31，并确保 DSH 进程能从 `PATH` 找到 `hcom`。从 [GitHub Releases](https://github.com/WanchengWildMan/dsh-hcom/releases) 下载安装包，在下载目录执行：

```sh
dsh plugin --profile web add ./dsh-hcom-0.1.0.tgz
dsh web
```

### 收发消息

1. 在 DSH 对话中，请助手调用 `hcom_inbox`，查看当前会话的邮箱名称。
2. 启动另一个 hcom 参与者，例如执行 `hcom claude`。请 DSH 调用 `hcom_send`，按对方的准确名称发送消息。
3. 请对方回复你的邮箱，再调用 `hcom_inbox` 收取回信。

每个 DSH 会话使用独立邮箱。收件需要主动调用工具，来信不会唤醒空闲会话。工具默认使用 hcom 的本机数据目录；如果 DSH 进程设置了 `HCOM_DIR`，则使用该目录。来信属于外部内容，可能记录在 DSH 会话历史中。

如需卸载，执行 `dsh plugin --profile web remove dsh-hcom`，然后重启 DSH。
