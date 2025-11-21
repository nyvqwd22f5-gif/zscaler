# Deleting Agents
Source: https://help.zscaler.com/zpa/deleting-agents
PDF: https://help.zscaler.com/pdf/com/en/1531954.pdf

Admins can [configure](/zpa/configuring-agents), [edit](/zpa/editing-agents), and delete agents as needed.
To delete an agent:
- Go to **Microsegmentation** > **Agent Management**.
- Click the** Agents** tab.
- Click the **Delete **icon for the agent you want to delete.
The **Delete Agent** confirmation window appears.
[See image.](#Agent-Management_Delete-Agent)
- Click **Delete**.
[See image.](#Delete-Agent-window)
Deleting an agent does not remove it from the Agent list, because it still exists in the workload services. Deleted agents are only unregistered in the system. The agent must be manually uninstalled from the workload, otherwise the resource reported by the agent is marked as Deleted. Deleted resources might appear in the Application map when viewing historical flows until the logs roll over every 14 days.
[]![A view of the Agents page and all its actions.](/downloads/tech-pubs-drafts/zws-draft-articles/deleting-agents/Agent-Management_Agents_Delete-Agent.png)
[]![A confirmation box appears when deleting an agent.](/downloads/tech-pubs-drafts/zws-draft-articles/deleting-agents/Delete-Agent_confirmation-window.png)