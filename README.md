# aks-store-demo

https://github.com/Azure-Samples/aks-store-demo

![](https://github.com/Azure-Samples/aks-store-demo/raw/main/assets/demo-arch.png)

TODOs:
- [X] `order-service`
- [X] `amqp` Humanitec resource definition
- [X] `product-service`
- [X] `store-front`
- [ ] `score-compose` (current issue with `service`)
- [X] `mongodb` Humanitec resource definition
- [X] `store-admin`
- [X] `makeline-service`
- [ ] `virtual-customer`
- [ ] `virtual-worker`
- [ ] Azure Cosmos DB

Deploy locally (current issue with `service`):
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
humctl apply \
    -f resources/in-cluster-mongodb.yaml

make score-deploy
```