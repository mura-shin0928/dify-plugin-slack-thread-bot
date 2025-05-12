*以其他语言阅读：[English](README.md)，[日本語](README.ja.md)，[Português](README.pt_BR.md)。*

![license](https://img.shields.io/github/license/solaoi/dify-plugin-slack-thread-bot)

## Slack Thread Bot

**Author:** solaoi
**Version:** 0.0.1
**Type:** 扩展

### 描述

支持线程回复（可选择将第一次回复发布至频道）、mrkdwn格式并可引用线程历史和用户列表的Slack机器人插件。

#### 功能

- 在 Slack 线程中回复（可选设置同时在频道中发送首条回复）
- 在回复中支持 Slack `mrkdwn` 格式
- 从关联的应用中访问线程会话历史和用户信息

#### 安装

要安装此插件，请在选择“安装插件”时指定以下 GitHub 仓库：

https://github.com/solaoi/dify-plugin-slack-thread-bot

#### 设置

按照与官方 SlackBot 插件相同的步骤进行设置。
但需要注意的是，本插件所需的权限范围（scopes）不同：

```
app_mentions:read, users:read, channels:history, groups:history, chat:write, groups:write
```

有关如何设置官方 SlackBot 插件的详细信息，请参阅：

https://github.com/langgenius/dify-official-plugins/blob/main/extensions/slack_bot/README.md

#### 使用方法

将此插件关联到你的 Chat Flow 应用后，你可以在起始节点中通过以下参数获取线程会话历史和线程用户列表：

<img width="409" alt="Image" src="https://github.com/user-attachments/assets/fe84c567-0e56-456e-8ea4-b41f2d43e854" />

```
thread_history：段落，最大长度（如 65535）
thread_users：段落，最大长度（如 65535）
```

示例（Chat Flow 应用中的 LLM 节点）：

<img width="1286" alt="Image" src="https://github.com/user-attachments/assets/03ec5de8-ebfd-40a3-9af8-3dc59ed830e5" />

```
你是一名在 Slack 上回答用户问题的助手。
请参考最近的对话历史并提供合适的回复。

如果需要提及特定用户，请查看用户列表，并使用 `<@ID>` 的格式提及对方。

# 最近的对话历史
开始.thread_history
# 用户列表
开始.thread_users
```
