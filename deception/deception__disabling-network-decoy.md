# Disabling a Network Decoy
Source: https://help.zscaler.com/deception/disabling-network-decoy
PDF: https://help.zscaler.com/pdf/com/en/1531277.pdf

You can stop all decoys at once via the Summary page (Deceive > Summary). If you want to stop a single decoy, you can disable it.
To disable a network decoy:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Network Decoys**.
- Select the **Internal** or **Zero Trust Network** tab.
- Navigate to the network decoy you want to disable, and under **Actions**, click the **Edit **icon.
[See image.](#select-edit-decoy)
- In the **Network Decoy Detail** window, select the **General **tab.
- Deselect **Enabled,** and then click **Submit**.
[See image.](#disable-toggle)
The network decoy is disabled and the decoy status icon turns gray (![Gray decoy deployment status icon](/downloads/deception/deceive/network-decoys/disabling-network-decoy/zscaler-deception-gray-icon.png)
).
[See image.](#decoy-disabled)
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys).
You cannot deploy a disabled decoy. You must enable it again to deploy it.
[]![Edit icon on the Internal decoy page](/downloads/deception/deceive/network-decoys/network-decoy-management/disabling-network-decoy/zscaler-deception-disable-decoy-edit-1.png)
[]![Disable network decoy](/downloads/deception/deceive/network-decoys/network-decoy-management/disabling-network-decoy/zscaler-deception-disable-decoy-option.png)
[]![Network decoy disabled](/downloads/deception/deceive/network-decoys/network-decoy-management/disabling-network-decoy/zscaler-deception-disable-decoy-status.png)