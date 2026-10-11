# Módulo 15 — Alta disponibilidade e convergência

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
A convergência depende da detecção de falha, processamento BGP, instalação de rotas e atualização da FIB. BFD pode detectar falhas rapidamente, mas timers agressivos podem causar instabilidade. Graceful Restart tenta preservar encaminhamento durante reinício de plano de controle, porém pode manter rotas obsoletas em certas falhas. PIC, Add-Path e multipath são recursos dependentes de plataforma e arquitetura.

Planeje objetivos mensuráveis: tempo de detecção, tempo para nova rota ativa, perda de pacotes e comportamento durante falha de interface, sessão, roteador e next-hop. Não ative recursos de alta disponibilidade sem entender suas condições e limitações.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Meça convergência sem BFD.
2. Habilite BFD apenas se suportado em ambos os lados.
3. Simule falha de interface e falha de sessão separadamente.
4. Registre tempo até nova rota e perda de pacotes.
5. Avalie se Graceful Restart seria apropriado para cada tipo de falha.

## Exemplo de configuração
Plano de teste:
```text
T0: iniciar ping/traceroute contínuo
T1: derrubar interface ou sessão
T2: registrar detecção de falha
T3: registrar seleção/instalação de rota alternativa
T4: medir recuperação de tráfego
Repetir 3 vezes e comparar os resultados.
```

## Comandos de verificação
```text
show ip bgp summary
show bfd neighbors
show interfaces
show ip route
show logging

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Métricas são registradas.
- O aluno explica a diferença entre detecção e convergência.
- Timers não são alterados sem uma hipótese e plano de reversão.

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
