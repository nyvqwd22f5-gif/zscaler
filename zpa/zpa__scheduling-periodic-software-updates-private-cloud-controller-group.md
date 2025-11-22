# Scheduling Periodic Software Updates for a Private Cloud Controller Group
Source: https://help.zscaler.com/zpa/scheduling-periodic-software-updates-private-cloud-controller-group
PDF: https://help.zscaler.com/pdf/com/en/1507181.pdf

To ensure that Business Continuity functions properly, Private Cloud Controllers must run on the same or a later software version as the App Connectors and ZPA Private Service Edges.
To schedule a periodic software update for a Private Cloud Controller group:
- Go to **Configuration & Control** > **Business Continuity** > **Business Continuity Management** > **Private Cloud Controller Groups**.
- In the table, locate the Private Cloud Controller group and click the **Edit **icon.
- In the **Edit Private Cloud Controller Group** window, under **Private Cloud Controller Software Update Schedule**, choose the day of the week and start time for the periodic update.
![Scheduling the Periodic Software Update Schedule for the Private Cloud Controller Group](/downloads/zpa/editing-private-cloud-controller-groups/zpa-edit-private-cloud-controller-group-perioidic-software-update.jpg)
- Click **Save**.
To confirm that the update was scheduled, go to the [Private Cloud Controller Groups](/zpa/about-private-cloud-controller-groups) page and verify that the proper day and time is displayed in the **Next Periodic Software Update** column.