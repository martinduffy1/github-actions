# Manual GitHub Actions for Pull Requests

GitHub Actions jobs can have different triggers as documented [on this page](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)

The following workflow triggers will associate a GitHub Actions job to a Pull Request, affecting the status and listing the job under the Checks tab for that PR.
- `pull_request`
- `pull_request_review`
- `pull_request_review_comment`
- `pull_request_target`
- `push`

The `pull_request` trigger has several sub-types that we can take advantage of. Note that `pull_request_review` and `pull_request_review_comment` only trigger when a comment is left on a file diff.

This repository contains two sample GitHub Actions jobs. One job (`automatic-ci`) runs whenever a Pull Request is opened, re-opened, or updated. The other job (`manual-ci`) requires manual intervention. It will be created and run when the label `run-test` is added to a Pull Request. Note that this job will be created whenever any label is added to a PR, but will be skipped unless the label name is `run-test`. Once the job is created, it can be manually rerun from the Checks tab if necesssary.
