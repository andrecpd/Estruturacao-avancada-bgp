# Módulo 03 — Prefix-lists e filtros de rotas

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Prefix-lists filtram NLRI pelo prefixo e pelo comprimento da máscara. A regra `permit 203.0.113.0/24` corresponde ao prefixo exato; `permit 203.0.113.0/24 le 28` corresponde ao /24 e aos mais específicos até /28. O comportamento é sequencial e existe deny implícito ao final.

Filtros de entrada devem limitar o que se aceita de cada vizinho. Filtros de saída devem limitar o que se anuncia. Uma allow-list de exportação é preferível a uma política permissiva. Filtros de bogons, prefixos próprios e prefixos de clientes devem ser mantidos e revisados continuamente.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Crie uma lista que permita apenas o prefixo fictício do ISP.
2. Tente anunciar um prefixo de cliente não autorizado.
3. Aplique o filtro na saída e confirme que o prefixo indevido não é exportado.
4. Crie uma regra de comprimento para permitir apenas prefixos de até um limite definido pelo cenário.
5. Teste IPv4 e IPv6 separadamente.

## Exemplo de configuração
Cisco:
```cisco
ip prefix-list ISP-OWNED seq 10 permit 203.0.113.0/24
ip prefix-list CUSTOMER-ALPHA seq 10 permit 198.51.100.0/24
!
route-map EXPORT-TRANSIT permit 10
 match ip address prefix-list ISP-OWNED
route-map EXPORT-TRANSIT permit 20
 match ip address prefix-list CUSTOMER-ALPHA
route-map EXPORT-TRANSIT deny 100
```
O exemplo é parcial: confirme que os prefixos estão autorizados e aplique a política de saída ao vizinho correto.

## Comandos de verificação
```text
show ip prefix-list
show route-map
show ip bgp neighbors <IP> advertised-routes
show ip bgp neighbors <IP> routes

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Prefixos autorizados passam; prefixos não autorizados são bloqueados.
- O aluno explica `ge` e `le`.
- A política não bloqueia acidentalmente o prefixo legítimo esperado.

## Perguntas de revisão
1. Qual problema operacional este recurso resolve?
2. Qual seria o risco de aplicá-lo sem filtros ou política explícita?
3. Que evidência comprova que a configuração funcionou?
4. Como o comportamento muda quando um peer ou next-hop falha?

## Registro de evidências
Preencha no seu caderno ou em `evidencias/`:
- Data e versão do software:
- Topologia:
- Configuração aplicada:
- Comandos e saídas:
- Resultado esperado:
- Resultado observado:
- Problemas encontrados:
- Rollback:
