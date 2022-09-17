helm repo add https://jupyterhub.github.io/helm-chart/
helm repo update
helm search repo pebble
helm show values jupyterhub/pebble > pebble-values-orig.yaml
helm install pebble jupyterhub/pebble --values ~/work/kube/pebble/pebble-values.yaml -n kube-system
