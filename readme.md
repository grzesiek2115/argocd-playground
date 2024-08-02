## Bootstrapping k8s cluster

- `kind create cluster --config ./kind_cluster.yaml`\
    This command will create create kind cluster on local machine.\
    https://kind.sigs.k8s.io/docs/user/quick-start/

## Bootstrapping argocd on k8s cluster

- Take from https://github.com/argoproj/argoproj-deployments/blob/master/argocd/kustomization.yaml, the kustomization.yaml and resources/namespace.yaml
- `kustomize build . | kubectl apply -f -` run it in kustomization.yaml dir
- `k get po -n argocd`
- To port-forward argocd to local browser, use this command `k port-forward svc/argocd-server -n argocd 8085:80`
- To decode admin password for argocd UI, use `k get secret -n argocd argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d`
