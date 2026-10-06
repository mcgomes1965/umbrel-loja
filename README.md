# Loja de apps do umbrelOS — Marcello

Loja de apps *community* para o umbrelOS, para empacotar serviços que não existem
na App Store oficial e mantê-los sob o ciclo de vida (pasta, permissões, update e
desinstalação) do próprio umbrelOS — sem sair da interface dele.

## Como usar

No umbrelOS: **App Store → (menu) → Community App Stores → Add** e cole a URL
deste repositório. Depois é só instalar os apps normalmente.

## Apps

| App | ID | O que é |
|---|---|---|
| **slskd** | `mcgomes-slskd` | Cliente Soulseek com interface web, para baixar música que tracker nenhum tem |

### slskd

- Baixa em `/downloads/soulseek` (mesma pasta que Lidarr/Bazarr/Jellyfin enxergam),
  com subpasta `incomplete` separada para não sujar a biblioteca.
- Pede acesso à pasta **Downloads** na instalação (declarado via
  `permissions: [STORAGE_DOWNLOADS]`).
- Configuração do Soulseek pela própria interface web (`SLSKD_REMOTE_CONFIGURATION=true`),
  em **Options → Soulseek**.
- Login padrão do app: `slskd` / `slskd`.
- Publica a porta **50300** (conexões de pares do Soulseek).

## Estrutura

```
umbrel-app-store.yml          metadados da loja (id + nome)
mcgomes-slskd/
  umbrel-app.yml              manifesto do app (como o umbrelOS o exibe)
  docker-compose.yml          serviços (app_proxy + slskd)
```

## Nota

O ID do app precisa começar com o ID da loja (`mcgomes-`), conforme a regra do
framework de apps do umbrelOS.
