# Create a deployment

"Oction" is a GitHub Action that implements a single call with 
[@octokit/request](https://www.npmjs.com/package/@octokit/request)
allowing easy interaction with GitHub REST APIs from your workflow.

Original documentation: https://developer.github.com/v3/repos/deployments/#create-a-deployment

This action implements `POST` request to `/repos/{owner}/{repo}/deployments`


# Quick start

```yaml
- uses: maxkomarychev/oction-create-deployment@v0.7.1
  id: my_step_id
  with:
    token: <token value>
    ref: <ref value>
- name: Print outputs
  run: |
    echo ${{ steps.my_step_id.outputs.id }}
    echo ${{ steps.my_step_id.outputs.number }}
```


# Inputs

| Name | Is required | Description |
|---|---|---|
|token|true|Token to authenticate the request
|owner|false|owner parameter
|repo|false|repo parameter
|ref|true|The ref to deploy. This can be a branch, tag, or SHA.
|task|false|Specifies a task to execute (e.g., `deploy` or `deploy:migrations`).
|auto_merge|false|Attempts to automatically merge the default branch into the requested ref, if it's behind the default branch.
|required_contexts|false|The [status](https://developer.github.com/v3/repos/statuses/) contexts to verify against commit status checks. If you omit this parameter, GitHub verifies all unique contexts before creating a deployment. To bypass checking entirely, pass `<<EMPTY>>`. To provide a list of contexts, use a comma-separated string (eg. `success,pending`). Defaults to all unique contexts.
|payload|false|JSON payload with extra information about the deployment.
|environment|false|Name for the target deployment environment (e.g., `production`, `staging`, `qa`).
|description|false|Short description of the deployment.
|transient_environment|false|Specifies if the given environment is specific to the deployment and will no longer exist at some point in the future. Default: `false`   **Note:** This parameter requires you to use the [`application/vnd.github.ant-man-preview+json`](https://developer.github.com/v3/previews/#enhanced-deployments) custom media type. **Note:** This parameter requires you to use the [`application/vnd.github.ant-man-preview+json`](https://developer.github.com/v3/previews/#enhanced-deployments) custom media type.
|production_environment|false|Specifies if the given environment is one that end-users directly interact with. Default: `true` when `environment` is `production` and `false` otherwise.   **Note:** This parameter requires you to use the [`application/vnd.github.ant-man-preview+json`](https://developer.github.com/v3/previews/#enhanced-deployments) custom media type.

# Outputs

| Name | Description |
|---|---|
|id|`id` field of the response (if exists)|
|number|`number` field of the response (if exists)|

# Friendly octions

* [oction-create-deployment-status](https://github.com/maxkomarychev/oction-create-deployment-status)
* [oction-create-deployment](https://github.com/maxkomarychev/oction-create-deployment)
* [oction-create-issue](https://github.com/maxkomarychev/oction-create-issue)
* [oction-create-release](https://github.com/maxkomarychev/oction-create-release)
* [oction-lock-issue](https://github.com/maxkomarychev/oction-lock-issue)
* [oction-merge-pull-request](https://github.com/maxkomarychev/oction-merge-pull-request)
* [oction-unlock-issue](https://github.com/maxkomarychev/oction-unlock-issue)
