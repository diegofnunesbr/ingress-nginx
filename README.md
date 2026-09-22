# ingress-nginx

Instalação do **ingress-nginx** via chart oficial (`ingress-nginx/ingress-nginx`),
usando uma Application multi-source do Argo CD: o chart vem direto do
repositório Helm oficial, e o `values.yaml` vem deste repositório.

Roda com `hostNetwork: true`: o pod escuta direto nas portas 80/443 do IP
do node (`192.168.0.4`), sem Service `LoadBalancer` e sem MetalLB. Funciona
porque o cluster é single-node (o IP do node já é o IP de entrada). Se um
dia tiver mais de um node, isso precisa ser revisto (MetalLB ou similar).

## Pré-requisitos

- `Kubernetes` instalado
- `kubectl` instalado
- ArgoCD instalado (ver repositório `argocd`)
- Portas 80/443 livres no node

## Estrutura do repositório

```text
ingress-nginx/
├── applications/
│   └── argocd.ingress-nginx.yaml     # Application multi-source do Argo CD
├── values.yaml                       # values do chart oficial
└── README.md
```

## Instalar o ingress-nginx

```bash
git clone https://github.com/diegofnunesbr/ingress-nginx.git
cd ingress-nginx
kubectl apply -f applications/argocd.ingress-nginx.yaml
```

**Lembrete:** a Application aponta pro GitHub, não pro clone local -
mudança em `values.yaml` só tem efeito depois de `git push`.

## Remover o ingress-nginx

Derruba o acesso a todos os serviços expostos por Ingress.

```bash
cd ingress-nginx
kubectl delete -f applications/argocd.ingress-nginx.yaml
kubectl delete namespace ingress-nginx --ignore-not-found
```
