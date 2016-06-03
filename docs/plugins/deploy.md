# Deploy

```
serverless deploy --stage dev --region us-east-1
```

Deploys your service to AWS.

## Options
- `--stage` The stage in your service that you want to deploy to. **Required**.
- `--region` The region in that stage that you want to deploy to. **Required**.

## Packaging
Note that you can define which files / folders should be excluded or included into your deployment with the help of
the `include` and `exclude` arrays in your `serverless.yaml` file.

Those two arrays are considered before we package your code for deployment.

At first the `exclude` array is checked. After that the files and folders inside the `include` array will be added. This
enables you a way to force inclusion of files and folder even if they are previously excluded.

The default files / folder which are exlucded are the following:
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
