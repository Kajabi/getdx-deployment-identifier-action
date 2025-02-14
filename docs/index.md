# 📖 GitHub Action for Identifying Deployments to send to GetDX

This GitHub Action is used to inform GetDX of deployments for a repo/service.

> Based on this help article: https://help.getdx.com/en/articles/7669458-deployments#h_fac2513522).

## Versions

- [`main`](https://github.com/Kajabi/getdx-deployment-identifier-action)

## Features

This Action sends a `deployments.create` API call to [GetDX](https://getdx.com/) and informs them when a deployment has been made for a specific repo/service

## Usage

```yaml
name: Deployment
on:
  push:
    branches:
      - "main"

jobs:
  deploy:
    steps:
      # All your deployment process steps, followed by: 
      - name: Report production deployment to GetDX
        uses: Kajabi/getdx-deployment-identifier-action@main
        with:
          getdx-instance-name: 'YOUR_INSTANCE_NAME'
          getdx-token: 'YOUR_TOKEN' # Utilize Github Secrets for security
          service-name: 'your-service' # optional
          default-branch: 'main' # optional
```

## Configuration

| Name                    | Description                                                                        | Required | Default                                  |
| ----------------------- | ---------------------------------------------------------------------------------- | -------- | ---------------------------------------- |
| `getdx-instance-name`   | Instance name for getdx (e.g. {instance-name}.getdx.net)                           | `true`   |                                          |
| `getx-token`            | Token for GetDX API Calls (use Github Secrets for security)                        | `true`   |                                          |
| `service-name`          | The service in GetDX that this deployment is for                                   | `false`  |                                          |
| `default-branch`        | The default branch for the repository                                              | `false`  | `main`                                   |
| `debug`                 | Enable debug mode and don't send API requests                                      | `false`  | `false`                                  |