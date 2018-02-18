## Deploy kube in separat files

```
$ cd kube
$ kubectl apply -f .
deployment "api" created
service "api" created
deployment "db" created
service "db" created
deployment "web" created
service "web" created
```

This will create everything needed using one file per Service, ReplicaSet and Deployment.

```
$ kubectl get deploy,service,replicaset
NAME         DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
deploy/api   5         5         5            5           2m
deploy/db    1         1         1            1           2m
deploy/web   1         1         1            1           2m

NAME             TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
svc/api          ClusterIP      None             <none>        8080/TCP         2m
svc/db           ClusterIP      None             <none>        5432/TCP         2m
svc/kubernetes   ClusterIP      10.96.0.1        <none>        443/TCP          1d
svc/web          LoadBalancer   10.109.140.172   <pending>     8081:32724/TCP   2m

NAME                DESIRED   CURRENT   READY     AGE
rs/api-5f75c58954   5         5         5         2m
rs/db-675d6c6dd8    1         1         1         2m
rs/web-65b986cd86   1         1         1         2m
```
