# Reverse Proxy

This example deploys a pod with containers containing a reverse proxy (Nginx or HAProxy) service.

See the [environment base file](../../../examples/rproxy.yml) for details about the deployment.

More details can be seen at http://github.com/lucasbasquerotto/ext-pod/tree/master/rproxy.

## Local - Hub

To deploy the local hub ([pod-rproxy-local-complete-hub](pod-rproxy-local-complete-hub.yml)), in which the reverse proxy service proxies the requests to 3 different pods using different domains, you must start the main pod, after deploying the project, and then the other 3 pods:

_After the project was deployed locally:_

```bash
./projects/dev/demo/files/cloud/ctxs/local_hub/node-pods/app/pods/rproxy_hub/run u
```

- Access `localhost:8080` -> OK
- Access `web1.localhost:8080` -> Error 503
- Access `web2.localhost:8080` -> Error 503
- Access `web3.localhost:8080` -> Error 503

```bash
./projects/dev/demo/files/cloud/ctxs/local_hub/node-pods/app/pods/rproxy_web_1/run u
```

- Access `localhost:8080` -> OK
- Access `web1.localhost:8080` -> OK
- Access `web2.localhost:8080` -> Error 503
- Access `web3.localhost:8080` -> Error 503

```bash
./projects/dev/demo/files/cloud/ctxs/local_hub/node-pods/app/pods/rproxy_web_2/run u
```

- Access `localhost:8080` -> OK
- Access `web1.localhost:8080` -> OK
- Access `web2.localhost:8080` -> OK
- Access `web3.localhost:8080` -> Error 503

```bash
./projects/dev/demo/files/cloud/ctxs/local_hub/node-pods/app/pods/rproxy_web_3/run u
```

- Access `localhost:8080` -> OK
- Access `web1.localhost:8080` -> OK
- Access `web2.localhost:8080` -> OK
- Access `web3.localhost:8080` -> OK

_When accessing `http://localhost:8080` more than 5 times in less than `10s`, it should return 429 errors (Too Many Requests), for demonstration purposes. The other paths are limited when there are more than 20 requests in less than `10s`._

## Local - Replicas

To deploy the local replicas ([pod-rproxy-local-complete-replicas](pod-rproxy-local-complete-replicas.yml)), in which the reverse proxy service load balances the requests to 3 different pods, you must start the main pod, after deploying the project, and then the other 3 pods:

_After the project was deployed locally:_

```bash
./projects/dev/demo/files/cloud/ctxs/local_replicas/node-pods/app/pods/rproxy_replicas_hub/run u
```

- Access `localhost:8080` -> OK
- Access `replica.localhost:8080` -> Error 503

```bash
./projects/dev/demo/files/cloud/ctxs/local_replicas/node-pods/node_replica_1/pods/rproxy_replica_1/run u
```

- Access `localhost:8080` -> OK
- Access `replica.localhost:8080` -> OK with pod name `rproxy_replica_1`

```bash
./projects/dev/demo/files/cloud/ctxs/local_replicas/node-pods/node_replica_2/pods/rproxy_replica_2/run u
```

- Access `localhost:8080` -> OK
- Access `replica.localhost:8080` -> OK with pod name alternating between `rproxy_replica_1` and `rproxy_replica_2`

```bash
./projects/dev/demo/files/cloud/ctxs/local_replicas/node-pods/node_replica_3/pods/rproxy_replica_3/run u
```

- Access `localhost:8080` -> OK
- Access `replica.localhost:8080` -> OK with pod name alternating among `rproxy_replica_1`, `rproxy_replica_2` and `rproxy_replica_3`

_When accessing `http://localhost:8080` more than 5 times in less than `10s`, it should return 429 errors (Too Many Requests), for demonstration purposes. The other paths are limited when there are more than 20 requests in less than `10s`._
