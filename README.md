Change directory to `/opt/services` and put both the files in that location

```
cd /opt/services
mkdir loki-data
docker compose up -d
```

Install Promtail agent on kubernetes cluster to send logs to the grafana loki vm

```
helm install promtail grafana/promtail --kubeconfig kube-cluster-kubeconfig -n logging --create-namespace --set "config.clients[0].url=http://vm-ip:3100/loki/api/v1/push"
```
