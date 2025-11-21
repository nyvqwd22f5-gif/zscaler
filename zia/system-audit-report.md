# System Audit Report
Source: https://help.zscaler.com/zia/system-audit-report

API Reference Guide for the ZIA Cloud Service and Sandbox Submission APIs

**Base URL:** https://zsapi.[zscaler-cloud-name]/api/v1

## `GET /configAudit`

Retrieves the System Audit Report. To learn more, see [About the System Audit Report](/zia/about-system-audit-report).
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** System Audit Report
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | ConfigAudit |

## `GET /configAudit/ipVisibility`

Retrieves the IP visibility audit report.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** System Audit Report
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | IpVisibilityAudit |

## `GET /configAudit/pacFile`

Retrieves the PAC file audit report.
**Note**: This endpoint is accessible via [Zscaler OneAPI](/oneapi/understanding-oneapi) only.

**Tags:** System Audit Report
**Consumes:** application/json
**Produces:** application/json
No parameters.

| Code | Description | Schema |
| ---- | ----------- | ------ |
| 200 | Successful Operation | PacFileAudit |

## Models
### AuthFrequency
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| authCustomFrequency | integer (int32) | No |  |
| authFrequency | string | No |  |

### ConfigAudit
Configuration audit information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| authFrequency | AuthFrequency | No | Authentication frequency |
| authFrequencyGrade | string | No | The rubric used to grade the authentication frequency |
| authFrequencyRecommendedConfiguration | string | No | Auth frequency recommended configuration |
| dataPresent | boolean | No | Data present flag |
| greTunnelGrade | string | No | The rubric used to grade GRE tunnels |
| greTunnelRecommendedConfiguration | string | No | GRE tunnel recommended configuration |
| highAvailabilityGrade | string | No | The rubric used to grade the High Availability Configuration for GRE tunnels and PAC files |
| ipVisibilityGrade | string | No | The rubric used to grade IP visibility |
| ipVisibilityRecommendedConfiguration | string | No | IP visibility recommended configuration |
| office365Flag | boolean | No | Office 365 One Click flag |
| office365Grade | string | No | Office 365 One Click grade |
| office365RecommendedConfiguration | string | No | Microsoft-recommended One Click Office 365 configuration |
| otherGrade | string | No | The rubric used to grade the Microsoft-Recommended Office 365 One Click Configuration and IP visibility |
| overallGrade | string | No | The rubric used to grade the report containing the overall grades for High Availability Configuration and User Performance Configuration combined. |
| pacFileGrade | string | No | The rubric used to grade PAC files |
| pacFileRecommendedConfiguration | string | No | PAC file recommended configuration |
| pacFileSizeRecommendedConfiguration | string | No | Pac file size recommended configuration |
| pacfileSizeGrade | string | No | The rubric used to grade the PAC file size |
| reportTimestamp | integer (int64) | No | Report timestamp |
| userPerformanceGrade | string | No | The rubric used to grade the User Performance Configuration for authentication frequency and PAC file |

### IpVisibilityAudit
IP visibility audit information
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| details | string | No | GRE tunnels audit details |
| locationsWithNat | array[string] | No | Locations with NAT |
| recommendation | string | No | GRE tunnels audit recommendation |
| totalGreLocations | integer (int32) | No | Total GRE locations |

### PacFileAudit
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| pacWithStaticIPs | array[PacWithStaticIp] | No | Total PAC files with static IPs |
| totalPacFiles | integer (int32) | No | Total PAC files |

### PacWithStaticIp
| Field | Type | Required | Description |
| ----- | ---- | -------- | ----------- |
| pacFileName | string | No |  |
| staticServiceIps | array[string] | No |  |
| staticVirtualIps | array[string] | No |  |
