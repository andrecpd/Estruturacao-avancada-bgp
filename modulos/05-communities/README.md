# Módulo 05 — Communities: standard, extended e large

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Communities são etiquetas usadas para classificar rotas e aplicar políticas. Standard communities têm 32 bits; large communities oferecem três campos de 32 bits e são úteis para convenções de operadoras; extended communities são comuns em cenários como VPNs e outras sinalizações.

Uma community não executa uma ação por si só: o efeito depende da política local ou do upstream que a interpreta. Documente a semântica, o escopo, a propagação e quem pode definir cada etiqueta. Evite confiar em communities enviadas por clientes sem validação.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Defina um esquema didático de communities para rotas próprias, clientes e peers.
2. Marque as rotas recebidas de cada cliente.
3. Use a etiqueta para aplicar Local Preference ou selecionar a exportação.
4. Confirme se a community é preservada ou removida na saída conforme a política.
5. Documente quais communities seriam específicas de um upstream real; não invente valores de operadora.

## Exemplo de configuração
Exemplo conceitual Cisco:
```cisco
ip community-list standard CUSTOMER-ALPHA permit 64500:110
route-map CUSTOMER-IN permit 10
 set community 64500:110 additive
```
A sintaxe e o suporte variam. Para transmitir communities a um vizinho, confirme se a plataforma exige ativação explícita, por exemplo `send-community`.

## Comandos de verificação
```text
show ip bgp <prefixo>
show ip bgp community
show route-map
show ip bgp neighbors <IP> advertised-routes

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- O plano de communities está documentado.
- Uma rota marcada recebe o tratamento esperado.
- Communities não autorizadas de clientes são removidas ou sobrescritas conforme política.

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
