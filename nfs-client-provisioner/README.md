#https://github.com/kubernetes-sigs/nfs-subdir-external-provisioner
#kubectl apply -k dev|prod
#k delete sc nfs-client
helm install nfs-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner --values nfs-provisioner-archived.yaml -n kube-system
