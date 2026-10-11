# Módulo 16 — Troubleshooting sistemático de BGP

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
O diagnóstico deve seguir camadas: interface e endereçamento; conectividade IP; TCP/179; estado da sessão; capacidades/famílias negociadas; filtros; atributos e melhor rota; reachability do next-hop; instalação na RIB/FIB; caminho de retorno e ACL/firewall.

Sessão Established sem rotas pode indicar ausência de anúncios, família não ativada, filtro, política de importação ou falta de prefixo elegível. Rota presente na tabela BGP mas ausente da RIB pode indicar next-hop inalcançável, rota concorrente preferida, política ou limitação da plataforma.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
Cenários:
1. Endereço de peer incorreto.
2. ASN remoto errado.
3. TCP/179 bloqueado.
4. Address-family não ativada.
5. Prefix-list bloqueando a rota.
6. Next-hop inalcançável.
7. Rota recebida, mas não anunciada devido à política de exportação.
Para cada caso, diagnostique antes de mudar a configuração.

## Exemplo de configuração
Roteiro:
```text
1. show interfaces / ping ao peer
2. show ip bgp summary
3. show ip bgp neighbors <IP>
4. inspecionar prefix-lists e route-maps
5. conferir rota e reachability do next-hop
6. verificar rotas anunciadas ao vizinho
7. testar tráfego e caminho de retorno
```

## Comandos de verificação
```text
show ip bgp summary
show ip bgp neighbors <IP>
show ip route <prefixo>
show ip cef <destino>
show logging

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Identificar a causa raiz com evidências.
- Evitar `clear ip bgp *` como primeira ação.
- Registrar a mudança mínima necessária e o rollback.

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
