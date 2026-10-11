# Módulo 08 — Multihoming, redundância e failover

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Multihoming conecta um AS a mais de um provedor ou ponto de interconexão. O desenho pode usar um ou vários roteadores de borda, circuitos independentes, iBGP e IGP. Redundância de sessão não equivale necessariamente a redundância física: circuitos podem compartilhar dutos, energia, POP ou equipamento.

A política de saída costuma usar Local Preference; multipath/ECMP pode distribuir fluxos quando a plataforma e os atributos permitem. O caminho de retorno pode ser assimétrico. Planeje a falha de interface, sessão BGP, roteador, next-hop, circuito e upstream, não apenas uma única condição.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Monte dois upstreams e duas bordas (ou simule duas sessões no mesmo roteador).
2. Defina Transit-A como preferido para saída.
3. Desligue a interface, depois derrube apenas a sessão BGP, comparando resultados.
4. Simule perda de reachability do next-hop.
5. Registre tempo de convergência e tráfego perdido.

## Exemplo de configuração
Política de preferência de saída:
```cisco
route-map TRANSIT-A-IN permit 10
 set local-preference 200
route-map TRANSIT-B-IN permit 10
 set local-preference 100
```
Aplique com filtros de importação apropriados. A preferência por A só funciona para rotas elegíveis e comparáveis.

## Comandos de verificação
```text
show ip bgp summary
show ip route
show ip cef <destino>
show interfaces
traceroute <destino>

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- A conectividade se recupera após cada falha planejada.
- O aluno identifica falhas de plano de controle versus plano de dados.
- O desenho não depende de um único equipamento quando o objetivo exige redundância física.

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
