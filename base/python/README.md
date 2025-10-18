Python base
===========

This base contains:
- `deployment.yaml` - web app Deployment (container name: python-fss-app)
- `service.yaml` - ClusterIP Service
- `python-job.yaml` - a one-off Job example
- `cronjob.yaml` - periodic CronJob example

Usage (overlay example):

```yaml
# overlays/staging/kustomization.yaml
resources:
  - ../../base/python

namespace: fss-app

images:
  - name: python
    newTag: 3.11.2

patches:
  - path: patch-replicas.yaml
    target:
      kind: Deployment
  - path: patch-image.yaml
    target:
      kind: Deployment
```

Replace image tags and replicas in overlays.
