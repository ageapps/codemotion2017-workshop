## Deployment
```
cd ./demo/k8s/

# Substitute $NAMESPACE inprefix
kubectl apply -f global-config.yaml
kubectl get cm --namespace=$NAMESPACE

kubectl apply -f echo-server.yaml
# Substitute $NAMESPACE
kubectl apply -f ingress/test-ingress.yaml
#Access IP/$NAMESPACE

kubectl delete -f echo-server.yaml
kubectl delete -f ingress/test-ingress.yaml


kubectl apply -f mongo
kubectl apply -f rabbit
kubectl apply -f gluster
kubectl apply -f docker-chat

kubectl logs -f [docker-chat-ID]

kubectl apply -f ingress/app-ingress.yaml

kubectl scale --replicas=3 -f docker-chat

```

## Get Rabbit dashboard

```
kubectl port-forward [POD_ID] 8080:15672
```
## Get GLUSTERFS volume nginx

```
kubectl port-forward [POD_ID] 8080:8080
```