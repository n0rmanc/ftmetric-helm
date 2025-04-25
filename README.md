# ftmetric-helm

A Helm chart for deploying ftmetric, which is part of the [fthelper](https://github.com/kamontat/fthelper) project's metric component. This chart packages the metric service that helps with Freqtrade trading bot monitoring and metrics collection.

## Overview

This Helm chart deploys the metric component from fthelper, which is a collection of Freqtrade helpers including scripts, servers, and docker images. The metric service is specifically designed to help monitor and collect metrics from your Freqtrade trading bot.

Original project: [kamontat/fthelper](https://github.com/kamontat/fthelper)

## Installation

### Add Helm Repository

```bash
helm repo add ftmetric-helm https://n0rmanc.github.io/ftmetric-helm
helm repo update
```

### Install Chart

```bash
helm install my-release ftmetric-helm/ftmetric
```

## Configuration

The following table lists the configurable parameters of the chart and their default values:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Container image repository | `ftmetric` |
| `image.tag` | Container image tag | `latest` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |


### Example values.yaml

```yaml

env:
  FTH_INTERNAL__LOG__LEVEL: "3"
  FTH_CLUSTERS: "1A,2A"
  FTH_SERVER__PORT: "8090"
  
  # Cluster 1A Configuration
  FTC_1A__FREQTRADE__HTTP__ENABLED: "true"
  FTC_1A__FREQTRADE__HTTP__URL: "http://freqtrade:8080"
  FTC_1A__FREQTRADE__HTTP__USERNAME: "freqtrade"
  FTC_1A__FREQTRADE__HTTP__PASSWORD: "password"
  FTC_1A__FREQTRADE__DB__ENABLED: "false"
  FTC_1A__FREQTRADE__DB__TYPE: "postgres"
  FTC_1A__FREQTRADE__DB__URL: "localhost:5432"
  FTC_1A__FREQTRADE__DB__NAME: "freqtrade"
  FTC_1A__FREQTRADE__DB__USERNAME: "freqtrade"
  FTC_1A__FREQTRADE__DB__PASSWORD: "password"

  # Cluster 2A Configuration
  FTC_2A__FREQTRADE__HTTP__ENABLED: "true"
  FTC_2A__FREQTRADE__HTTP__URL: "http://localhost:8081"
  FTC_2A__FREQTRADE__HTTP__USERNAME: "freqtrade"
  FTC_2A__FREQTRADE__HTTP__PASSWORD: "password"
  FTC_2A__FREQTRADE__DB__ENABLED: "false"

To use this configuration:

```bash
helm install my-release ftmetric-helm/ftmetric -f values.yaml
```

## Custom Configuration

To customize the configuration, you can create a values.yaml file:

```bash
helm install my-release ftmetric-helm/ftmetric -f values.yaml
```

## Upgrade and Uninstallation

### Upgrade

```bash
helm upgrade my-release ftmetric-helm/ftmetric
```

### Uninstall

```bash
helm uninstall my-release
```

## Development

### Local Testing

```bash
helm install my-release . --dry-run --debug
```

## Contributing

Pull requests and issues are welcome.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
