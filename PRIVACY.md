## Privacy Policy for Slack Thread Bot

This plugin acts as an extension to communicate with the Slack API and facilitate automated replies in Slack threads.

---

**Data Collection**

To function properly, this plugin requires you to provide Slack credentials (e.g., a Bot Token) when configuring the plugin in Dify. The following data is accessed or processed during normal operation:

- **Slack credentials**: Necessary tokens to authenticate and access Slack’s API.  
- **Slack messages and thread conversation history**: Depending on configuration, the plugin may read and process messages within Slack threads to provide replies.  
- **Slack user information**: The plugin may retrieve basic user data (such as user IDs, display names) in order to mention or reference users within threads.

---

**Data Usage**

- **Credentials**: Slack tokens are used solely for making authorized requests to the Slack API.  
- **Message Content**: The plugin processes thread conversation text so it can provide messages to your Dify runtime environment.  
- **User Data**: Information about users in a Slack thread is used only to format mentions (`<@ID>`) or retrieve user context.  
- **Data Retention**: The plugin does not store user data or credentials beyond the necessary runtime context for processing requests. All data is handled in-transit when making API calls.

---

**Third-Party Services / Self-Hosting**

- The plugin communicates directly with Slack’s API, which is governed by Slack’s own privacy policy. For more information, refer to:  
  [https://slack.com/legal](https://slack.com/legal)
- Configuration of Slack (workspace settings, channels, permissions, etc.) is the sole responsibility of the user.
- This plugin is not affiliated with Slack, Inc.
