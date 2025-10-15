*他の言語で読む: [English](https://github.com/solaoi/dify-plugin-slack-thread-bot/blob/v0.0.5/README.md), [简体中文](https://github.com/solaoi/dify-plugin-slack-thread-bot/blob/v0.0.5/README.zh-Hans.md), [Português](https://github.com/solaoi/dify-plugin-slack-thread-bot/blob/v0.0.5/README.pt_BR.md).*

![license](https://img.shields.io/github/license/solaoi/dify-plugin-slack-thread-bot)

## Slack Thread Bot

<img width="120" alt="Image" src="_assets/icon.svg">

**Author:** mura-shin0928
**Version:** 0.0.1
**Type:** 拡張機能

### 解説

スレッド返信（初回返信をチャンネルにも投稿可）、Slackファイルアップロード、mrkdwn対応、スレッド履歴・ユーザーリスト参照、任意で利用チャンネルを制限可能なSlackボットプラグイン。

#### 機能

- スレッド内での返信（初回の返信をチャンネルにも投稿できるオプション付き）
- Slackファイルのアップロード（紐づけたチャットフローアプリから、参照可能）
- Slack 上での `mrkdwn` フォーマットに対応
- 紐づけたチャットフローアプリから、スレッド履歴・ユーザー情報・Slackスレッド情報（ `channel_id`, `thread_ts` ）を参照可能
- 単一のSlackチャンネルへ利用を限定し、よりセキュアな運用を可能にするオプション

> [!NOTE]
> `channel_id` と `thread_ts` は主に高度なユースケース向けのパラメータです。通常のシナリオでは使用しないことがほとんどですが、[Slack Post](https://github.com/solaoi/dify-plugin-slack-post) プラグインをインストールしている場合、特定のチャンネルやスレッドへの投稿にこれらのパラメータを活用でき、Slack Thread Bot とアプリケーションをさらに深く連携させることができます。

#### 1. インストール方法

「プラグインをインストールする」画面で、以下のGitHubリポジトリを指定してインストールしてください。

https://github.com/solaoi/dify-plugin-slack-thread-bot

#### 2. 設定手順

公式のSlackBotプラグインと同様の手順で設定してください。
ただし、本プラグインでは下記のスコープが必要となります。

```text
app_mentions:read, users:read, channels:history, groups:history, chat:write, groups:write, channels:read,
groups:read, files:read
```

また、Slackアプリの設定で「Subscribe to bot events」を構成する際、以下のイベントを追加する必要があります：
- `app_mention` - ボットがメンションされたとき
- `message.channels` - パブリックチャンネルでメッセージを受信（スレッドキャッシュに必要）
- `message.groups` - プライベートチャンネルでメッセージを受信（スレッドキャッシュに必要）

`message.channels`と`message.groups`イベントは、ボットのキャッシング機能に不可欠です。これにより、Slackの厳しいレート制限（スレッド履歴取得は1分間に1回）を回避し、レート制限に達することなくリアルタイムでスレッドのコンテキストを維持できます。

公式のSlackBotプラグインのセットアップ手順については以下をご参照ください。

https://github.com/langgenius/dify-official-plugins/blob/main/extensions/slack_bot/README.md

#### 3. 使い方

このプラグインを紐づけるチャットフローアプリの「開始ノード」で、以下の引数を設定することで、スレッド内の会話履歴やユーザー一覧を参照できます。

<div align="left">
  <img src="_assets/how_to_use_1_ja.png" width="50%"/>
</div>

| 入力フィールド | フィールドタイプ |
| ---- | ---- |
| thread_history | 段落（例：最大長 65535） |
| thread_users | 段落（例：最大長 65535） |
| files | ファイルリスト |
| thread_ts | 短文（例：最大長 48（デフォルト）） |
| channel_id | 短文（例：最大長 48（デフォルト）） |

例：チャットフローアプリ内のLLMノード

<div align="left">
  <img src="_assets/how_to_use_2_ja.png" width="80%"/>
</div>

```text
あなたはSlack上でユーザーの質問に答えるアシスタントです。
直近の会話履歴を参照して、適切な回答をお願いします。

なお、特定のユーザーに向けてメンションする場合は、
ユーザーリストを参照して、`<@ID>` 形式でメンションしてください。

# 直近の会話履歴
開始.thread_history
# ユーザーリスト
開始.thread_users
```
