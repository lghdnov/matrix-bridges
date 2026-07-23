# matrix-bridges

Helm charts for Matrix bridges.

## mautrix-telegram

Production-ready Helm chart for the [mautrix-telegram](https://github.com/mautrix/telegram) bridge running in puppeting mode.

### Quick start

```bash
helm lint mautrix-telegram/
helm template my-telegram-bridge mautrix-telegram/ -f my-values.yaml
helm install my-telegram-bridge mautrix-telegram/ -f my-values.yaml
```

### Required values

```yaml
homeserver:
  address: "https://matrix.example.com"
  domain: "example.com"

telegram:
  apiId: "12345"
  apiHash: "your_api_hash"
  botToken: "your_bot_token"

registration:
  asToken: "appservice_token"
  hsToken: "homeserver_token"
```

### Registration

After install, extract `registration.yaml` and register it with your homeserver:

```bash
kubectl get secret my-telegram-bridge-mautrix-telegram \
  -n <namespace> \
  -o jsonpath='{.data.registration\\.yaml}' | base64 -d
```
