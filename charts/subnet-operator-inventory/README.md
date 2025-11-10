# Subnet Operator Inventory Helm Chart

Helm chart for deploying Subnet Operator Inventory on Kubernetes cluster.

## Description

This chart deploys Subnet Operator Inventory - a Kubernetes operator for managing subnet inventory in the cluster.

## Installation

### Install with default values

```bash
helm install subnet-operator-inventory ./subnet-operator-inventory
```

### Install with custom values

```bash
helm install subnet-operator-inventory ./subnet-operator-inventory -f my-values.yaml
```

### Install to a specific namespace

```bash
helm install subnet-operator-inventory ./subnet-operator-inventory --namespace subnet-system --create-namespace
```

## Configuration

Main configuration parameters in `values.yaml`:

### Image

```yaml
image:
  repository: subnet-operator-inventory
  pullPolicy: IfNotPresent
  tag: "latest"
```

### Replica Count

```yaml
replicaCount: 1
```

### Service Account

```yaml
serviceAccount:
  create: true
  name: ""
```

### RBAC

Subnet Operator is granted cluster-wide management permissions (ClusterRole) with full access:

- **Core resources**: nodes, namespaces, pods, services, configmaps, secrets, persistentvolumes, etc.
- **Apps resources**: deployments, statefulsets, daemonsets, replicasets
- **Networking**: networkpolicies, ingresses, endpoints
- **Storage**: storageclasses, volumeattachments
- **Custom Resources**: CRDs and all custom resources
- **Policy**: poddisruptionbudgets
- **Coordination**: leases (for leader election)

```yaml
rbac:
  create: true
  rules: []  # Additional custom rules can be added if needed
```

**Note**: The operator uses ClusterRole and ClusterRoleBinding to manage the entire cluster, not just within a single namespace.

### Operator Configuration

```yaml
operator:
  watchNamespace: ""  # Empty means all namespaces
  syncPeriod: 60
  maxConcurrentReconciles: 1
```

### Leader Election

```yaml
leaderElection:
  enabled: true
  resourceName: subnet-operator-inventory-leader-election
```

### Metrics

```yaml
metrics:
  enabled: true
  serviceMonitor:
    enabled: false
```

### Autoscaling

```yaml
autoscaling:
  enabled: false
  minReplicas: 1
  maxReplicas: 100
  targetCPUUtilizationPercentage: 80
```

### Configuration

The operator uses a configuration file mounted as a ConfigMap. The default configuration:

```yaml
config:
  version: v1
  cluster_storage:
    - default
  exclude:
    nodes: []
    node_storage: []
  configPath: /etc/subnet-operator-inventory/config.yaml
```

- `version`: Configuration version
- `cluster_storage`: List of cluster storage names to manage
- `exclude.nodes`: List of node names to exclude from management
- `exclude.node_storage`: List of node storage names to exclude
- `configPath`: Path where the config file is mounted in the container

## Uninstall

```bash
helm uninstall subnet-operator-inventory
```

## Upgrade

```bash
helm upgrade subnet-operator-inventory ./subnet-operator-inventory
```

## Status Check

```bash
# Check pods
kubectl get pods -l app.kubernetes.io/name=subnet-operator-inventory

# View logs
kubectl logs -l app.kubernetes.io/name=subnet-operator-inventory --tail=-1

# Check service
kubectl get svc -l app.kubernetes.io/name=subnet-operator-inventory
```

## Requirements

- Kubernetes >= 1.19
- Helm >= 3.0

## License

[Your License]
