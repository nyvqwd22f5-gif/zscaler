# First Time Provisioning for Digital Experience Monitoring Admins
Source: https://help.zscaler.com/unified/first-time-provisioning-digital-experience-monitoring-admins
PDF: https://help.zscaler.com/pdf/com/en/1490906.pdf

To onboard Digital Experience Monitoring for your organization, first reach out to Zscaler Support. Support will set up a default admin role and send an email requesting the password be reset for that role. After you have reset that password, you can act as the first default admin to log in and begin creating other admins and roles for Digital Experience Monitoring.
You will be able to see all functions of the Admin Portal due to the default admin role. This default admin role is necessary to onboard Digital Experience Monitoring for your organization, but it is not recommended for day-to-day use. Zscaler recommends creating your own admin user for yourself. This should be used as your primary user details for better auditing and tracking in Digital Experience Monitoring. The default admin user will still exist, but is not recommended for further use.
To complete first time provisioning and establish your own admin user details:
- Go to **Administration **> **Admin Management** > **Role Based Access Control** > **Digital Experience **to configure other admins and admin roles. To learn more, see [About Digital Experience Monitoring Role-Based Administration](/unified/about-digital-experience-monitoring-role-based-administration).
- On the Role Management page, click **Add New ZDX Role**. This role is to pair with the default admin created initially. Even though the default admin settings cannot be changed, a role type is still needed to allow the creation of other admins and role types. To learn more, see [Adding Digital Experience Monitoring Roles](/unified/adding-digital-experience-monitoring-roles).
- Edit the new role to have the highest level of permissions:
- **Dashboard**: View Only
- **Configuration**: Full
- **Admin Management**: Full
- **User & Device Names**: Visible
- **Locations**: View Only
- **User Management**: View Only
- **Save** your changes.