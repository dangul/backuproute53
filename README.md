# backuproute53
This cloudformation template creates

* Lambda with python 3.13 code to backup all route53 zones in a account
* EventBridge rule to trigger Lambda
* CloudWatch log group to monitor process
* IAM policy & role with least privileges 

### Stack details:  

**S3BucketName** - Bucket to store route53 zones  
**DestinationKMS** - KMS key (arn) for S3 bucket  
**ScheduleExpression** - Cron expression when Lambda should be triggered  

**Example** :  
S3BucketName = Route53Zones  
DestinationKMS = arn:aws:kms:eu-north-1:xxxxxxxxxxxx:key/11111111-2222-3333-4444-555555555555  
ScheduleExpression = cron(15 3 * * ? *)  

Note :warning:  
-> Don´t forget to create your S3 bucket before deploy stack!  
-> Create lifcycle rule to remove old backups (example remove older backupfiles that 30 days)