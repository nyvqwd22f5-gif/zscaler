# API Response Codes and Error Messages
Source: https://help.zscaler.com/zidentity/api-response-codes-and-error-messages
PDF: https://help.zscaler.com/pdf/com/en/1529236.pdf

The following table outlines the HTTP status codes returned by the API.
| Code | Description |
| ---- | ----------- |
| 200 | OK - The request was successful, and the server returned the expected response. |
| 201 | Created - new resource was successfully created. |
| 202 | Accepted - The request has been accepted for processing, but processing has not yet been completed. |
| 204 | No Content - The request was processed successfully, but no content is returned in the response. |
| 400 | Bad Request - The request contains invalid syntax or parameters. |
| 401 | Unauthorized - Authentication is required or provided credentials are incorrect. |
| 403 | Forbidden - Indicates that the server understood the request but did not process it. |
| 404 | Not Found - The requested resource was not found on the server. |
| 406 | Not Acceptable - The server could not provide a response that matches the content type requested by the client. |
| 409 | Conflict - The server encountered a request that conflicts with the current state of the resource. |
| 413 | Payload Too Large - The server cannot process the request because the request's payload exceeds the server's configured limit. |
| 500 | Internal Server Error - An unexpected server issue occurred, preventing the request from being processed. |

## Contents
- **API Developer & Reference Guide**
  - [API Response Codes and Error Messages](/zidentity/api-response-codes-and-error-messages)
  - **Reference Guide**
    - [API Clients](/zidentity/api-clients)
    - [Groups](/zidentity/groups)
    - [Resource Servers](/zidentity/resource-servers)
    - [Users](/zidentity/users)