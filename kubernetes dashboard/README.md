# Get a Token for logging in

## create Service Account
kubectl create serviceaccount dashboard-admin-sa

## create Cluster Role Binding
kubectl create clusterrolebinding dashboard-admin-sa 
--clusterrole=cluster-admin --serviceaccount=default:dashboard-admin-sa

## Get Token
kubectl create token dashbaord-admin-sa

-> use token to login.