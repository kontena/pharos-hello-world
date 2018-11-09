# Kontena Pharos Hello World

## Prerequisities

- working [Kontena Pharos](https://www.kontena.io/pharos/) cluster
- Kontena Pharos addons:
    - ingress-nginx
    - cert-manager
- dns name pointed to your Kontena Pharos cluster
- [Kontena Mortar](https://github.com/kontena/mortar/) installed for deploying the YAML manifests

## Deployment

```sh
$ mortar fire --var host=hello.mydomain.com --var email=me@domain.com deploy/ hello
```

where `hello.mydomain.com` is a DNS name that points to the hello-world app. Note: you need to configure this outside of Kontena Pharos.

Deployment does the following steps:

- creates `hello-world` namespace
- adds `ResourceQuota` to the namespace
- adds Let's Encrypt certificate `Issuer` to the namespace
- creates `Deployment` to the namespace
- creates `Service` to the namespace that targets the deployment
- creates `Ingress` for the given host that targets the service
- creates `Certificate` for the given host