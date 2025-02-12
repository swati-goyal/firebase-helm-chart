
# Firebase Helm Chart

This repository contains a Helm chart for deploying Firebase services on a Kubernetes cluster. It provides a simplified approach to manage Firebase integration within your Kubernetes ecosystem. 

Overview: [Medium Blog Post](https://swati-goyal.medium.com/creating-my-first-helm-chart-for-firebase-a0e5b8869412)


## Prerequisites

Before setting up the Firebase Helm Chart, make sure you have the following tools installed:

- **Kubernetes**: 1.21.x or higher
- **Helm**: 3.x or higher
- **kubectl**: 1.21.x or higher
- **Firebase Project**: You should have a Firebase project set up with the necessary credentials (service account key) to integrate Firebase services.

## Getting Started

### 1. Clone the Repository

Start by cloning this repository to your local machine:

```
git clone https://github.com/swati-goyal/firebase-helm-chart.git
cd firebase-helm-chart
```

### 2. Add Helm Repositories
Before installing the chart, ensure you have added the necessary Helm repositories:
```
helm repo add firebase-repo https://firebase.github.io/helm-charts
helm repo update
```

### Create Firebase Secrets
Create a Kubernetes Secret with your Firebase credentials (service account key):
```
kubectl create secret generic firebase-secret --from-file=serviceAccountKey.json=<path_to_your_service_account_key.json> -n <your_namespace>
```

### 4. Install the Chart
To install the Firebase Helm chart with your specific configurations, use the following command:
```
helm install firebase firebase-repo/firebase-helm-chart -n <your_namespace> --set firebase.credentialsSecret=firebase-secret
```

### 5. Upgrade the Chart
To upgrade your Firebase deployment, run the following:
```
helm upgrade firebase firebase-repo/firebase-helm-chart -n <your_namespace> --set firebase.credentialsSecret=firebase-secret
```

### 6. Verify the Installation
You can verify if the Firebase services are successfully deployed using:
```
kubectl get all -n <your_namespace>
```

## Configuration
You can customize the deployment by modifying the values.yaml file. Here are some key configurable parameters:

- firebase.credentialsSecret: The name of the Kubernetes secret containing your Firebase service account key.
- firebase.projectId: The Firebase project ID for integration.
- firebase.databaseUrl: The Firebase Realtime Database URL (if required).

To override any values, you can use the `--set` flag during the Helm install/upgrade commands.

Example Custom Configuration:
```
helm install firebase firebase-repo/firebase-helm-chart -n <your_namespace> \
  --set firebase.credentialsSecret=firebase-secret \
  --set firebase.projectId="your-firebase-project-id" \
  --set firebase.databaseUrl="https://your-firebase-db-url"
```

## Kubernetes and Helm Versions
- Kubernetes: This chart is compatible with Kubernetes version 1.21.x or higher.
- Helm: Helm 3.x or higher is required to install and manage the chart.
- Ensure your Helm and Kubernetes versions are compatible by checking:
```
kubectl version --client
helm version
```

## Uninstall the Chart
To uninstall the Firebase Helm chart, run:
```helm uninstall firebase -n <your_namespace>```

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Support
For any issues or questions, please open an issue on this repository.

Thanks for using the Firebase Helm Chart!
```
Feel free to adjust any specific values or services as needed for your environment!
```
