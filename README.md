# dsh-hcom

Local agent messaging for [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness), powered by [hcom](https://github.com/aannoo/hcom). hcom is developed by its upstream maintainers; this project is a separate DSH adapter.

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
