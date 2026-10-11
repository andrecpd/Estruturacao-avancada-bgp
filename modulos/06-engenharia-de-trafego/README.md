# Módulo 06 — Engenharia de tráfego: entrada e saída

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
A engenharia de tráfego BGP envolve dois planos diferentes. Para tráfego de saída do seu AS, Local Preference é um mecanismo interno típico. Para influenciar tráfego de entrada, pode-se anunciar prefixos mais específicos quando autorizado, usar AS-PATH prepend ou communities documentadas pelo upstream. A decisão final de entrada pertence às redes remotas e suas políticas.

MED é um sinal limitado e pode ser ignorado ou comparado somente em certas condições. Prepend não garante resultado, pois políticas remotas, peering, Local Preference e comprimento de prefixo podem prevalecer. Anúncios mais específicos devem respeitar alocação, filtros, RPKI e políticas dos peers.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Desenhe dois upstreams e dois destinos de teste.
2. Configure Local Preference para preferir Transit-A na saída.
3. Simule retirada da rota A e confirme failover para B.
4. Em ambiente simulado, aplique prepend em um anúncio para B.
5. Compare as tabelas dos ASNs de laboratório e explique por que o resultado pode divergir.

## Exemplo de configuração
Exemplo conceitual de prepend em Cisco:
```cisco
route-map EXPORT-TRANSIT-B permit 10
 match ip address prefix-list ISP-OWNED
 set as-path prepend 64500 64500 64500
```
Aplique apenas ao vizinho pretendido e mantenha anúncios de prefixos autorizados. O exemplo não inclui a política completa de exportação.

## Comandos de verificação
```text
show ip bgp <prefixo>
show ip bgp neighbors <IP> advertised-routes
traceroute <destino-de-teste>
ping <destino-de-teste>

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- O aluno separa controle de saída e influência de entrada.
- O failover não depende de intervenção manual.
- Não se afirma que prepend garante caminho específico.

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
