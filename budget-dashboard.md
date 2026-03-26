# Budget Dashboard — Development Account

## Active Budgets
| Budget Name | Scope | Monthly Limit | Alerts |
|-------------|-------|---------------|--------|
| Monthly-Dev-Budget | All services | $50 | 50%, 80%, 100% actual + 100% forecasted |
| EC2-Monthly-Budget | EC2 only | $30 | 80%, 100% actual |
| Dev-Environment-Budget | Tag: Environment=development | $25 | 80%, 100% actual |

## Notification Channel
- **SNS Topic:** budget-alerts
- **ARN:** arn:aws:sns:us-east-1:741429964627:budget-alerts

## Automated Actions
| Budget | Trigger | Action | Target |
|--------|---------|--------|--------|
| Monthly-Dev-Budget | 100% actual | Apply Deny Policy | developers IAM group |

## Deny Policy Scope
When triggered, the following actions are blocked in us-east-1:
- `ec2:RunInstances`
- `ec2:CreateVolume`
- `rds:CreateDBInstance`
- `lambda:CreateFunction`
