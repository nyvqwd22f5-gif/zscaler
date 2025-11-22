# Copying and Pasting with Clipboard
Source: https://help.zscaler.com/zpa/copying-and-pasting-clipboard
PDF: https://help.zscaler.com/pdf/com/en/1485676.pdf

When you click the Clipboard icon (![Clipboard icon within a privileged console](/downloads/zpa/privileged-remote-access-management/copying-and-pasting-clipboard/Clipboard%20icon_0.png)
) within a privileged console, the Clipboard window appears. In this window, you can copy and paste within the privileged console based on the [privileged capabilities policies](/zpa/configuring-privileged-capabilities-policies) that you have set. If you enable the Clipboard Copy option, you can copy functions from the Privileged Remote Access system to your local system. If you enable the Clipboard Paste option, you can paste functions from your local system to the Privileged Remote Access system. If you have multiple privileged consoles open, copied text is carried over to all of the Clipboard-enabled privileged consoles.
Keep the following in mind when using Clipboard:
- You can only use Clipboard operations when the selected protocol and remote operating system allow it.
- You cannot copy and paste non-ASCII characters with the Clipboard feature if the privileged console is using a VNC protocol or an SSH protocol.
- Clipboard operations between a non-Windows OS and a Windows OS can lead to additional newline characters, as Windows uses a different newline character format.
Clipboard options are disabled by default, but you can still select the Clipboard icon with the options grayed out.
Copying in a Privileged Console
Certain browsers support the Clipboard copy function in a privileged console using your own keyboard. To learn more, see [Browser Behavior](#browser). When using your own keyboard, you need to use the keys associated with copying for the related machine. When your browser doesn't allow the Clipboard copy function with your keyboard, use the following steps:
- Go to the privileged console.
- Highlight the information you want to copy from the privileged console.
- Click the **Clipboard** icon at the bottom of the screen.
The **Clipboard** window appears.
When you enable the Clipboard features in a privileged capabilities policy, a new session needs to be started before the Clipboard permissions take effect. Refreshing the page also refreshes the permissions.
- Click **Copy**. The copied text appears in the** Clipboard** window. If you want to remove the copied text, click **Clear**.
[See image.](#Copy)
- Go to your local system and paste as you normally would within that system.
Pasting in a Privileged Console
Certain browsers support the Clipboard paste function in a privileged console using your own keyboard. When using your own keyboard, you need to use the keys associated with pasting for the receiving machine. To learn more, see [Browser Behavior](#browser). When your browser doesn't allow the Clipboard paste function with your keyboard, use the following steps:
- Copy from your local system. When Clipboard is enabled, the copied content from your local system is periodically synced to the privileged console Clipboard if the browser you are using supports it.
You can only copy and paste up to 4,096 characters.
- Go to the privileged console and navigate to where you want to paste into the privileged console.
Websites or other applications on your device can modify the Clipboard before it is pasted into the privileged console. Ensure the content is not modified before pasting it into your privileged console.
- Click the **Clipboard** icon at the bottom of the screen.
The **Clipboard** window appears.
If you have a current session running and you start Clipboard, then you need to terminate the existing session and start a new session to show the Clipboard icon.
- Click **Paste**. The text is pasted into the privileged console.
[See image.](#Paste)
[]Browser Behavior
When the Clipboard Copy and Paste features are enabled, the Clipboard functions are dependent upon the browser you are using.
If you are using Safari, you can only use the Clipboard window to do copy and paste operations within the privileged console. When using Safari, the browser's **Copy** and **Paste** buttons appear next to the Clipboard **Copy** and **Paste** buttons.
[See image.](#Safaributtons)
If you are using Chrome and have copied from the local system Clipboard and are pasting into the privileged console, a pop-up message from your Chrome browser appears when you attempt the paste operation by keyboard or via the privileged console Clipboard. Click **Allow** to complete the paste.
[See image.](#Chrome)
If you are using Firefox and want to copy from a privileged console and paste into the Firefox browser, you can do so by using either the Clipboard window or the keyboard. If you are copying from the Firefox browser and want to paste into the privileged console, you need to [complete additional configurations on the Firefox side.](#Foxsteps)
[]![Copy in the Clipboard window within a privileged console](/downloads/zpa/privileged-remote-access-management/copying-and-pasting-clipboard/Updated%20Clipboard%20Copy%20Screenshot.png)
[]![Paste in the Clipboard window within a privileged console](/downloads/zpa/privileged-remote-access-management/copying-and-pasting-clipboard/Temporary%20Clipboard%20Paste%20screenshot.png)
[]![Safari browser buttons appear next to Clipboard feature buttons](/downloads/zpa/privileged-remote-access-management/copying-and-pasting-clipboard/Safari%20extra%20buttons.png)
[]![Chrome browser pop up when pasting into a privileged console](/downloads/zpa/privileged-remote-access-management/copying-and-pasting-clipboard/chrome%20pop%20up.png)
- []In the Firefox browser, go to the `about:config` page.
- Set the following options to **true**:
- dom.events.testing.asyncClipboard
- dom.events.asyncClipboard.readText
[See image.](#Firefox)
[]![Firefox browser configurations to use Clipboard paste ](/downloads/zpa/privileged-remote-access-management/copying-and-pasting-clipboard/Firefox.png)