Secret for AWX connection to postgress needs to be created manually. 

```bash
rancher kubectl -n awx-int get secret awx-postgres-app -o json | jq '.data | {"apiVersion": "v1", "kind": "Secret", "metadata": {"name": "awx-postgres-secret", "namespace": "awx"}, "data": {"database": .dbname, "host": .host, "password": .password, "port": .port, "type": "dW5tYW5hZ2Vk", "username": .username}}' | rancher kubectl apply -f -
```

When you have created the secret for postgres app, you might need to restart the awx deployment if that started before the secret where recreated, and then rancher-fleet redeploys that. 
```bash
rancher kubectl -n awx delete awx awx
```

Create tls secret
```bash
rancher kubectl -n awx-int create secret tls awx-tls-secret --cert=awx-demo.app.gdm.se.pem --key=awx-demo.app.gdm.se.key
```

