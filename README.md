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
helm install longhorn/longhorn --name longhorn --namespace longhorn-system
```
ATTENTION!: Dont delete the Namespace in case you want to delete Longhorn -> there is an uninstall script.
