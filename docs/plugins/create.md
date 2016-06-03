# Create

```
serverless create --name serviceName --stage dev --region us-east-1
```

Creates a new service in the current working directory.

## Options
- `--name` The name of your new service. **Required**.
- `--stage` The name of your first stage in service. **Required**.
- `--region` The name of your first region in stage. **Required**.

## Examples

```
serverless create --name serviceName --stage dev --region us-east-1
```

This example will create a new service called `serviceName` and generate boilerplate in the current working directory. Your new service will have a new stage called `dev` and a region inside that stage called `us-east-1`.

## How It Works
The create plugin generates basic scaffolding for a new "hello world" service to kick start your new microservice. It generates a new folder in the current working directory with the service name you chose. It'll also generate 4 basic files for your new service:

- **serverless.yaml**: The main configuration file for your service. It basically includes the name of your service and a basic `hello` function configuration that is ready to be deployed right away.
- **serverless.env.yaml**: The configuration file for handling stages, regions and serverless variables. This file is meant to hold sensitive information, so it's .gitignored by default. This generated file just includes the stage and region you provided.
- **handlers.js**: A basic handlers file that contains your first `hello` function handler. You can add more function handlers inside that file file and reference them in `serverless.yaml`.
- **package.json**: A basic `package.json` for your new service to handle dependencies.
