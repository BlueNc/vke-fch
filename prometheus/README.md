## Grafana
* url : https://grafana.codeblue.ovh/
* user : admin
* password :
    ```
    kubectl get secret prometheus-grafana -n prometheus -o jsonpath="{.data.admin-password}" | base64 -d && echo
    ```
