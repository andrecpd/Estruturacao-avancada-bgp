# Módulo 13 — VRF, VPNv4/VPNv6 e MPLS L3VPN

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
VRF mantém tabelas de roteamento separadas no mesmo equipamento. Em MPLS L3VPN, Route Distinguisher (RD) torna rotas VPN distintas; Route Targets (RTs) controlam importação e exportação entre VRFs. MP-BGP pode transportar rotas VPNv4/VPNv6 entre PE routers, enquanto MPLS fornece o transporte do plano de dados.

RD não é política de import/export. RTs são o mecanismo comum de associação entre VRFs. Um erro de RT pode causar vazamento de rotas entre clientes, portanto a configuração precisa ser revisada como controle de isolamento.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Crie VRF Alpha e VRF Beta.
2. Configure rotas distintas em cada VRF.
3. Confirme que Alpha não alcança Beta.
4. Em plataforma compatível, configure RTs e MP-BGP VPN.
5. Faça um teste controlado de RT incorreto no laboratório e observe o vazamento; reverta imediatamente.

## Exemplo de configuração
Exemplo conceitual, dependente da plataforma:
```text
VRF ALPHA:
  RD 64500:10
  RT import/export 64500:10

VRF BETA:
  RD 64500:20
  RT import/export 64500:20
```
A sintaxe completa varia significativamente entre IOS XE, IOS XR e Junos; use documentação específica.

## Comandos de verificação
```text
show vrf
show ip route vrf ALPHA
show bgp vpnv4 unicast
show route-target

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Rotas permanecem isoladas por padrão.
- O aluno explica RD versus RT.
- O teste de vazamento é documentado e revertido.

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
