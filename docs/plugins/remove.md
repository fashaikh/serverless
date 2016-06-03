# Remove

```
serverless remove --stage dev --region us-east-1
```

Removes the deployed service which is defined in your current working directory according to the stage and region.

## Options
- `--stage` The name of the stage in service. **Required**.
- `--region` The name of the region in stage. **Required**.

## Examples

```
serverless remove --stage dev --region us-east-1
```

This example will remove the deployed service of your current working directory with the stage `dev` and the region `us-east-1`.

## How It Works
When you run the `serverless remove` command for a specified stage/reigon. We first list all the files inside the S3 bucket (which are mainly deployed function zips) and delete them all to empty the bucket. We then delete the entire deployed CloudFormation stack which will delete all the resources, functions and events you deployed for your service, including the S3 bucket. This will completely clear anything related to this service from your AWS account.