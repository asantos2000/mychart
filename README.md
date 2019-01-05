# mychart

[mychart](https://github.com/kubernetes/ingress-nginx) is an Ingress controller that uses ConfigMap to store the nginx configuration.

## TL;DR;

```bash
# Add repo
helm repo add asantos2000 https://asantos2000.github.io/helm-charts

# Update
helm repo update

# Install
helm install asantos2000/mychart
```

## Introduction

This chart bootstraps an nginx deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites
  - Kubernetes 1.6+

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
helm install --name my-release asantos2000/mychart
```

The command deploys nginx on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the nginx-ingress chart and their default values.

Parameter | Description | Default
--- | --- | ---
`replicaCount` | Number of replicas for deployment | `1`
`image.repository` | nginx image repository | `nginx`
`image.tag` | nginx image tag | `stable`
`image.pullPolicy` | nginx container image pull policy | `IfNotPresent`
`nameOverride` | name | none
`fullnameOverride` | Fullname | none
`ingress.enabled` | Deploy ingress if true | `false`
`ingress.annotations` | annotations for ingress | `{}`
`ingress.paths` | Ingress paths | `[]`
`ingress.hosts` | Ingress hosts | `- chart-example.local`
`ingress.tls` | Ingress tls | `[]`
`ingress.annotations` | annotations for ingress | `{}`
`service.port` | Sets the targetPort | `80`
`service.type` | type of controller service to create | `ClusterIP`
`resources` | set limits and requests for cpu and memeory | `{}`
`nodeSelector` | nodeSelector for deployment | `{}`
`tolerations` | tolerations for deployment | `[]`
`affinity` | affinity for deployment | `{}`


```bash
helm install asantos2000/mychart --name my-release \
    --set stats.enabled=true
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
helm install asantos2000/mychart --name my-release -f values.yaml
```

A useful trick to debug issues with ingress is to increase the logLevel
as described [here](https://github.com/kubernetes/ingress-nginx/blob/master/docs/troubleshooting.md#debug)

```bash
helm install asantos2000/mychart --set extraArgs.v=2
```
> **Tip**: You can use the default [values.yaml](values.yaml)