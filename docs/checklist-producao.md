# Checklist antes de uma mudança BGP em produção

## Antes
- [ ] Escopo e objetivo da mudança aprovados.
- [ ] Prefixos próprios e de clientes conferidos.
- [ ] ASN de origem autorizado e IRR/ROA revisados.
- [ ] Política de importação e exportação revisada por segundo operador.
- [ ] Estado atual salvo (configuração e saídas dos comandos de verificação).
- [ ] Impacto de `clear`/soft reset compreendido.
- [ ] Plano de rollback testado ou descrito.
- [ ] Janela, contatos e critérios de abortar definidos.

## Durante
- [ ] Confirmar sessão e contadores.
- [ ] Verificar rotas aceitas, melhores rotas e rotas instaladas.
- [ ] Verificar anúncios recebidos pelo vizinho, quando houver looking glass ou confirmação do peer.
- [ ] Testar conectividade de vários destinos.
- [ ] Monitorar tráfego, perda, latência e alertas.

## Depois
- [ ] Comparar estado final com o esperado.
- [ ] Registrar evidências e diferenças.
- [ ] Atualizar documentação e repositório.
- [ ] Fechar a mudança apenas quando os critérios de aceite forem atendidos.
