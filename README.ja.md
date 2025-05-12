*他の言語で読む: [English](README.md), [简体中文](README.zh-Hans.md), [Português](README.pt_BR.md).*

![license](https://img.shields.io/github/license/solaoi/dify-plugin-slack-thread-bot)

## Slack Thread Bot

**Author:** solaoi
**Version:** 0.0.1
**Type:** 拡張機能

### 解説

スレッド返信（初回返信をチャンネルにも投稿可能）、mrkdwn対応、スレッド履歴やユーザーリストへの参照ができるSlackボットプラグイン。

#### 機能

- スレッド内での返信（初回の返信をチャンネルにも投稿できるオプション付き）
- Slack 上での `mrkdwn` フォーマットに対応
- 紐づけたチャットフローアプリから、スレッド履歴やユーザー情報を参照可能

#### インストール方法

「プラグインをインストールする」画面で、以下のGitHubリポジトリを指定してインストールしてください。

https://github.com/solaoi/dify-plugin-slack-thread-bot

#### 設定手順

公式のSlackBotプラグインと同様の手順で設定してください。
ただし、本プラグインでは下記のスコープが必要となります。

```
app_mentions:read, users:read, channels:history, groups:history, chat:write, groups:write
```

公式のSlackBotプラグインのセットアップ手順については以下をご参照ください。

https://github.com/langgenius/dify-official-plugins/blob/main/extensions/slack_bot/README.md

#### 使い方

このプラグインを紐づけるチャットフローアプリの「開始ノード」で、以下の引数を設定することで、スレッド内の会話履歴やユーザー一覧を参照できます。

<img width="407" alt="Image" src="https://github.com/user-attachments/assets/76e2a560-2440-48ee-9acb-266c3e417a72" />

```
thread_history: 段落（例：最大長 65535）
thread_users: 段落（例：最大長 65535）
```

例：チャットフローアプリ内のLLMノード

<img width="1288" alt="Image" src="https://github.com/user-attachments/assets/05f066c0-d1ed-457d-b4c3-bb2dc69ab97e" />

```
あなたはSlack上でユーザーの質問に答えるアシスタントです。
直近の会話履歴を参照して、適切な回答をお願いします。

なお、特定のユーザーに向けてメンションする場合は、
ユーザーリストを参照して、`<@ID>` 形式でメンションしてください。

# 直近の会話履歴
開始.thread_history
# ユーザーリスト
開始.thread_users
```
