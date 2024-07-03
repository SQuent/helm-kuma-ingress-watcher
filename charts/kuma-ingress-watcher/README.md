# kuma-ingress-watcher

![Version: 0.1.1](https://img.shields.io/badge/Version-0.1.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.1.1](https://img.shields.io/badge/AppVersion-1.1.1-informational?style=flat-square)

**for the moment, the controller only manages IngressRoute objects but if people are interested in the project then other objects like ingress could be added**

A Helm chart for Kuma ingress watcher. it is a kubernetes controller designed to automatically monitor Traefik Ingress routes in a Kubernetes cluster and create corresponding monitors in Uptime Kuma.

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
        password: admin
        user: toto
    ````

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| clusterRole.name | string | `"ingress-reader"` |  |
| clusterRoleBinding.name | string | `"kuma-ingress-reader-binding"` |  |
| configMap.name | string | `"controller-scripts"` |  |
| deployment.image.name | string | `"squent/kuma-ingress-watcher"` |  |
| deployment.label | string | `"kuma-ingress-watcher"` |  |
| deployment.name | string | `"kuma-ingress-watcher"` |  |
| deployment.replicas | int | `1` |  |
| namespace | string | `"monitoring"` |  |
| resources.limits.cpu | string | `"500m"` |  |
| resources.limits.memory | string | `"128Mi"` |  |
| resources.requests.cpu | string | `"250m"` |  |
| resources.requests.memory | string | `"64Mi"` |  |
| secret.name | string | `"kuma-ingress-discovery-token"` |  |
| serviceAccount.name | string | `"kuma-ingress-discovery"` |  |
| uptimeKuma.credentialsSecret | string | `"uptime-kuma-credentials"` |  |
| uptimeKuma.url | string | `"http://uptime-kuma:3001"` |  |

