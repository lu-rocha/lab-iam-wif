# Configurando Workload Identity Federation para GitHub Actions 🔐

## Fluxo da autenticação via Workload Identity Federation:

```text
GitHub Actions
    ↓
Gera token OIDC temporário
    ↓
Google Provider valida:
- issuer
- repository
- pool
- provider
    ↓
GCP permite assumir a SA ci-runner
    ↓
Pipeline ganha permissões da SA

```

## Conceitos Importantes:

| Conceito                      | Explicação                                         |
| ----------------------------- | -------------------------------------------------- |
| Workload Identity Federation  | Permite autenticação sem chave JSON                |
| OIDC                          | Protocolo usado pelo GitHub para emitir identidade |
| Attribute Mapping             | Mapeia claims do token para atributos do GCP       |
| Service Account Impersonation | GitHub assume temporariamente a identidade da SA   |
| Token Temporário              | Credencial expira automaticamente                  |

