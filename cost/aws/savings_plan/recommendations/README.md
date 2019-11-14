# AWS Savings Plan Recommendations

## NOTE: These Savings Plan Purchase Recommendations are generated by AWS. This policy will raise incidents based on those recommendations

### What it does

This Policy Template leverages the [AWS Cost Explorer API](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetSavingsPlansPurchaseRecommendation.html). It will raise incidents if AWS has any Savings Plan Purchase Recommendations, whose monthly savings exceeds the *Monthly Savings Threshold* parameter in the Policy.

It will email the user specified in `Email addresses of the recipients you wish to notify`

### Prerequisites

- The following RightScale Credentials
  - `AWS_ACCESS_KEY_ID` - The Access Key of an IAM User in the Master Payer account, which has access to Cost Explorer.
  - `AWS_SECRET_ACCESS_KEY` - The Secret Access Key of the IAM User.

#### AWS Required Permissions

This policy requires permissions to describe AWS Cost Explorer.
The IAM user will require the following permissions:

```javascript
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ce:*"
      ],
      "Resource": [
        "*"
      ]
    }
  ]
}
```

### Input Parameters

This policy has the following input parameters required when launching the policy.

- *Look Back Period* - Specify the number of days of past usage to analyze.
- *Savings Plan Term* - Specify he Term length for the Savings Plan.
- *Payment Option* - Specify the payment option for the Savings Plan.
- *Savings Plan Type* - Choose between Compute Savings Plans or EC2 Instance Savings Plans
- *Monthly Savings Threshold* - Specify the minimum monthly savings that should result in a Savings Plan purchase recommendation
- *Email addresses to notify* - A list of email addresses to notify

### Policy Actions

- Send an email report

### Required RightScale Roles

- Cloud Management - credential_viewer

### Supported Clouds

- AWS

### Cost

This Policy Template does not launch any instances, and so does not incur any cloud costs.