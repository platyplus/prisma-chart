# Prisma Helm Chart

[Prisma](https://prisma.io) is a performant open-source GraphQL ORM-like layer doing the heavy lifting in your GraphQL server.

## TL;DR;

```bash
$ helm install incubator/prisma
```

## Introduction

This chart bootstraps a prisma deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name my-release incubator/prisma
```

By default, this chart includes a PostgreSQL chart as a dependency in the `requirements.yaml` file. However, this can be disabled and Prisma can be configured to use any other supported database.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the Prisma chart and their default values.

| Parameter                     | Description                                  | Default                                                              |
| ----------------------------- | -------------------------------------------- | -------------------------------------------------------------------- |
| `image`                       | `prisma` image repository                    | `prismagraphql/prisma`                                               |
| `imageTag`                    | `prisma` image tag                           | `1.8`                                                                |
| `imagePullPolicy`             | Image pull policy                            | `IfNotPresent`                                                       |
| `database.connector`          | Database connector                           | `postgres`                                                           |
| `database.user`               | Database user                                | `prisma`                                                             |
| `database.password`           | Database user's password                     | `prisma`                                                             |
| `database.host`               | Host for the database endpoint               | `nil`                                                                |
| `database.port`               | Port for the database endpoint               | `nil`                                                                |
| `auth.enabled`                | Use authentication for `prisma`              | `false`                                                              |
| `auth.secret`                 | Secret to use for authentication             | `nil`                                                                |
| `service.type`                | k8s service type exposing ports              | `ClusterIP`                                                          |
| `service.port`                | TCP port                                     | `4466`                                                               |
| `ingress.enabled`             | Enables Ingress                              | `false`                                                              |
| `ingress.annotations`         | Ingress annotations                          | `{}`                                                                 |
| `ingress.path`                | Ingress path                                 | `/`                                                                  |
| `ingress.hosts`               | Ingress accepted hostnames                   | `[]`                                                                 |
| `ingress.tls`                 | Ingress TLS configuration                    | `[]`                                                                 |
| `resources`                   | CPU/Memory resource requests/limits          | `{}`                                                                 |
| `nodeSelector`                | Node labels for pod assignment               | `{}`                                                                 |
| `affinity`                    | Affinity settings for pod assignment         | `{}`                                                                 |
| `tolerations`                 | Toleration labels for pod assignment         | `[]`                                                                 |
| `postgresql.enabled`          | Install PostgreSQL chart                     | `true`                                                               |
| `postgresql.resources`        | PostgreSQL resource requests and limits      | Memory: `256Mi`, CPU: `100m`                                         |
| `postgresql.imagePullPolicy`  | PostgreSQL image pull policy                 | `Always` if `imageTag` is `latest`, else `IfNotPresent`              |
| `postgresql.postgresUser`     | Username of new user to create               | `prisma`                                                             |
| `postgresql.postgresPassword` | Password for the new user                    | `prisma`                                                             |

Additional configuration parameters for the PostgreSQL database deployed with Prisma can be found [here](https://github.com/kubernetes/charts/tree/master/stable/postgresql).

> **Tip**: You can use the default [values.yaml](values.yaml)
