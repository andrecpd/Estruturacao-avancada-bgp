# Módulo 02 — Seleção de rotas e atributos

**Nível:** intermediário a avançado · **Trilha:** ISP / engenharia de roteamento

## Ementa
Weight (Cisco), LOCAL_PREF, locally originated, AS_PATH, ORIGIN, MED, eBGP/iBGP, IGP metric até next-hop, multipath e desempates finais.

## Conceitos essenciais
A seleção depende da implementação e da configuração. No Cisco IOS/IOS XE, Weight é local ao roteador e não é propagado; LOCAL_PREF influencia a saída dentro do AS; AS_PATH ajuda políticas inter-AS; MED é uma sugestão comparativa geralmente limitada a rotas do mesmo AS vizinho. Não trate a ordem de desempate como universal entre fabricantes/versões.

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
**Desafio:** Receba o mesmo prefixo por dois upstreams. Ajuste LOCAL_PREF para preferir o provedor A; depois use prepend no anúncio de saída para testar o efeito na preferência de entrada.

### Passos
1. Implemente a topologia de referência e confirme conectividade IP entre vizinhos.
2. Configure o BGP e verifique que as sessões estão em `Established`.
3. Aplique a política específica deste módulo.
4. Colete saída dos comandos de verificação e compare com o resultado esperado.
5. Introduza uma falha controlada, identifique-a e restaure o serviço.

### Verificação
```text
show ip bgp 203.0.113.0; show ip bgp; show ip route 203.0.113.0
```

### Resultado esperado
Documente o caminho antes/depois e diferencie controle de tráfego de saída (LOCAL_PREF) e influência de entrada (AS_PATH prepend, MED, mais específicos).

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
