## Do this manualy to create the PC secret
Create the following file on a linux machine where you have the rancher CLI installed 

```yaml
apiVersion: v1
kind: Secret
metadata:
 name: ntnx-pc-secret
 namespace: ntnx-system
data:
 # base64 encoded prism-ip:prism-port:admin:password.
 # E.g.: echo -n "10.0.00.000:9440:admin:mypassword" | base64
 key: MTAuMC4wMC4wMDA6OTQ0MDphZG1pbjpteXBhc3N3b3Jk 
 ```
 
then apply the file to the ntnx-system namespace

```bash 
rancher kubectl apply -f pc-secret.yaml
