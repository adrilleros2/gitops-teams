# my-team-manifests

Private repo. Only our team has access.

## Convention

> `values-<env>.yaml` exists → app is deployed to that env.
> No file → not deployed. It's that simple.

## Apps

| App | Namespace | stage | production |
|-----|-----------|-------|------------|
| hello-world | my-team-frontend | ✅ | ✅ |
| worker-service | my-team-workers | ✅ | ❌ |
| admin-dashboard | my-team-admin | ❌ | ✅ |

## Add a new app

1. `mkdir -p charts/my-new-app/templates`
2. Create `Chart.yaml`, `values.yaml`, templates
3. Create `values-stage.yaml` with `targetNamespace: my-team-something`
4. `git push` → ArgoCD auto-discovers and deploys

## Deploy an existing app to another env

1. Create `values-production.yaml` with `targetNamespace: ...`
2. `git push` → deployed

## Remove an app from an env

1. Delete `values-<env>.yaml`
2. `git push` → Application is pruned
