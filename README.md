# kubernetes

# Configure TLS with Self-Signed certificates

`openssl req -newkey rsa:4096 -x509 -sha256 -days 3650 -nodes -out ams.crt -keyout ams.key`

`kubectl create secret tls antmedia-cert --key="ams.key" --cert="ams.crt"`

# Ingress
```
tls:
- secretName: antmedia-cert
  hosts:
    - test.antmedia.xyz
```

# How to use docker private repository on Kubernetes
```
kubectl create secret docker-registry "docker"  --docker-server="https://index.docker.io/v1/" --docker-username="test" --docker-password="test"
```
Add to your YAML file the following lines.
```
imagePullSecrets:
      - name: docker
```
#
