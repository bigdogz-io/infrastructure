# RabbitMQ

Helm installation of [RabbitMQ](https://github.com/bitnami/charts/tree/master/bitnami/rabbitmq) using Bitnami's chart.

**Add bitnami helm repository**
```shell
$ helm repo add bitnami https://charts.bitnami.com/bitnami
"bitnami" has been added to your repositories
```

**Install Helm Chart**
```shell
$ helm install rabbit-local \
  --set auth.username=developer,auth.password=localdeveloper,auth.erlangCookie=cookiemonster \
    bitnami/rabbitmq
NAME: rabbit-local
LAST DEPLOYED: Mon Dec  7 00:19:16 2020
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
** Please be patient while the chart is being deployed **

Credentials:

    echo "Username      : developer"
    echo "Password      : $(kubectl get secret --namespace default rabbit-local-rabbitmq -o jsonpath="{.data.rabbitmq-password}" | base64 --decode)"
    echo "ErLang Cookie : $(kubectl get secret --namespace default rabbit-local-rabbitmq -o jsonpath="{.data.rabbitmq-erlang-cookie}" | base64 --decode)"

RabbitMQ can be accessed within the cluster on port  at rabbit-local-rabbitmq.default.svc.

To access for outside the cluster, perform the following steps:

To Access the RabbitMQ AMQP port:

    echo "URL : amqp://127.0.0.1:5672/"
    kubectl port-forward --namespace default svc/rabbit-local-rabbitmq 5672:5672

To Access the RabbitMQ Management interface:

    echo "URL : http://127.0.0.1:15672/"
    kubectl port-forward --namespace default svc/rabbit-local-rabbitmq 15672:15672
```

