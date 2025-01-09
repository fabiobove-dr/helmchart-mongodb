# 🍃🛞 Helm Chart for MongoDB and MongoExpress

This repository contains a Helm chart for deploying **MongoDB** and **MongoExpress** on Kubernetes. MongoDB is a widely used NoSQL database, and MongoExpress is a web-based administrative interface for MongoDB.

---

## Features

- Deploys MongoDB as a StatefulSet for persistent storage.
- Includes MongoExpress for web-based database management.
- Highly configurable through `values.yaml`.
- Secure and production-ready configurations.

## Prerequisites

- Kubernetes cluster (v1.18 or higher).
- Helm (v3 or higher).
- Persistent volume provisioner support in the Kubernetes cluster.

## Installation

1. Install the chart:
   ```bash
   helm install my-mongodb ./helmchart-mongodb
   ```
   Replace `my-mongodb` with your desired release name.

2. Verify the installation:
   ```bash
   kubectl get pods
   ```

## Configuration

The chart can be customized using the `values.yaml` file. Below are some key configuration options:

### MongoDB Configuration

- **`mongodb.replicas`**: Number of MongoDB replicas.
- **`mongodb.storage.size`**: Size of the persistent volume.
- **`mongodb.auth.username`**: Admin username.
- **`mongodb.auth.password`**: Admin password.

### MongoExpress Configuration

- **`mongoExpress.enabled`**: Enable or disable MongoExpress.
- **`mongoExpress.env`**: Environment variables for MongoExpress.

### Example `values.yaml`

```yaml
mongodb:
  replicas: 3
  storage:
    size: 10Gi
  auth:
    username: admin
    password: secret

mongoExpress:
  enabled: true
  env:
    ME_CONFIG_MONGODB_ADMINUSERNAME: admin
    ME_CONFIG_MONGODB_ADMINPASSWORD: secret
```

## Directory Structure

```plaintext
helmchart-mongodb/
|-- .helmignore             # Files to ignore during packaging
|-- Chart.yaml              # Chart metadata
|-- LICENSE                 # License information
|-- README.md               # Documentation
|-- values.yaml             # Default configuration values
|-- templates/              # Helm templates
    |-- deployment.yaml     # Deployment configuration
    |-- service.yaml        # Service configuration
    |-- ...                 # Additional templates
```

## Accessing MongoExpress

1. Check the service information:
   ```bash
   kubectl get svc my-mongodb-mongoexpress
   ```

2. Access MongoExpress using the external IP or NodePort.

## Uninstallation

To uninstall the chart and release:
```bash
helm uninstall my-mongodb
```

## License

This project is licensed under the terms of the MIT license. See the `LICENSE` file for details.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.