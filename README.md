# Prometheus Operator Example

This repo demonstrates using the Prometheus Operator to deploy and manage Prometheus in Kubernetes. You can find an associated article here: https://www.minibuilds.io/posts/prometheus-kubernetes/.


## Deploy Everything

```bash
LATEST=$(curl -s https://api.github.com/repos/prometheus-operator/prometheus-operator/releases/latest | jq -cr .tag_name)
curl -sL https://github.com/prometheus-operator/prometheus-operator/releases/download/${LATEST}/bundle.yaml | kubectl create -f -

# e.g.
curl -sL https://github.com/prometheus-operator/prometheus-operator/releases/download/v0.69.1/bundle.yaml | kubectl create -f -
```


```bash
kubectl apply -f metrics-app-namespace.yaml
kubectl apply -f metrics-app-deployment.yaml
kubectl apply -f metrics-app-svc.yaml
kubectl apply -f metrics-app-service-monitor.yaml
```

```bash
kubectl apply -f prometheus-cluster-role-binding.yaml
kubectl apply -f prometheus-cluster-role.yaml
kubectl apply -f prometheus.yaml
kubectl apply -f prometheus-svc.yaml
```