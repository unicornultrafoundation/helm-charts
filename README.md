# Helm Charts Repository

Repository containing Helm charts for Subnet Operator and related components.

## 📋 Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
- [Available Charts](#available-charts)
- [Usage](#usage)
- [Development](#development)
- [Contributing](#contributing)
- [License](#license)

## 🚀 Introduction

This repository contains Helm charts maintained by Unicorn Ultra Foundation for deploying and managing Subnet Operator on Kubernetes clusters.

## 📦 Installation

### Add Helm repository

```bash
helm repo add u2u https://unicornultrafoundation.github.io/helm-charts/
helm repo update
```

### Install chart

```bash
helm install subnet-operator-inventory u2u/subnet-operator-inventory
```

## 📚 Available Charts

### subnet-operator-inventory

Helm chart for deploying Subnet Operator Inventory - a Kubernetes operator for managing subnet inventory in the cluster.

**Details:** See [chart README](./charts/subnet-operator-inventory/README.md)

**Install:**
```bash
helm install subnet-operator-inventory u2u/subnet-operator-inventory \
  --namespace subnet-system \
  --create-namespace
```

**Install with custom values:**
```bash
helm install subnet-operator-inventory u2u/subnet-operator-inventory \
  --namespace subnet-system \
  --create-namespace \
  -f my-values.yaml
```

## 🔧 Usage

### List available charts

```bash
helm search repo u2u
```

### Update repository

```bash
helm repo update u2u
```

### Upgrade chart

```bash
helm upgrade subnet-operator-inventory u2u/subnet-operator-inventory \
  --namespace subnet-system
```

### Uninstall

```bash
helm uninstall subnet-operator-inventory --namespace subnet-system
```

## 🛠️ Development

### Requirements

- Kubernetes >= 1.19
- Helm >= 3.0
- [ct (chart-testing)](https://github.com/helm/chart-testing) (for testing)

### Repository Structure

```
helm-charts/
├── charts/                          # Directory containing charts
│   └── subnet-operator-inventory/   # Chart for Subnet Operator Inventory
│       ├── Chart.yaml               # Chart metadata
│       ├── values.yaml              # Default values
│       ├── values.example.yaml      # Example values
│       ├── README.md                # Chart documentation
│       └── templates/               # Helm templates
├── cr.yaml                          # Chart releaser configuration
├── ct.yaml                          # Chart testing configuration
└── README.md                        # This file
```

### Testing Charts

Use `ct` (chart-testing) to test charts:

```bash
# Lint charts
ct lint

# Test charts
ct install

# Validate charts
ct lint-and-install
```

### Package Charts

```bash
# Package chart
helm package charts/subnet-operator-inventory

# Create index
helm repo index .
```

### Release Charts

This repository uses [chart-releaser](https://github.com/helm/chart-releaser) to automatically release charts. Configuration is defined in `cr.yaml`.

## 📝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Guidelines

- Follow [Helm best practices](https://helm.sh/docs/chart_best_practices/)
- Ensure charts pass all tests (`ct lint-and-install`)
- Update chart README.md when adding new features
- Version charts according to [Semantic Versioning](https://semver.org/)

## 🔗 Links

- **Homepage:** https://github.com/unicornultrafoundation/subnet-node
- **Source Code:** https://github.com/unicornultrafoundation/subnet-node
- **Helm Repository:** https://unicornultrafoundation.github.io/helm-charts/

## 📄 License

[Your License]

## 👥 Maintainers

- Subnet Operator Team
