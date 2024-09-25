# Helm Chart for Hassio Xfinity Usage

Fetch Xfinity data usage and serve it via an HTTP endpoint, publish it to MQTT
or post it to an URL.

To learn more, visit <https://github.com/thor0215/hassio-xfinity-usage/>.

## Prerequisites

- Kubernetes 1.10+

## Installing the Chart

```console
helm repo add naterator https://naterator.github.io/helm-charts/
helm repo update
helm install \
  --set config.xfinity.username=USERNAME_HERE \
  --set config.xfinity.password=PASSWORD_HERE \
  hassio-xfinity-usage naterator/hassio-xfinity-usage
```

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `hassio-xfinity-usage` release:

```console
helm uninstall hassio-xfinity-usage
```

The command removes all the Kubernetes components associated with the chart and
deletes the release.

## Configuration parameters

The following table lists the configurable parameters of the Hassio Xfinity Usage
chart and their default values.

| Parameter                          | Description                                                                                                 | Default                                  |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------- | ---------------------------------------- |
| `config.xfinity.username`          | Username for Xfinity.                                                                                       | `""`                                     |
| `config.xfinity.password`          | Password for Xfinity.                                                                                       | `""`                                     |
| `replicaCount`                     | Number of pod replicas. Only one replica is currently supported.                                            | `1`                                      |
| `image.repository`                 | Repository of the container image.                                                                          | `ghcr.io/thor0215/hassio-xfinity-usage-amd64`   |
| `image.tag`                        | Tag of the container image.                                                                                 | `latest`                                 |
| `image.pullPolicy`                 | Container image pull policy.                                                                                | `Always`                                 |
| `image.imagePullSecrets`           | Name of image pull secrets to be used by kubernetes.                                                        | `[]`                                     |
| `nameOverride`                     | Overrides the name of the chart.                                                                            | `""`                                     |
| `fullnameOverride`                 | Overrides the full name of the chart.                                                                       | `""`                                     |
| `service.type`                     | Service type.                                                                                               | `NodePort`                               |
| `service.port`                     | Incoming port to access Hassio Xfinity Usage.                                                                 | `7878`                                   |
| `ingress.enabled`                  | Enable ingress.                                                                                             | `true`                                   |
| `ingress.className`                | Ingress className.                                                                                          | `""`                                     |
| `ingress.annotations`              | Ingress annotations.                                                                                        | `{}`                                     |
| `ingress.hosts`                    | Ingress hosts.                                                                                              | `[]`                                     |
| `ingress.tls`                      | Ingress TLS configuration.                                                                                  | `[]`                                     |
| `resources`                        | CPU/memory resource requests/limits.                                                                        | `{}`                                     |
| `nodeSelector`                     | Node labels for pod assignment.                                                                             | `{}`                                     |
| `tolerations`                      | Toleration labels for pod assignment.                                                                       | `[]`                                     |
| `affinity`                         | Affinity settings for pod assignment.                                                                       | `{}`                                     |
| `podSecurityContext`               | Set SecurityContext on the pod level.                                                                       | `{}`                                     |
| `podAnnotations`                   | Set annotations on the pod level.                                                                           | `{}`                                     |
| `podLabels`                        | Set labels on the pod level.                                                                                | `{}`                                     |
| `securityContext`                  | Set the securityContext for the pod.                                                                        | `{}`                                     |
| `volumes`                          | Additional volumes available to containers.                                                                 | `[]`                                     |
| `volumeMounts`                     | Additional mount points of volumes in a container.                                                          | `[]`                                     |

Specify each parameter using the `--set key=value` argument to `helm install`.
For example,

```console
helm repo add naterator https://naterator.github.io/helm-charts/
helm repo update
helm install \
  --set config.xfinity.username=USERNAME_HERE \
  --set config.xfinity.password=PASSWORD_HERE \
  hassio-xfinity-usage naterator/hassio-xfinity-usage
```

Alternatively, a YAML file that specifies the values for the parameters can be
provided while installing the chart. For example,

```console
helm install -f values.yaml hassio-xfinity-usage naterator/hassio-xfinity-usage
```

> **Tip**: You can use the default [values.yaml](values.yaml)
