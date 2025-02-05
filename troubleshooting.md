Few handy commands - 
1. `helm install firebase ~/work/firebase-chart --debug` - to install the helm chart on your local kube cluster
2. `helm uninstall `helm ls -q`` - this uninstall everything running on the kube cluster (USE WITH CAUTION)
3. `kubectl get pods` - to see what pods are runnning
4. `kubectl describe pod firebase` - to see the deployment config and other pod related helm values