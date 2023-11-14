+++
title = "Stern"
author = ["Dmitry Markushevich"]
date = 2023-11-13T00:00:00-08:00
lastmod = 2023-11-13T17:05:45-08:00
tags = ["seedling", "devops", "k8s"]
draft = false
+++

stern is a log tailer for k8s. Similar to `tail -f` but for multipe Kubernetes pods:

```bash
stern --only-log-lines --max-log-requests 1000 --namespace k8s-namesapce 'podw-wildcard*'
```
