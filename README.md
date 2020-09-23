# Kubernetes

Create file yaml
```bash
kubectl create -f service-nodeport.yaml 
```
Output:

```bash
replicaset.apps/tailwind-nodeport created
service/tailwind-service-nodeport created
```

Untuk melihat status
```bash
kubectl get all --show-labels
```
Output:
```bash
NAME                          READY   STATUS    RESTARTS   AGE   LABELS
pod/tailwind-nodeport-7qv5c   1/1     Running   0          6s    name=tailwind-nodeport
pod/tailwind-nodeport-lxx7d   1/1     Running   0          6s    name=tailwind-nodeport

NAME                                TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE   LABELS
service/kubernetes                  ClusterIP   10.96.0.1       <none>        443/TCP        48s   component=apiserver,provider=kubernetes
service/tailwind-service-nodeport   NodePort    10.96.231.139   <none>        80:30001/TCP   6s    <none>

NAME                                DESIRED   CURRENT   READY   AGE   LABELS
replicaset.apps/tailwind-nodeport   2         2         2       6s    <none>
```

Untuk melihat List
```bash
minikube service list
```
Output:
```bash
|-------------|---------------------------|--------------|-------------------------|
|  NAMESPACE  |           NAME            | TARGET PORT  |           URL           |
|-------------|---------------------------|--------------|-------------------------|
| default     | kubernetes                | No node port |
| default     | tailwind-service-nodeport |           80 | http://172.17.0.3:30002 |
| kube-system | kube-dns                  | No node port |
|-------------|---------------------------|--------------|-------------------------|

```

Untuk Delete semua pod 
```bash
kubectl delete all --all
```

Output:
```bash
pod "tailwind-ingress-hxqhs" deleted
pod "tailwind-ingress-pmt6x" deleted
pod "tailwind-loadbalancer-fxp9m" deleted
pod "tailwind-loadbalancer-s5zt6" deleted
pod "tailwind-nodeport-6dkzq" deleted
pod "tailwind-nodeport-fvvf4" deleted
service "kubernetes" deleted
service "tailwind-service-ingress" deleted
service "tailwind-service-loadbalancer" deleted
service "tailwind-service-nodeport" deleted
replicaset.apps "tailwind-ingress" deleted
replicaset.apps "tailwind-loadbalancer" deleted
replicaset.apps "tailwind-nodeport" deleted

```
