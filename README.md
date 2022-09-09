# kube

export K3SUP_MASTER="cube1"
export K3SUP_CHANNEL="stable"
export K3SUP_INSTALL_USER="automator"
export K3SUP_INSTALL_KEY="~/.ssh/automator"

k3sup install \
  --host $K3SUP_MASTER \
  --k3s-extra-args '--no-deploy servicelb' \
  --ssh-key $K3SUP_INSTALL_KEY \
  --user $K3SUP_INSTALL_USER \
  --sudo \
  --k3s-channel $K3SUP_CHANNEL



#### as cluster
k3sup install \
  --cluster \
  --k3s-extra-args '--no-deploy servicelb' \
  --host cube1 \
  --ssh-key ~/.ssh/automator \
  --user automator \
  --sudo \
  --k3s-channel stable
