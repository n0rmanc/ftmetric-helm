# ftmetric-helm

A Helm chart for deploying ftmetric.

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
