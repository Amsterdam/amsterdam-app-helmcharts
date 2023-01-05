# amsterdam-app-helmcharts
Amsterdam App Helm chart repo

## Install the charts

First configure the Helm repository:

```bash
helm repo add aapp https://amsterdam.github.io/amsterdam-app-helmcharts/
helm repo update
```

Then install the modules chart:

```bash
helm upgrade --install \
  modules aapp/backend \
  --create-namespace \
  --namespace aapp \
  --set "settings.allowedHosts=api.aapp.example.com" \
  --set "settings.defaultPdokMunicipalities=Amsterdam" \
  --set "settings.userIdField=email" \
  --set "ingress.enabled=true" \
  --set "ingress.hosts[0]=api.aapp.example.com"
```

```

## Uninstall the charts

To delete the charts:

```bash
helm delete --namespace aapp modules
```

And finally remove the namespace:

```bash
kubectl delete namespace aapp
```
