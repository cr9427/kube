help repo update
helm search repo metallb
helm show values metallb/metallb > metallb-values.yaml
helm install metallb metallb/metallb --values metallb-values.yaml -n kube-system
kubectl apply -f address-pool.yaml -n kube-system
kubectl apply -f l2-advertisment.yaml -n kube-system
