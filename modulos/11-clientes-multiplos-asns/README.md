# Módulo 11 — Clientes BGP e múltiplos ASNs

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
A borda de ISP precisa distinguir rotas próprias, rotas de clientes, peers e trânsito. Para cada cliente, mantenha lista de prefixos autorizados, ASN esperado, communities aceitas, limites de anúncios e política de exportação. O padrão seguro é anunciar somente rotas contratadas e impedir que um cliente se torne trânsito não intencional para outro.

Valide AS-PATH e origem quando apropriado, mas não dependa de um único atributo para impedir vazamentos. Clientes podem anunciar indevidamente default, full table ou prefixos de terceiros; filtros explícitos são necessários.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Crie dois clientes com ASNs diferentes.
2. Autorize um prefixo para cada cliente.
3. Confirme que Alpha não recebe rotas privadas de Beta.
4. Faça Alpha anunciar um prefixo não autorizado e confirme bloqueio.
5. Teste uma tentativa de anunciar default e documente a resposta da política.

## Exemplo de configuração
Exemplo de exportação:
```cisco
ip prefix-list ALPHA-OUT seq 10 permit 203.0.113.0/24
route-map TO-ALPHA permit 10
 match ip address prefix-list ALPHA-OUT
route-map TO-ALPHA deny 100
```
O exemplo permite apenas o prefixo indicado; adicione rotas de clientes autorizadas somente se o contrato exigir.

## Comandos de verificação
```text
show ip bgp neighbors <IP> routes
show ip bgp neighbors <IP> advertised-routes
show ip prefix-list
show route-map

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Cada cliente tem política individual.
- Prefixos indevidos não são aceitos nem reanunciados.
- O aluno mostra evidência de anúncios por vizinho.

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
