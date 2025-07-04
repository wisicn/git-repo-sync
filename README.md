# Git Repo Sync

Git Repo Sync enables you to synchronize code to other code management platforms, such as GitLab, Gitee, etc.
This repository is forked from [wangchucheng/git-repo-sync](https://github.com/wangchucheng/git-repo-sync) .

## Try Git Repo Sync

You can use the following example as a template to create a new file with any name under `.github/workflows/`.

If any of your target URL, username and token is private, just setup the secert in your project settings.

```yaml
name: <action-name>

on: 
  push:
      branches:
        - master
  delete:

jobs:
  sync:
    runs-on: ubuntu-latest
    name: Git Repo Sync
    steps:
    - uses: actions/checkout@v4
      with:
        fetch-depth: 0
    - uses: wangchucheng/git-repo-sync@v0.1.0
      with:
        # Such as https://github.com/wangchucheng/git-repo-sync.git
        target-url: ${{ secrets.GITLAB_URL }}
        # Such as wangchucheng
        target-username: ${{ secrets.GITLAB_USERNAME }}
        # You can store token in your project's 'Setting > Secrets' and reference the name here. Such as ${{ secrets.GITLAB_ACCESS_TOKEN }}
        target-token: ${{ secrets.GITLAB_ACCESS_TOKEN }}
```
