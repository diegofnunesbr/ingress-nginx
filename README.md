# Ingress NGINX

Este guia descreve a instalação e remoção do **Ingress NGINX** em um cluster Kubernetes, utilizando o manifesto `ingress-nginx.yaml`.

## Pré-requisitos

- `Kubernetes` instalado
- `kubectl` instalado
- IP `192.168.1.3` disponível na rede

## Estrutura do repositório

```text
ingress-nginx/
├── applications/
│   └── argocd.yaml        # Application do Argo CD
├── ingress-nginx.yaml     # Manifests do Ingress NGINX
└── README.md
```

---

## Instalar o Ingress NGINX

```bash
git clone https://github.com/diegofnunesbr/ingress-nginx.git
cd ingress-nginx
kubectl apply -f applications/argocd-ingress-nginx.yaml
```

## Remover o Ingress NGINX

```bash
cd ingress-nginx
kubectl delete -f applications/argocd-ingress-nginx.yaml
kubectl delete namespace ingress-nginx --ignore-not-found
```
