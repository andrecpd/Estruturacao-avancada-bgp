# Módulo 02 — Seleção de rotas e atributos

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
O processo de melhor caminho compara rotas elegíveis segundo regras específicas da implementação e da configuração. Em Cisco, Weight é local ao roteador e não é atributo transmitido aos peers. Local Preference é usado dentro do AS e valores maiores normalmente são preferidos. AS-PATH mais curto costuma ser preferido em etapas posteriores, mas não deve ser tratado como regra universal isolada.

Origin, MED, preferência entre eBGP/iBGP, custo IGP até o next-hop, multipath e critérios de desempate podem afetar o resultado. A ordem exata varia entre fabricantes e pode ser alterada por configuração. MED costuma ser comparado entre rotas do mesmo AS vizinho, a menos que outras opções mudem esse comportamento.

A seleção BGP não é igual à escolha de rota global do sistema operacional: a rota BGP vencedora ainda precisa ser elegível para instalação na RIB e ter next-hop resolvido.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Anuncie o mesmo prefixo por dois peers.
2. Inspecione atributos recebidos.
3. Aplique Local Preference diferente às duas rotas.
4. Confirme a melhor rota e a rota instalada.
5. Retire a rota preferida e confirme a troca para a alternativa.
6. Repita usando prepend no AS de laboratório e compare o resultado.

## Exemplo de configuração
Exemplo de política de entrada Cisco:
```cisco
route-map TRANSIT-A-IN permit 10
 set local-preference 200
route-map TRANSIT-B-IN permit 10
 set local-preference 100
```
Aplique cada route-map somente ao vizinho correto, depois valide a rota recebida e a decisão efetiva. Evite usar esta política indiscriminadamente em produção.

## Comandos de verificação
```text
show ip bgp <prefixo>
show ip bgp <prefixo> longer-prefixes
show ip route <prefixo>
show route-map

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Prever qual rota vence antes de executar o comando.
- Explicar quais atributos são locais e quais são propagados.
- Demonstrar a alteração e o failover com evidências.

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
