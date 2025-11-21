# Supported AWS IAM Condition Keys and Operators
Source: https://help.zscaler.com/dspm/supported-aws-iam-condition-keys-and-operators
PDF: https://help.zscaler.com/pdf/com/en/1532278.pdf

This article provides the list of AWS IAM condition operators and keys that DSPM supports for managing principal-based (identity-based) and resource-based access for scanning data.
Condition Operators
The following operators are supported:
- [String](#ds-string)
- [ARN](#ds-arn)
- [Boolean](#ds-boolean)
The following operators are not supported:
- Numeric operators (`NumericEquals, NumericNotEquals, NumericLessThan`, etc.)
- Date operators (`DateEquals, DateNotEquals, DateLessThan`, etc.)
- IP Address operators (`IpAddress, NotIpAddress`)
- Binary operators (`BinaryEquals`)
[]
- `StringEquals`
- `StringNotEquals`
- `StringEqualsIgnoreCase`
- `StringNotEqualsIgnoreCase`
- `StringLike`
- `StringNotLike`
- `StringEqualsIfExists`
- `StringNotEqualsIfExists`
- `StringEqualsIgnoreCaseIfExists`
- `StringNotEqualsIgnoreCaseIfExists`
- `StringLikeIfExists`
- `StringNotLikeIfExists`
[]
- `ArnEquals`
- `ArnNotEquals`
- `ArnLike`
- `ArnNotLike`
- `ArnEqualsIfExists`
- `ArnLikeIfExists`
- `ArnNotEqualsIfExists`
- `ArnNotLikeIfExists`
[]
`Bool`
DSPM supports `NotPrincipal` element in IAM policies. To learn more, refer to the[ AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_notprincipal.html).
To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition_operators.html).
Condition Keys
The following keys are supported:
- [Principal-Based Keys](#ds-principal-based)
- [Resource-Based Keys](#ds-resource-based)
[]
- `aws:PrincipalTag/tag-key`
- `aws:PrincipalOrgID`
- `aws:PrincipalArn`
- `aws:PrincipalAccount`
- `aws:PrincipalIsAWSService`
- `aws:PrincipalServiceName`
- `aws:PrincipalServiceNamesList`
- `aws:PrincipalType`
- `aws:userid`
- `aws:username`
[]
- `aws:ResourceTag/tag-key`
- `aws:ResourceAccount`
- `aws:ResourceOrgID`
The following keys are not supported:
- Principal-based condition keys: `aws:PrincipalOrgPaths`: AWS organizations path evaluation
- Resource-based condition keys: `aws:ResourceOrgPaths`: AWS organizations path evaluation
- Network and request context keys:
- `aws:SourceIp`: Source IP address
- `aws:SourceVpc`: Source VPC ID
- `aws:SourceVpce`: Source VPC endpoint ID
- `aws:VpcSourceIp`: VPC source IP address
- `aws:CurrentTime`: Current date or time
- `aws:EpochTime`: Epoch time
- `aws:RequestedRegion`: Requested AWS region
- `aws:SecureTransport`: HTTPS or TLS usage
- `aws:UserAgent`: User agent string
- `aws:referer`: HTTP referer header
- Advanced context keys:
- `aws:CalledVia`: Service call chain
- `aws:CalledViaFirst`: First service in call chain
- `aws:CalledViaLast`: Last service in call chain
- `aws:ViaAWSService`: Called via AWS service
- `aws:SourceAccount`: Source account for service calls
- `aws:SourceArn`: Source ARN for service calls
- `aws:SourceOrgID`: Source organization ID
- `aws:MultiFactorAuthPresent`: MFA authentication
- `aws:MultiFactorAuthAge`: MFA age
- `aws:TokenIssueTime`: Token issue time
When condition keys are not supported, then evaluation of the condition is skipped (e.g., `aws:PrincipalOrgPaths`).
Unsupported Features
The following features are not supported:
- **Numeric and Date Conditions**: No support for numeric or date-based comparisons.
- **Network Context**: No IP address, VPC, or network-based conditions.
- **Time-Based Access**: No support for time-based access controls.
- **MFA Conditions**: No support for MFA validation.
- **Service Integration Context**: Limited support for cross-service condition keys.
- **Organization Paths**: No support for AWS organizations path-based conditions.
- **Dynamic Conditions**: Dynamic conditions like <pre> tag where we have to deduce a value are not supported.