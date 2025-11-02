#Setup the k8s cluster using minikube on local machine with 3 nodes
minikube start --nodes=3

#To stop the cluster
minikube stop

#Apply the dashboard manifest
kubectl apply -f recommended.yaml
kubectl apply -f dashboard-admin-user.yaml

#To get the token to login to dashboard
kubectl -n kubernetes-dashboard describe secret admin-user-token

#To enable the proxy to api server
kubectl proxy

#To access the dashboard
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/workloads?namespace=_all
