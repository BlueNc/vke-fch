./khoj/secret.yaml
```
apiVersion: v1
kind: Secret
metadata:
  name: google-client
  annotations:
    sealedsecrets.bitnami.com/cluster-wide: "true"
data:
  client-secret: <echo -n "****" | base64>
  ```

  kubeseal -f ./khoj/secret.yaml --format yaml > ./khoj/secret-sealed.yaml