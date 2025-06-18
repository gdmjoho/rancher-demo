Secret for AWX connection to postgress needs to be created manually. 

```bash
rancher kubectl -n awx-int get secret awx-postgres-app -o json | jq '.data | {"apiVersion": "v1", "kind": "Secret", "metadata": {"name": "awx-postgres-secret", "namespace": "awx-int"}, "data": {"database": .dbname, "host": .host, "password": .password, "port": .port, "type": "dW5tYW5hZ2Vk", "username": .username}}' | rancher kubectl apply -f -
```

When you have created the secret for postgres app, you might need to restart the awx deployment, and then rancher-fleet redeploys that. 
```bash
rancher kubectl -n awx-int delete awx awx-int
```



Skapa tls secret
```bash
rancher kubectl -n awx-int create secret tls awx-tls-secret --cert=awx-test.app.gdm.se.pem --key=awx-test.app.gdm.se.key
```

