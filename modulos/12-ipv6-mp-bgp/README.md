# Módulo 12 — IPv6 e MP-BGP

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
BGP usa extensões multiprotocolo para transportar NLRI de diferentes famílias de endereços. IPv4 unicast e IPv6 unicast são ativados e filtrados separadamente em muitas plataformas. Uma sessão de transporte IPv4 pode carregar NLRI IPv6, dependendo da configuração; o next-hop precisa continuar resolvível.

IPv6 exige filtros equivalentes aos de IPv4, controle de prefixos, política de exportação e validação de origem. O prefixo de documentação `2001:db8::/32` serve para exemplos e não deve ser anunciado publicamente.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Ative address-family IPv6 unicast nos peers de laboratório.
2. Anuncie `2001:db8:100::/48` apenas dentro do laboratório.
3. Crie filtros IPv6 independentes.
4. Derrube a sessão/família IPv6 sem alterar a família IPv4, se suportado.
5. Compare rotas aprendidas e anunciadas por família.

## Exemplo de configuração
Cisco IOS/IOS XE ilustrativo:
```cisco
ipv6 prefix-list V6-OWNED seq 10 permit 2001:db8:100::/48
router bgp 64500
 address-family ipv6
  neighbor 2001:db8:ffff::1 activate
  neighbor 2001:db8:ffff::1 prefix-list V6-OWNED out
 exit-address-family
```
Adapte o endereço de peering, a família e o método de ativação à plataforma.

## Comandos de verificação
```text
show bgp ipv6 unicast summary
show bgp ipv6 unicast
show bgp ipv6 unicast neighbors <IP> advertised-routes

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- IPv4 continua funcional quando apenas a política IPv6 muda.
- O prefixo IPv6 é aceito e anunciado somente aos peers autorizados.
- O aluno explica diferenças entre transporte da sessão e família NLRI.

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
