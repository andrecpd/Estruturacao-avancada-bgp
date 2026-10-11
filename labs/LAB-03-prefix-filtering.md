# LAB-03 — Filtragem de prefixos

**Objetivo:** aceitar somente prefixos autorizados e testar prefixos indevidos.

## Política pretendida
Aceitar `198.51.100.0/24` exato. Negar `198.51.100.0/25`, `198.51.100.0/24` se vier de peer não autorizado e qualquer prefixo não listado.

## Exemplo Cisco IOS/IOS XE
```cisco
ip prefix-list CUSTOMER-IN seq 10 permit 198.51.100.0/24
! Negação implícita para tudo o mais
route-map CUSTOMER-IN permit 10
 match ip address prefix-list CUSTOMER-IN
```

Aplique o route-map inbound no peer de laboratório e verifique rotas recebidas, aceitas e instaladas. O comando para mostrar rotas recebidas sem filtro pode exigir `soft-reconfiguration inbound` ou Route Refresh, conforme plataforma.

## Testes negativos
- Anunciar um prefixo não listado.
- Anunciar um prefixo mais específico.
- Retirar a rota autorizada e verificar que ela desaparece.

## Critério de aceitação
Somente o prefixo exato autorizado pode ser aceito. Documente como comprovou o bloqueio, não apenas a ausência de ping.
