# Install

1. create a namespace for the coder installation:
```bash
kubectl create namespace longhorn-system
```

2. Add basic auth credentials:
```bash
USER=longhorn; PASSWORD=izVVRDxvUghkeHny; echo "${USER}:$(openssl passwd -stdin -apr1 <<< ${PASSWORD})" >> ./auth
```

3. Create basic auth secret:
```bash
kubectl create secret generic basic-auth -n longhorn-system --from-file=./auth
```

4. Add the Helm repository:

```bash
helm repo add longhorn https://charts.longhorn.io
```

5. Update your local Helm chart repository cache:

```bash
helm repo update
```

6. Install the Longhorn Helm chart:

```bash
helm install longhorn longhorn/longhorn \
  --namespace longhorn-system \
  --create-namespace \
  -f ./values.yaml
```

