# kuma-ingress-watcher

![Version: 1.1.0](https://img.shields.io/badge/Version-1.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.3.0](https://img.shields.io/badge/AppVersion-1.3.0-informational?style=flat-square)

A Helm chart for Kuma ingress watcher. it is a kubernetes controller designed to automatically monitor Traefik Ingress routes and/or kubernetes Ingress object in a Kubernetes cluster and create corresponding monitors in Uptime Kuma.

**Homepage:** <https://github.com/SQuent/helm-kuma-ingress-watcher>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Quentin SALLIO | <q.sallio@gmail.com> |  |

## Source Code

* <https://github.com/SQuent/kuma-ingress-watcher>

## Prerequistes

- Uptime-Kuma instance on kubernetes configured with the creation of at least one user.
- Traefik deployed with IngressRoute crds
- A secret in the same namespace with in the data field:

    ````
    data:
        user: alice
        password: alice
    ````

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| clusterRole.name | string | `"ingress-reader"` |  |
| clusterRoleBinding.name | string | `"kuma-ingress-reader-binding"` |  |
| configMap.name | string | `"controller-scripts"` |  |
| deployment.image.name | string | `"squent/kuma-ingress-watcher"` |  |
| deployment.label | string | `"kuma-ingress-watcher"` |  |
| deployment.logLevel | string | `"INFO"` |  |
| deployment.name | string | `"kuma-ingress-watcher"` |  |
| deployment.replicas | int | `1` |  |
| kumaIngressWatcher.ingress.enabled | bool | `true` |  |
| kumaIngressWatcher.ingressRoute.enabled | bool | `false` |  |
| kumaIngressWatcher.watchInterval | int | `10` |  |
| namespace | string | `"monitoring"` |  |
| resources.limits.cpu | string | `"500m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"250m"` |  |
| resources.requests.memory | string | `"64Mi"` |  |
| secret.name | string | `"kuma-ingress-discovery-token"` |  |
| serviceAccount.name | string | `"kuma-ingress-discovery"` |  |
| uptimeKuma.credentialsSecret | string | `"uptime-kuma-credentials"` |  |
| uptimeKuma.url | string | `"http://uptime-kuma:3001"` |  |

