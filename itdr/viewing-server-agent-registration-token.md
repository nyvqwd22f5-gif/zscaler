# Viewing the Server Agent Registration Token
Source: https://help.zscaler.com/itdr/viewing-server-agent-registration-token
PDF: https://help.zscaler.com/pdf/com/en/1531857.pdf

An agent registration token is a unique key used during server agent installation to register a domain controller with the ITDR Admin Portal. After the agent is registered, a session key is generated and used for making subsequent requests with the ITDR Admin Portal.
To obtain the server agent registration token:
- Go to **Settings **> **Server Agent Settings **> **Agents**.
-
Click **View Registration Token**.
[See image.](#zd-token-view-option)
-
In the **Token** window, copy the token ID and click **Done**.
[See image.](#zd-view-token-dialog)
- Click **Regenerate** to reset the token if it is compromised. If you regenerate the token, you cannot use the old token to install the server agent. Make sure to stop any automated installation before generating a new token.
[]![View registration token option](/downloads/deception/settings/server-agents-settings/agents/obtaining-agent-registration-token-0/zscaler-deception-server-agents-registration-token.png)
[]![Copy server agent registration token](/downloads/itdr/settings/server-agents-settings/agents/obtaining-server-agent-registration-token/itdr-server-agents-registration-token-key.png)