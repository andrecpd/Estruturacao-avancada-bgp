# Topologias

## Etapa 1 — eBGP
R1 (AS64500) — R2 (AS64501)

## Etapa 2 — Dois upstreams
Transit-A (AS64501) — Edge-1 (AS64500) — Transit-B (AS64502)

## Etapa 3 — ISP completo
- AS64500: Edge-1, Edge-2 e core iBGP/IGP
- AS64501: Transit-A
- AS64502: Transit-B
- AS64520: Peer-LAB
- AS64510: Cliente Alpha
- AS64530: Cliente Beta

## Regras
- Prefixos de documentação não devem ser anunciados na Internet.
- Use enlaces internos de laboratório separados dos prefixos de serviço.
- Documente quais interfaces e sessões são redundantes de fato.
