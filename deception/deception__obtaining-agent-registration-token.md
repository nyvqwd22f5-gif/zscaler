# Obtaining the Agent Registration Token
Source: https://help.zscaler.com/deception/obtaining-agent-registration-token
PDF: https://help.zscaler.com/pdf/com/en/1531295.pdf

An agent registration token is a unique key used during landmine agent installation to register an endpoint with the Zscaler Deception Admin Portal. After the agent is registered, a session key is generated and is used for making subsequent requests with the Deception Admin Portal.
To obtain the agent registration token:
- Go to **Settings **> **Endpoint Settings **> **Agents**.
-
Click **View Registration Token**.
[See image.](#zd-token-view-option)
-
In the **Token** window, copy the token ID and click **Done**.
[See image.](#zd-view-token-dialog)
Click **Regenerate** to reset the token ID if it is compromised. If you regenerate the token, new landmine agents cannot register with the Deception Admin Portal using the old token. Therefore, make sure that you stop any automated deployment mechanisms or installations before regenerating the token.
[]![View Registration Token option](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/obtaining-agent-registration-token/zscaler-deception-view-registration-token-new.jpg)
[]![Copy landmine agent registration token](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/obtaining-agent-registration-token/zscaler-deception-copy-token.png)