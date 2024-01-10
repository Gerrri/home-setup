Thats my collection of home-services I'm hosting on a mini-pc running a K3s Kubernetes Cluster (one Node) 

## What I'm currently hosting
- Paperless NGX
- Kubernete Dashboard

## What I'm going to host
- Home-Assistant (currently running on a Raspberry Pi)

## My todos
- Longhorn degraded volumes error
- Longhorn Backups

# Preparing machine
- install k3s (one-line-installation)
- enable ssh
- install open-scsi (for Longhorn)

# Cluster Infrastructure
## Setup [Longhorn](https://github.com/longhorn/longhorn/tree/master/chart)
```
helm repo add longhorn https://charts.longhorn.io
helm repo update
helm install longhorn longhorn/longhorn --namespace longhorn-system --set defaultSettings.defaultReplicaCount=1
```
ATTENTION!: Dont delete the Namespace in case you want to delete Longhorn -> there is an uninstall script.

## SMB storage class
To use my NAS as a storage exchange with some Pods (e.g. paperless), Im going to make a SMB-share accessible via a Storage class out of the Cluster

install on Node
```
sudo apt install cifs-utils smbclient
sudo apt-get install nfs-common
sudo apt-get install nfs-utils
```

install csi-driver-smb
```
helm repo add csi-driver-smb https://raw.githubusercontent.com/kubernetes-csi/csi-driver-smb/master/charts
helm install csi-driver-smb csi-driver-smb/csi-driver-smb --namespace kube-system --version v1.13.0
```
uninstall : helm uninstall csi-driver-smb -n kube-system

```
kubectl create secret generic smbcreds --from-literal username=mr_paperless --from-literal password="<replace_me>" --namespace home-services

kubectl create -f https://raw.githubusercontent.com/kubernetes-csi/csi-driver-smb/master/deploy/example/storageclass-smb.yaml --namespace home-services

#check status

```

