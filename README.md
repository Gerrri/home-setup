# Debian
install open-scsi

# Infrastructure
## Longhorn (https://github.com/longhorn/longhorn/tree/master/chart)
helm repo add longhorn https://charts.longhorn.io
helm repo update

helm install longhorn/longhorn --name longhorn --namespace longhorn-system

ATTENTION!: Dont delete the Namespace in case you want to delete Longhorn - there is an uninstall script.
