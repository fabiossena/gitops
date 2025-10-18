PHP base
========

This base contains:
- `deployment.yaml` - web app Deployment (container name: php-fss-app)
- `service.yaml` - ClusterIP Service
- `php-job.yaml` - a one-off Job example
- `cronjob.yaml` - periodic CronJob example

Usage (overlay example):

```yaml
# overlays/prod/kustomization.yaml
resources:
  - ../../base/php

namespace: fss-app

images:
  - name: php
    newTag: 8.2.1

patches:
  - path: patch-replicas.yaml
    target:
      kind: Deployment
  - path: patch-image.yaml
    target:
      kind: Deployment
```

Replace image tags and replicas in overlays.
