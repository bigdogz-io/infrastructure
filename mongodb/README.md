# MongoDB

Helm installation of [MongoDB](https://github.com/bitnami/charts/tree/master/bitnami/mongodb) using Bitnami's chart.

## Local Developer

**Add bitnami helm repository**
```shell
$ helm repo add bitnami https://charts.bitnami.com/bitnami
"bitnami" has been added to your repositories
```

**Install Helm Chart**
```shell
$ helm install mongo-local --set \
  auth.rootPassword=localdeveloper \
    bitnami/mongodb
NAME: mongo-local
LAST DEPLOYED: Mon Dec  7 00:09:34 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: Noneπ
NOTES:
** Please be patient while the chart is being deployed **

MongoDB can be accessed on the following DNS name(s) and ports from within your cluster:

    mongo-local-mongodb.default.svc.cluster.local

To get the root password run:

    export MONGODB_ROOT_PASSWORD=$(kubectl get secret --namespace default mongo-local-mongodb -o jsonpath="{.data.mongodb-root-password}" | base64 --decode)

To connect to your database, create a MongoDB client container:

    kubectl run --namespace default mongo-local-mongodb-client --rm --tty -i --restart='Never' --env="MONGODB_ROOT_PASSWORD=$MONGODB_ROOT_PASSWORD" --image docker.io/bitnami/mongodb:4.4.2-debian-10-r0 --command -- bash

Then, run the following command:
    mongo admin --host "mongo-local-mongodb" --authenticationDatabase admin -u root -p $MONGODB_ROOT_PASSWORD

To connect to your database from outside the cluster execute the following commands:

    kubectl port-forward --namespace default svc/mongo-local-mongodb 27017:27017 &
    mongo --host 127.0.0.1 --authenticationDatabase admin -p $MONGODB_ROOT_PASSWORD
```
