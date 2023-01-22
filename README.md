# vke-fch
Vultr Kubernetes Engine (VKE) https://www.vultr.com/docs/vultr-kubernetes-engine/

## bootstrap
```
helm repo add argo https://argoproj.github.io/argo-helm

cd ./argocd/argocd/
helm dependency build
cd ../../argocd/argocd-apps/
helm dependency build
cd ../..

helm install argocd ./argocd/argocd --namespace argocd --create-namespace
helm install argocd-apps ./argocd/argocd-apps --namespace argocd
```

## Argo-cd
* url : https://argo-cd.bluenc.ovh/
* user : admin
* password :

    ```
    kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d && echo
    ```

## Sealed secrets
Exemple :
```
kubectl create secret generic mysecret --dry-run=client  -o yaml --from-literal=password=azerty123 > mysecret.yaml
kubeseal -f mysecret.yaml --format yaml > mysealedsecret.yaml
```