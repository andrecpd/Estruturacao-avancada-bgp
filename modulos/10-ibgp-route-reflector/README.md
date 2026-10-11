# Módulo 10 — iBGP, IGP e Route Reflectors

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Em uma malha iBGP, cada roteador precisa de sessões com os demais, o que cresce quadraticamente. Route Reflectors reduzem a quantidade de sessões ao refletir rotas entre clientes. O desenho precisa considerar redundância de RRs, cluster ID, originator ID, loop prevention e reachability do next-hop.

O IGP ou rotas estáticas devem garantir alcançabilidade dos next-hops usados pelo BGP. `next-hop-self` pode ser necessário em determinados desenhos, mas altera o ponto de encaminhamento e precisa refletir a arquitetura desejada. Não redistribua rotas indiscriminadamente entre IGP e BGP.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Crie três roteadores no mesmo AS.
2. Estabeleça iBGP full mesh e confirme propagação.
3. Converta para Route Reflector e clientes.
4. Derrube um RR e verifique continuidade se houver RR redundante.
5. Torne um next-hop inalcançável e diagnostique por que a rota deixa de ser utilizável.

## Exemplo de configuração
Cisco ilustrativo:
```cisco
router bgp 64500
 neighbor 10.255.0.2 remote-as 64500
 neighbor 10.255.0.2 route-reflector-client
```
Configuração incompleta: configure loopbacks, reachability via IGP/estático e sessões conforme a topologia. Confirme suporte e sintaxe na versão usada.

## Comandos de verificação
```text
show ip bgp summary
show ip bgp
show ip route <next-hop>
show ip bgp neighbors

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Rotas internas são distribuídas conforme o desenho.
- O next-hop está alcançável.
- O aluno explica prevenção de loops e a necessidade de redundância de RR.

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
