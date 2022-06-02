## Automated Security Hub Account Findings Reports

Many customers take advantage of AWS Security Hub allowing them to centrally manage many member accounts from a single AWS Security Hub account. This pattern takes all of the member accounts, creates a custom insight for each account, creates an Amazon SNS topic for each account, and uses Amazon SNS sends the findings to the account's email that is listed in AWS Security Hub automatically on a set schedule.

The purpose this solution provides is automated notifications for how many passed, not passed, failed, and warning findings for each member account in AWS Security Hub to the listed email for the account in AWS Security Hub. The objective is to use these automated notifications to encourage the account to take a look at Security Hub and take action on the findings.

This pattern is an AWS CloudFormation template employs a Lambda that is triggered by a Cloud Watch Event that fires on a set schedule. The Lambda creates a custom insight in AWS Security Hub and Amazon SNS topic for each account. The code is highly customizable by the customer with the ability to change how often the code executes, the custom insight that is created, and the message that is sent. This allows the customer to shape the solution to fit their needs.

## Prerequisites 

This solution requires at least one member account in AWS Security Hub. You can view the help page on how to add and invite member accounts [here](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub-accounts-add-invite.html).


## Limitations 

The limitations of this solution are the quota limits of the services themselves. For example, if AWS Security Hub's quota limit on the number of custom insights is less than the quota limit for number of AWS Security Hub member accounts then this solution may fail to create custom insights in AWS Security Hub if the number of member accounts in use exceeds the quota limit for the number of custom insights.

[Quotas for AWS Security Hub](https://docs.aws.amazon.com/securityhub/latest/userguide/securityhub_limits.html)

## Product versions

The Lambda uses Python 3.9 code.

## Target technology stack  

The AWS CloudFormation template will create a Lambda, Lambda permissions, a CloudWatch Event, and an IAM role with permissions the Lambda needs. Every time the Lambda runs it will attempt to create AWS Security Hub custom insight and Amazon SNS topics.


## Target architecture 

![Architecture Diagram](https://github.com/aws-samples/automated-security-hub-account-findings-reports/blob/main/Solution Diagram.PNG?raw=true)

## Automation and scale

This solution is fully automated. The code is highly customizable with the ability to change how often the code executes, the custom insight that is created, and the message that is sent.



## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

