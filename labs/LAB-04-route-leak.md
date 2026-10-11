# LAB-04 — Prevenção de route leak

**Objetivo:** garantir que um AS cliente não exporte rotas aprendidas de um upstream para outro upstream sem autorização.

## Topologia
```mermaid
flowchart TB
 U1[Transit A AS65001] --- E1[Edge AS65010]
 U2[Transit B AS65002] --- E2[Edge AS65010]
 E1 --- CORE[Core AS65010]
 E2 --- CORE
 C[Cliente AS65101] --- E1
```

## Política
- Inbound do cliente: aceitar apenas prefixos autorizados do cliente.
- Outbound para o cliente: anunciar somente rotas contratadas.
- Outbound para upstreams: anunciar prefixos próprios e de clientes autorizados, nunca full-table aprendida de outro upstream por acidente.

## Exercício
Monte prefix-lists separadas por peer e route-maps inbound/outbound. Inspecione `advertised-routes` em cada sessão. Introduza uma linha permissiva errada e demonstre como o teste de política a detecta.

## Critério de aceitação
Nenhuma rota de Transit A é anunciada a Transit B, salvo se o cenário declarar explicitamente que o AS fornece trânsito entre eles.
