# Modifying Lure Refresh Interval
Source: https://help.zscaler.com/deception/configuring-lure-refresh-interval
PDF: https://help.zscaler.com/pdf/com/en/1531318.pdf

The lure refresh interval is the frequency in which the decoys deployed on an endpoint are refreshed. You can configure the refresh interval (in hours) from the [Agent Configuration](/deception/about-landmine-settings) page.
If you make any changes to the landmine policies, the updates are applied as soon as the landmine agent connects to the Zscaler Deception Admin Portal. The updates do not wait for the lures to refresh.
To configure the lure refresh interval:
- Go to **Settings** > **Endpoint Settings** > **Agent Configuration**.
-
Under the **Agent Settings to Refresh Lures** section, enter a number of hours in the **Refresh Interval (hr)** field.
[See image.](#lure-interval)
- Click **Save**.
[]![A screenshot capturing the Agent Settings to Refresh Lures section](/downloads/deception/deceive/landmine-decoys/landmine-settings/configuring-lure-refresh-interval/zscaler-deception-refresh-lure-interval.png)