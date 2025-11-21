# Managing URL Allowlist and Denylist Using API
Source: https://help.zscaler.com/zia/managing-url-allowlist-and-denylist-using-api
PDF: https://help.zscaler.com/pdf/com/en/1400421.pdf

The endpoint for managing denylists is `/security/advanced`. You can use this endpoint to retrieve or replace the entire denylist. To add or remove individual URLs to or from the denylist, use the `security/advanced/blacklistUrls` endpoint. The endpoint for managing allowlists is `/security`. You can use this endpoint to retrieve or replace the entire allowlist. However, you cannot add or remove individual URLs to or from the allowlist.
You can add up to 25,000 custom URLs and IPs across all categories (custom and predefined) and your organization's custom denylist and allowlist. For additional information on policy enforcement and prioritization of denylists, see [About Policy Enforcement](/zia/about-policy-enforcement).
Managing a Denylist
To update your custom denylist:
- (Optional) Get the current denylist by sending a GET request to `/security/advanced`.
- Modify the denylist's information by sending a PUT request to `/security/advanced`, and including all of the proper URLs to denylist in the Body. This action completely replaces the previous denylist.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
To add or remove a URL from a denylist:
- (Optional) Get the current denylist by sending a GET request to `/security/advanced`.
- Modify the denylist's information by sending a POST request to `/security/advanced/blacklistUrls`, with the `action` parameter set to `ADD_TO_LIST` or `REMOVE_FROM_LIST`, including all of the proper URLs in the Body.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
To learn more about the endpoints, see Security Policy Settings in the [API Reference](/zia/security-policy-settings).
Managing an Allowlist
To update your custom allowlist:
- (Optional) Get the current allowlist by sending a GET request to `/security`.
- Modify the allowlist's information by sending a PUT request to `/security`, and including all of the proper URLs to allowlist in the Body. This action completely replaces the previous allowlist.
- [Activate the changes to your configuration.](/zia/api-getting-started#ActivateChangestoYourConfiguration)
To learn more about the endpoints, see Security Policy Settings in the [API Reference](/zia/security-policy-settings).
When adding URLs to a denylist or allowlist, if a single URL uses an invalid format, the request is rejected and an error code is produced. A valid URL must meet the following requirements:
- The URL must use a standard URI format.
- The URL length cannot exceed 1024 characters.
- The URL cannot contain non-ASCII characters.
- The domain name before the colon (:) cannot exceed 255 characters.
- The domain name between periods (.) cannot exceed 63 characters.