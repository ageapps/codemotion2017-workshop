

## Create Cluster 
```
gcloud container clusters create codemotion-cluster --num-nodes=3
```
[imagen de consola y cluster]

## Instalar kubectl
[instalation guide](https://cloud.google.com/container-engine/)

## Setup namespaces
```
export  NAMESPACE=code-[NUMBER_ASSIGNED]
kubectl create namespace $NAMESPACE
sed 's/ASSIGNED-NAMESPACE/'$NAMESPACE'/1' ./config/tmp-config > ./config/cluster-config
kubectl config set-context $(kubectl config current-context) --namespace=$NAMESPACE
kubectl config view | grep namespace:
```

## Setup kubectl configuration
```
export  KUBECONFIG_SAVED=$KUBECONFIG
export  KUBECONFIG=$KUBECONFIG:$(pwd)/config/cluster-config
kubectl get nodes
NAME                                                STATUS    AGE       VERSION
gke-codemotion-cluster-default-pool-548f897f-4d0p   Ready     51m       v1.7.8-gke.0
gke-codemotion-cluster-default-pool-548f897f-5sx5   Ready     51m       v1.7.8-gke.0
gke-codemotion-cluster-default-pool-548f897f-h18m   Ready     51m       v1.7.8-gke.0
gke-codemotion-cluster-default-pool-548f897f-rj3l   Ready     51m       v1.7.8-gke.0
gke-codemotion-cluster-default-pool-548f897f-sm28   Ready     51m       v1.7.8-gke.0

# At the end of the workshop
export  KUBECONFIG=$KUBECONFIG_SAVED
```


## Syncronize docker-chat repo
```
rsync -r ../docker-chat/ ./demo/
```