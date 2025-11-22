# Storing Passwords as Hashes
Source: https://help.zscaler.com/deception/storing-passwords-hashes
PDF: https://help.zscaler.com/pdf/com/en/1531342.pdf

By default, the credentials that adversaries use to log in to the decoys are usually stored in a plain text format. However, you can enable the hash password feature to store these passwords as SHA256 hashes. This helps you to know if the same password is being attempted multiple times without revealing the actual password.
To store passwords as hashes:
- Go to **Deceive** > **Settings** > **Hash Passwords**.
- Select **Enabled**.
[See image.](#zd-ds-hash-password)
- Click **Save**.
Verifying Hashed Passwords
After enabling the hash password setting, you can test a decoy to simulate an attack, and then verify that the credentials are stored in the hash format.
- Open a web browser.
- In the browser address bar, enter the URL of a decoy with the web service enabled or a threat intelligence decoy.
- After the decoy web page appears, enter credentials in both the username and password fields, and sign in.
- Log in to the Zscaler Deception Admin Portal.
- In the left-side navigation, click **Investigate**.
- Select a time frame from the drop-down menu. For example, select **Last 7 days**.
[See image.](#zd-investigate-window)
- Click the threat icon to open the attacker details pane, and then click **View Extended Details**.
The threat icon  (![Threat icon](/downloads/deception/deceive/deception-settings/storing-passwords-hashes/zscaler-deception-threat-icon.png)
) is unique for each attacker.
[See image.](#zd-attack-score)
- On the **ThreatParse** page, click **Attempted web login** and scroll down to the **Important fields** table to view the credentials submitted by the adversary. The password must be a SHA256 hash of the password submitted while logging in to the decoy.
[See image.](#zd-tp-fields)
[] ![Enable hash password feature](/downloads/deception/deceive/deception-settings/storing-passwords-hashes/zscaler-deception-deceive-setttings-enabled-hash-password.png)
[] ![Investigate threat](/downloads/deception/deceive/deception-settings/storing-passwords-hashes/zscaler-deception-deceive-settings-investigate-threat.png)
[] ![Attacker details pane](/downloads/deception/deceive/deception-settings/storing-passwords-hashes/zscaler-deception-deceive-settings-threatparse.png)
[] ![Verify password in the ThreatParse page](/downloads/deception/deceive/deception-settings/storing-passwords-hashes/zscaler-deception-deceive-settings-threatparse-attempted-web-login.png)