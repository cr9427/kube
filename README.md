# kube

export K3SUP_MASTER="cube1"
export K3SUP_AGENT="pve1"
export K3SUP_CHANNEL="stable"
export K3SUP_INSTALL_USER="automator"
export K3SUP_INSTALL_KEY="~/.ssh/automator"

k3sup install \
  --host $K3SUP_MASTER \
  --k3s-extra-args '--cluster-cidr=10.42.0.0/16,fd42::/48 --service-cidr=10.43.0.0/16,fd43::/112 --node-ip=192.168.1.24,fd00:cafe::24 --disable-network-policy' \
  --no-extras \
  --ssh-key $K3SUP_INSTALL_KEY \
  --user $K3SUP_INSTALL_USER \
  --sudo \
  --k3s-channel $K3SUP_CHANNEL

#### join an agent
k3sup join \
  --host $K3SUP_AGENT \
  --server-host $K3SUP_MASTER \
  --server-user $K3SUP_INSTALL_USER \
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
