# Helm Charts Repository

Repository containing Helm charts for Unicorn Ultra Foundation applications and services.

## Adding the Repository

To add this repository to your Helm, run the following command:

```bash
helm repo add unicornultra https://unicornultrafoundation.github.io/helm-charts
helm repo update
```

## Installing a Chart

After adding the repository, you can install charts using the following command:

```bash
helm install <release-name> unicornultra/<chart-name>
```

## Available Charts

### subnet-operator-inventory

Chart for managing Subnet Operator Inventory.

**Version:** 0.1.0

**Install:**

```bash
helm install subnet-operator-inventory unicornultra/subnet-operator-inventory
```

**Install with custom values:**

```bash
helm install subnet-operator-inventory unicornultra/subnet-operator-inventory -f values.yaml
```

**Upgrade:**

```bash
helm upgrade subnet-operator-inventory unicornultra/subnet-operator-inventory
```

**Uninstall:**

```bash
helm uninstall subnet-operator-inventory
```

## Repository Structure

```
helm-charts/
├── index.yaml          # Helm repository index file
├── README.md           # This file
└── subnet/             # Directory containing charts
    └── subnet-operator-inventory/
```

## Contact and Support

- Repository: https://github.com/unicornultrafoundation/helm-charts
- Issues: https://github.com/unicornultrafoundation/helm-charts/issues

## License

See the LICENSE file in the repository for more details about the license.

