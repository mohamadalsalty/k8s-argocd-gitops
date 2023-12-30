# ArgoCD Commands

This document provides a quick reference to the essential commands used for managing ArgoCD, a declarative, GitOps continuous delivery tool for Kubernetes.

### Creating Namespace for ArgoCD

```
kubectl create namespace argocd
```

### Installing ArgoCD

```
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### Viewing ArgoCD Deployments

```
kubectl get deploy -n argocd
```

### Checking ArgoCD Services

```
kubectl get svc -n argocd
```

### Port Forwarding for ArgoCD Server

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

### Retrieving Initial Admin Secret for ArgoCD

```
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{'{.data.password}'}" | base64 -d
```

### Logging into ArgoCD

```
argocd login localhost:8080
```

### Checking Current Kubernetes Context

```
kubectl config current-context
```

### Adding a Cluster to ArgoCD

```
argocd cluster add minikube
```

### Listing Clusters in ArgoCD

```
argocd cluster list
```

### Creating an Application in ArgoCD

```
argocd app create argocd-example --repo https://github.com/mohamadalsalty/k8s.git --path nodejs --dest-server https://192.168.49.2:8443
```

### Listing Applications in ArgoCD

```
argocd app list
```

### Getting Details of an Application in ArgoCD

```
argocd app get argocd/argocd-example
```

### Synchronizing an Application in ArgoCD

```
argocd app sync argocd/argocd-example
```

### Viewing Pods in a Specific Namespace

```
kubectl get pods -n dev
```

---

**Note:** Always ensure your kubectl and argocd CLI are correctly configured and authenticated before executing these commands.
