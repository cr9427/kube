helm repo add https://jupyterhub.github.io/helm-chart/
helm repo update
helm search repo pebble
helm show values jupyterhub/pebble > pebble-values-orig.yaml



k create namespace pihole
k apply -f pvc.yaml -n pihole
helm install pihole mojo2600/pihole --values pihole-values.yaml -n pihole --create-namespace
