*Leia em outros idiomas: [English](README.md), [日本語](README.ja.md), [简体中文](README.zh-Hans.md).*

![license](https://img.shields.io/github/license/solaoi/dify-plugin-slack-thread-bot)

## Slack Thread Bot

<img width="120" alt="Image" src="_assets/icon.svg">

**Author:** solaoi
**Version:** 0.0.1
**Type:** extensão

### Descrição

Plugin de bot do Slack com suporte a respostas em thread (opção de postar a primeira resposta no canal), formatação mrkdwn e acesso ao histórico de thread e lista de usuários.

#### Recursos

- Responde dentro de threads no Slack (com a opção de também postar a primeira resposta no canal)
- Suporte a formatação `mrkdwn` do Slack nas respostas
- Acesso ao histórico de conversa de uma thread e às informações de usuário a partir de um aplicativo vinculado

#### Instalação

Para instalar este plugin, ao selecionar "Instale o plugin", especifique o seguinte repositório do GitHub:

https://github.com/solaoi/dify-plugin-slack-thread-bot

#### Configuração

Siga o mesmo procedimento de configuração do plugin oficial SlackBot.
Entretanto, este plugin requer escopos diferentes:

```
app_mentions:read, users:read, channels:history, groups:history, chat:write, groups:write
```

Para mais detalhes sobre como configurar o plugin oficial SlackBot, consulte:

https://github.com/langgenius/dify-official-plugins/blob/main/extensions/slack_bot/README.md

#### Como usar

No nó inicial do aplicativo Chat Flow vinculado a este plugin, você pode fazer referência ao histórico de conversa da thread e à lista de usuários na thread usando os seguintes argumentos:

<img width="407" alt="Image" src="https://github.com/user-attachments/assets/fa979598-0010-41b5-be28-d855a16ac150" />

```
thread_history: Parágrafo, comprimento máximo (ex. 65535)
thread_users: Parágrafo, comprimento máximo (ex. 65535)
```

Exemplo (nó LLM em um aplicativo Chat Flow):

<img width="1285" alt="Image" src="https://github.com/user-attachments/assets/88af22fc-fe9c-43bd-95cd-aae00f174ead" />

```
Você é um assistente no Slack que responde às perguntas dos usuários.
Consulte o histórico recente de conversa e forneça uma resposta apropriada.

Se precisar mencionar um usuário específico, consulte a lista de usuários e mencione-o no formato `<@ID>`.

# Histórico recente de conversa
Iniciar.thread_history
# Lista de usuários
Iniciar.thread_users
```
