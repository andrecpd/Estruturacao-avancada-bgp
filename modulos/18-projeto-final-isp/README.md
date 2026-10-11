# Módulo 18 — Projeto final: ISP multihomed

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
O projeto integra as competências do curso em uma rede fictícia: AS64500 com duas bordas, Transit-A AS64501, Transit-B AS64502, Peer-LAB AS64520, Cliente Alpha AS64510 e Cliente Beta AS64530. O objetivo é criar política coerente de import/export, engenharia de tráfego, segurança e contingência.

O projeto deve refletir requisitos de negócio: qual rota deve ser preferida, quais prefixos cada vizinho pode anunciar, quais prefixos podem ser exportados, como o tráfego deve reagir a falhas e quais evidências demonstram o comportamento. A arquitetura é mais importante do que copiar comandos isolados.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
Entregáveis:
1. Diagrama lógico e físico.
2. Plano IPv4/IPv6 e tabela de ASN.
3. Política de importação por vizinho.
4. Política de exportação por vizinho.
5. Plano de communities.
6. Preferência de saída e estratégia de entrada.
7. Filtros, max-prefix e plano RPKI/IRR.
8. Testes de falha de sessão, link e next-hop.
9. Relatório de troubleshooting com um erro injetado.
10. Plano de rollback e README para reproduzir o lab.

## Exemplo de configuração
A configuração completa deve ser construída a partir das políticas dos módulos anteriores. Antes de habilitar sessões, revise todas as exportações em modo offline. Não anuncie prefixos de documentação em peers reais. Faça revisão por pares e teste cada falha de forma isolada.

## Comandos de verificação
```text
Evidências mínimas:
- estado das sessões;
- rotas recebidas por vizinho;
- melhor rota e atributos;
- rotas anunciadas por vizinho;
- tabela global/FIB;
- conectividade antes/depois de falhas;
- logs e relatório de causa raiz.

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
Rubrica (100 pontos):
- Arquitetura e endereçamento: 10
- Import/export e filtros: 20
- Communities e engenharia de tráfego: 15
- Multihoming e failover: 15
- Segurança: 15
- IPv6: 5
- Troubleshooting com evidências: 10
- Documentação e Git: 10

Aprovação recomendada: 80/100 e nenhum vazamento crítico de rotas no teste final.

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
