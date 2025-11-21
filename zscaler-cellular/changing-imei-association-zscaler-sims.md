# Changing the IMEI Association for Zscaler SIMs
Source: https://help.zscaler.com/zscaler-cellular/changing-imei-association-zscaler-sims
PDF: https://help.zscaler.com/pdf/com/en/1524936.pdf

You can modify the IMEI associated with a Zscaler SIM provisioned to your organization from the SIMs page.
To change the IMEI association for a Zscaler SIM:
-
In the left-side navigation, select **SIMs**.
The SIMs page appears.
- On the SIMs page, you can:
- [Modify the IMEI association for a single SIM](#change-imei-association-single-sim)
- [Modify the IMEI association for multiple SIMs](#change-imei-association-multiple-sim)
- []Locate the SIM card for which you want to change the IMEI association.
-
In the **Manage **column, click the **Lock **icon.
[See image.](#lock-icon-manage-column)
Alternatively, you can go to the SIM details page by clicking the **ICCID **link and select the **Update IMEI **option from the **Update **drop-down menu in the top-right corner.
[See image.](#update-imei-sim-details-page)
The Update IMEI Lock/Unlock Info** **window appears.
-
In the Update IMEI Lock/Unlock Info window:
-
If you want to create a new IMEI association or update an existing association, enter the new IMEI value in the **IMEI Lock Value** field.
- You can lock a SIM card to a particular IMEI. To do this, enable **Lock **while creating or updating an IMEI association.
- Updating the lock status without changing the IMEI value is allowed for existing associations.
- If you want to unlock an IMEI from a SIM card, disable **Lock**.
[See image.](#update-imei-single-sim)
-
Click **Save**.
The IMEI association for the SIM card is updated.
The lock is not immediate. After initiation, the SIM enters a pending lock state and might take approximately 15 to 30 minutes to transition into the locked state.
- []Locate and select the SIM cards whose IMEI associations you want to change.
-
Click **Update **and select **Update IMEI**.
[See image.](#update-imei-drop-down)
The Update IMEI Lock/Unlock Info window appears.
-
In the Update IMEI Lock/Unlock Info** **window:
-
If you want to create new IMEI associations or update existing associations, enter the new IMEI values in the **IMEI Lock Value** field for the required SIM cards.
- You can lock a SIM card to a particular IMEI. To do this, enable **Lock **while creating or updating IMEI associations.
- Updating the lock status without changing the IMEI value is allowed for existing associations.
- If you want to unlock IMEI from SIM cards, disable **Lock**.
[See image.](#update-imei-multiple-sims)
-
Click **Save**.
The IMEI associations for the selected SIM cards are updated.
The lock is not immediate. After initiation, the SIM enters a pending lock state and might take approximately 15 to 30 minutes to transition into the locked state.
[]![Option to update IMEI for a SIM card highlighted](/downloads/zscaler-cellular/sims/changing-imei-association-zscaler-sims/zscaler-cellular-lock-option-sims-page.jpg)
[]![The SIM Details page, showing widgets for basic information, current data usage, and a usage graph. The Update drop-down menu shows options for Update Status, Update IMEI, and Update Tags. The Update IMEI option is highlighted.](/downloads/zscaler-cellular/sims/changing-imei-association-zscaler-sims/zscaler-cellular-update-imei-option-details-apge.jpg)
[]![A toggle with Lock selected, a Save button, and a table with columns for ICCID, IMEI, Data Authorize, and Data Authorize Value](/downloads/zscaler-cellular/sims/changing-imei-association-zscaler-sims/zscaler-cellular-single-imei-update.png)
[]![Option to update IMEI from the Update drop-down menu when multiple SIM cards are selected](/downloads/zscaler-cellular/sims/changing-imei-association-zscaler-sims/zscaler-cellular-update-imei-option-sims-page.jpg)
[]![A toggle with Lock selected, a Save button, and a table with columns for ICCID, IMEI, Data Authorize, and Data Authorize Value](/downloads/zscaler-cellular/sims/changing-imei-association-zscaler-sims/zscaler-cellular-multiple-imei-update.png)