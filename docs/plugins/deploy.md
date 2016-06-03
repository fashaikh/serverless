# Deploy

```
serverless deploy --stage dev --region us-east-1
```

Deploys your service to AWS.

## Options
- `--stage` The stage in your service that you want to deploy to. **Required**.
- `--region` The region in that stage that you want to deploy to. **Required**.

## Packaging
You can define which files / folders should be excluded or included into your deployment with the help of
the `include` and `exclude` arrays in your `serverless.yaml` file. Those two arrays are considered before we package your code for deployment.

At first the `exclude` array is checked. After that the files and folders inside the `include` array will be added. This
enables you a way to force inclusion of files and folder even if they are previously excluded.

The default files / folder which are excluded are the following:
- `serverless.yaml`
- `serverless.env.yaml`
- `.git`
- `.gitignore`
- `.DS_Store`

## Examples

```
serverless deploy --stage dev --region us-east-1
```

This example will deploy your service to the `us-east-1` region in the `dev` stage. Will throw an error if this stage/region pair does not exist.

## How It Works
When you run the `serverless deploy` command, a new CloudFormation stack with core IAM and Bucket resources is created. This process takes around 1-2mins. After the core stack is created, an `iamRoleArnLambda` variable is added to the region vars in `serverless.env.yaml`. This step happens only in the first time you deploy.

We then go through all the functions defined in your `serverless.yaml` file and start packaging the functions based on the `handler` property and the include/exclude filters. We then push all those zipped function packages to the S3 bucket that was created with the stack.

After that we add those lambda function config to the stack template and pointing to those zip files in the bucket. We'll also merge that new stack template with any resources you have defined in `serverless.yaml` (the `resources.aws` property). Finally we just update the stack with all those new resources (including functions).
