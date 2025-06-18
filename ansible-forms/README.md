After the DB is deployed. Visit the application. 
Create the Schema, then restart this deployment 

```bash
rancher kubectl -n forms rollout restart deployment forms
```

or: 
```bash
rancher kubectl -n forms get pods
rancher kubectl -n forms delete pods forms-5dbdfcbfb5-xxx
```

Skapa tls secret
```bash
rancher kubectl -n forms create secret tls forms-tls --cert=forms-demo.domain.com.pem --key=forms-demo.domain.com.key
```