# Módulo 15 — Alta disponibilidade: BFD, Graceful Restart e PIC

**Nível:** intermediário a avançado · **Trilha:** ISP / engenharia de roteamento

## Ementa
BFD, timers BGP, Graceful Restart, LLGR, PIC, ECMP/Add-Path conforme plataforma, redundância de RRs e riscos de stale routes.

## Conceitos essenciais
BFD pode detectar falhas de forwarding mais rapidamente que timers BGP, mas timers agressivos podem gerar instabilidade. Graceful Restart mantém rotas stale durante reinício sob condições específicas; isso melhora continuidade em alguns eventos e pode prolongar blackholes em outros. Verifique suporte e interoperabilidade antes de habilitar.

## Objetivos de aprendizagem
Ao concluir, o aluno deverá explicar os conceitos do módulo, interpretar a tabela BGP, aplicar políticas com segurança e registrar evidências reproduzíveis.

## Pré-requisitos e ambiente
- Conhecimento de IPv4/IPv6, sub-redes, roteamento IP e CLI de roteadores.
- Ambiente sugerido: Cisco CML, EVE-NG, GNS3 ou containerlab com FRRouting. A disponibilidade de comandos depende da imagem e licença.
- Use apenas endereços de documentação (RFC 5737 / RFC 3849) em laboratórios isolados. Não anuncie esses prefixos na Internet.

## Procedimento de laboratório
1. Salve o estado inicial e a configuração de cada nó.
2. Aplique uma alteração por vez e registre o comando executado.
3. Valide sessão, NLRI recebida, melhor caminho, tabela IP e anúncios enviados.
4. Faça um teste negativo para confirmar que a política bloqueia o que deve bloquear.
5. Reverta o laboratório e registre lições aprendidas.

## Segurança operacional
Não cole comandos diretamente em produção. Revise filtros inbound/outbound, janela de mudança, impacto, backup, plano de rollback e autorização de prefixos. A sintaxe apresentada é referência Cisco IOS/IOS XE e deve ser adaptada à versão/plataforma.

## Topologia de referência
Consulte [`../topologias/README.md`](../topologias/README.md) e os diagramas Mermaid associados. Adapte os nós ao cenário do módulo sem alterar os prefixos de documentação.

## Laboratório guiado
**Desafio:** Compare queda de sessão com e sem BFD em ambiente controlado; observe retirada de rotas e impacto. Documente trade-off de Graceful Restart.

### Passos
1. Implemente a topologia de referência e confirme conectividade IP entre vizinhos.
2. Configure o BGP e verifique que as sessões estão em `Established`.
3. Aplique a política específica deste módulo.
4. Colete saída dos comandos de verificação e compare com o resultado esperado.
5. Introduza uma falha controlada, identifique-a e restaure o serviço.

### Verificação
```text
show bfd neighbors; show ip bgp summary; show logging
```

### Resultado esperado
Descreva o que cada mecanismo protege e o que não protege; não prometa tempo de failover sem medições.

## Exercícios
1. Explique os conceitos do módulo com suas próprias palavras e identifique um risco operacional.
2. Proponha uma mudança de política e preveja o efeito na rota recebida, escolhida e anunciada.
3. Crie um caso negativo que deveria ser bloqueado. Como comprovaria que foi bloqueado?
4. Registre evidências, resultado, causa raiz e rollback em um relatório de laboratório.

## Checklist de conclusão
- [ ] Entendi os conceitos e os limites do recurso.
- [ ] Configurei o laboratório e guardei a configuração inicial/final.
- [ ] Validei a RIB BGP, a tabela IP e os anúncios ao peer.
- [ ] Testei uma condição negativa e documentei o rollback.

## Referências normativas e documentação
- RFC 4271 — Border Gateway Protocol 4.
- RFC 7454 — BGP Operations and Security.
- RFC 8212 — Default External BGP (eBGP) Route Propagation Behavior without Policies.
- Documentação oficial Cisco IOS/IOS XE correspondente à versão usada no laboratório.
