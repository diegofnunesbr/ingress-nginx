# Ingress NGINX

Este README descreve a instalação e validação do **Ingress Controller NGINX** em um cluster Kubernetes, utilizando o manifesto `ingress-nginx.yaml`.

## Pré-requisitos

- `Kubernetes` instalado
- IP `192.168.15.3` disponível na rede

---

## Instalação

1. **Aplique o manifesto no cluster:**

```bash
kubectl apply -f ingress-nginx.yaml
