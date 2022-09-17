helm repo add mojo2600 https://mojo2600.github.io/pihole-kubernetes/
helm repo update
helm search repo pihole
helm show values mojo2600/pihole > pihole-values-orig.yaml
k apply -f pvc.yaml -n infra
helm install pihole mojo2600/pihole --values pihole-values.yaml -n infra
