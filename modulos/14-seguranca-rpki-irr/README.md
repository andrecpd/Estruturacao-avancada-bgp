# Módulo 14 — Segurança: RPKI, IRR, filtros e sessões

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
A segurança BGP começa por limitar o que se aceita e anuncia. Controles comuns incluem prefix-lists, filtros anti-bogon, AS-PATH filters, max-prefix, autenticação de sessão quando suportada, GTSM/TTL security em cenários adequados e proteção do plano de controle.

RPKI Route Origin Validation compara prefixo, comprimento e ASN de origem com ROAs válidos. Estados típicos: Valid, Invalid e NotFound. ROV não valida todo o AS-PATH e não substitui filtros de exportação. IRR pode apoiar geração de filtros, mas a qualidade e atualização dos objetos variam. Documente política para Invalid/NotFound e processo de exceção.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Monte uma política de importação com prefixos autorizados.
2. Configure limite de prefixos adequado ao tamanho simulado.
3. Classifique exemplos como Valid, Invalid e NotFound usando dados didáticos.
4. Rejeite o anúncio Invalid conforme política do exercício.
5. Documente exceções e monitoração sem desativar globalmente a validação.

## Exemplo de configuração
Checklist conceitual:
```text
1. Validar origem e comprimento com RPKI/ROA.
2. Aplicar política documentada a Invalid.
3. Tratar NotFound segundo política local.
4. Manter filtros de prefixos e ASNs independentes.
5. Monitorar max-prefix e alterações de vizinhança.
```
A configuração de cache RPKI e políticas varia por plataforma e software.

## Comandos de verificação
```text
show ip bgp
show ip bgp neighbors <IP>
show logging
# Em FRR, use os comandos de RPKI/ROV disponíveis na versão instalada.

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Exportação é allow-list.
- O aluno diferencia RPKI origin validation de validação de caminho completo.
- Há plano para monitorar mudanças de estado e atualizar filtros.

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
