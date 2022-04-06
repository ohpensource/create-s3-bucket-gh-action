# create-s3-bucket-gh-action

Repository containing Ohpen's Github Action to create s3 bucket with Ohpen standard.

<!-- vscode-markdown-toc -->
- [create-s3-bucket-gh-action](#create-s3-bucket-gh-action)
  - [<a name='code-of-conduct'></a>code-of-conduct](#code-of-conduct)
    - [<a name='github-action'></a>github-action](#github-action)

<!-- vscode-markdown-toc-config
	numbering=false
	autoSave=false
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->


## <a name='code-of-conduct'></a>code-of-conduct

Go crazy on the pull requests :) ! The only requirements are:

> - Use [conventional-commits](#check-conventional-commits).
> - Include [jira-tickets](#check-jira-tickets-commits) in your commits.
> - Create/Update the documentation of the use case you are creating, improving or fixing. **[Boy scout](https://biratkirat.medium.com/step-8-the-boy-scout-rule-robert-c-martin-uncle-bob-9ac839778385) rules apply**. That means, for example, if you fix an already existing workflow, please include the necessary documentation to help everybody. The rule of thumb is: _leave the place (just a little bit)better than when you came_.

### <a name='github-action'></a>github-action

This action will create s3 bucket in AWS account.

On backend action is built as shell script implementing [aws cli](https://docs.aws.amazon.com/cli/latest/reference/s3api/index.html) 

example usage:

```yaml
name: CD
on:
  push:
    branches: ["main"]
jobs:
    build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
       - name: create-s3-bucket
        uses: ohpensource/create-s3-bucket-gh-action/action@v0.0.2
        with:
          region: ${{ secrets.AWS_REGION }}
          access-key: ${{ secrets.AWS_ACCESS_KEY_ID }}
          secret-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          account: <aws account id where to create s3 bucket>
          role-name: <name of the role to assume in the destination account>
          s3-bucket: <bucket name>
          

```