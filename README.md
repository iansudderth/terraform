# run setup
1. run local.sh
```
bash local.sh
```

# run terraform
1. run terraform in any sub directory
```
cd kubernetes
terraform init
terraform plan
terraform apply
```

# create secrets (optional)
```
htpasswd auth $SOME_USER
kubectl create secret generic -n monitoring   custom-nginx-basic-auth --from-file=./auth --dry-run -o yaml | kubectl apply -f -
kubectl create secret generic -n istio-system custom-nginx-basic-auth --from-file=./auth --dry-run -o yaml | kubectl apply -f -
```

# docker registry secret (optional)
```
docker run --entrypoint htpasswd registry:2 -Bbn user password > ./htpasswd
```

# TODO:
```
fix thanos or deprecate in favor of metricbeat
fix logging to work out local vs non local for full testing, possibly minio
fix istio telemetry and policy
fix kubeconfig
fix prom variable storage spec
add auditbeat
add packetkbeat
add auditbeat
add heartbeat
deprecate helm stable
add grafana iac
add vault transit token
```
