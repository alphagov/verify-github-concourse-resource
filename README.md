# verify-github-concourse-resource

>**GOV.UK Verify has closed**
>
>This repository is out of date and has been archived

GitHub resource for Concourse that enforces a minimum number of GitHub approvals. This relies heavily on the [Concourse `git-resource`](https://github.com/concourse/git-resource).

This has been taken from the now archived [GSP repository](https://github.com/alphagov/gsp/tree/master/components/concourse-github-resource) and updated. It's heavily used in Verify and needs maintaining.

## Source configuration

All the required configuration for the Concourse `git-resource` will be required along with:

* `organization` *Required.* The GitHub organization the repo is in.
* `repository` *Required.* The repository name.
* `github_api_token` *Required.* A GitHub API token.
* `approvers`*Required.* A list GitHub usernames of approvers.
* `required_approval_count` *Required.* The minimum number of approvals required to proceed.

## Run tests

Update the value for `github_api_token` in test.json to an actual token. Then run:

```
rm -rf tmp && cat test.json | docker run -v $PWD/tmp:/mnt/myapp -i $(docker build -q .) /opt/resource/in /mnt/myapp
```
