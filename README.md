*Read this in other languages: [日本語](README.ja.md), [简体中文](README.zh-Hans.md), [Português](README.pt_BR.md).*

![license](https://img.shields.io/github/license/solaoi/dify-plugin-slack-thread-bot)

## Slack Thread Bot

**Author:** solaoi
**Version:** 0.0.1
**Type:** extension

### Description

Slack bot plugin supporting thread replies (optionally posting the first reply in the channel), mrkdwn formatting, and referencing thread history and user list.

#### Features

- Reply within Slack threads (with an optional setting to also post the first reply in the channel)
- Support for Slack `mrkdwn` formatting in replies
- Access to thread conversation history and user information from a linked app

#### Install

To install this plugin, specify the following GitHub repository when selecting "Install Plugin":

https://github.com/solaoi/dify-plugin-slack-thread-bot

#### Setup

Follow the same setup procedure as the official SlackBot plugin.
However, this plugin requires different scopes:

```
app_mentions:read, users:read, channels:history, groups:history, chat:write, groups:write
```

For details on how to set up the official SlackBot plugin, see:

https://github.com/langgenius/dify-official-plugins/blob/main/extensions/slack_bot/README.md

#### How to use

In the start node of the chat flow app that you link to this plugin, you can reference the conversation history and the list of users in the thread using the following arguments:

<img width="414" alt="Image" src="https://github.com/user-attachments/assets/443ea297-512a-4f5f-8296-fba4ecb45f25" />

```
thread_history: Paragraph, maximum length (eg. 65535)
thread_users: Paragraph, maximum length (eg. 65535)
```

Example (LLM node in the chat flow app):

<img width="1286" alt="Image" src="https://github.com/user-attachments/assets/91a58bc1-02e0-4481-8cbe-6187298e6dd7" />

```
You are an assistant on Slack who answers user questions.
Refer to the recent conversation history and provide an appropriate response.

If you need to mention a specific user, refer to the user list and mention them in the format `<@ID>`.

# Recent conversation history
Start.thread_history
# User list
Start.thread_users
```
