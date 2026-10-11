# Módulo 07 — Trânsito IP e política de upstream

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Um contrato de trânsito pode oferecer rota default ou tabela completa, com diferentes regras de aceitação e anúncio. A política deve refletir o serviço contratado: não aceitar rotas sem necessidade, não anunciar rotas de terceiros sem autorização e não permitir que um cliente use seu AS como trânsito se isso não estiver acordado.

Para tabela completa, dimensione memória, CPU, convergência e FIB. `maximum-prefix` deve refletir o perfil esperado com margem controlada e alertas; um limite inadequado pode derrubar uma sessão. Filtros devem ser gerados de fontes confiáveis e atualizados com revisão.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Modele Transit-A e Transit-B.
2. Defina política de importação para default-only; compare conceitualmente com full table.
3. Configure exportação allow-list.
4. Simule recebimento de prefixo indevido e prove que o filtro o bloqueia.
5. Documente o limite de prefixos e o procedimento de alerta.

## Exemplo de configuração
Modelo Cisco parcial:
```cisco
router bgp 64500
 neighbor 10.0.0.1 remote-as 64501
 neighbor 10.0.0.1 maximum-prefix 100 80 restart 5
```
O valor 100 é meramente didático e inadequado como valor universal. Ajuste ao número de rotas esperado e à plataforma; confirme semântica de aviso, limiar e restart.

## Comandos de verificação
```text
show ip bgp summary
show ip bgp neighbors <IP>
show ip bgp neighbors <IP> advertised-routes
show logging

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Não há exportação irrestrita.
- Importação é específica para cada upstream.
- Existe procedimento para mudança de perfil default-only/full-table.
- O aluno explica o risco de max-prefix mal dimensionado.

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
