# ingress-nginx

Este guia descreve a instalação e remoção do **ingress-nginx** em um cluster Kubernetes, utilizando o manifesto `ingress-nginx.yaml`.

## Pré-requisitos

- `Kubernetes` instalado
- `kubectl` instalado
- IP `192.168.1.3` disponível na rede

## Estrutura do repositório

```text
ingress-nginx/
├── applications/
│   └── argocd.ingress-nginx.yaml     # Application do Argo CD
├── ingress-nginx.yaml                # Manifests do ingress-nginx
└── README.md
```

---

## Instalar o ingress-nginx

```bash
git clone https://github.com/diegofnunesbr/ingress-nginx.git
cd ingress-nginx
kubectl apply -f applications/argocd.ingress-nginx.yaml
```

## Remover o ingress-nginx

```bash
cd ingress-nginx
kubectl delete -f applications/argocd.ingress-nginx.yaml
kubectl delete namespace ingress-nginx --ignore-not-found
```
