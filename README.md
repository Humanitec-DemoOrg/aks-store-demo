# aks-store-demo

https://github.com/Azure-Samples/aks-store-demo

TODOs:
- [X] `order-service`
- [X] `amqp` Humanitec resource definition
- [X] `product-service`
- [X] `store-front`
- [X] `score-compose`

Deploy locally:
```bash
make compose-up
```

Deploy to Humanitec:
```bash
export HUMANITEC_ORG=FIXME
export HUMANITEC_APPLICATION=store-front
export HUMANITEC_ENVIRONMENT=development

humctl login

humctl create app ${HUMANITEC_APPLICATION} \
    --name ${HUMANITEC_APPLICATION}

humctl apply \
    -f resources/in-cluster-rabbitmq.yaml

make score-deploy
```