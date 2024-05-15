+++
title = "How to remove stale github workflows"
author = ["Dmitry Markushevich"]
date = 2024-01-26
lastmod = 2024-01-26T11:54:37-08:00
tags = ["seedling", "github", "devops"]
draft = false
+++

There's a [long standing Github ticket](https://github.com/orgs/community/discussions/26256) for removing stale github workflows. Turns out there's no way to remove a workflow.

The work around here is to remove all **workflow runs** first.

1.  Install github command line tool: `brew install gh`
2.  In the repo's working directory do the following:

<!--listend-->

```shell
gh run list --workflow=stale-workflow.yml --json databaseId | jq '.[].databaseId' | xargs -I{} gh run delete {}
```

Replace `stale-workflow.yml` with the appropriate workflow file name.

Note that this does not handle the case where there are many hundreds of workflow runs.
