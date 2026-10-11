# Topologia e plano de endereçamento

## ASNs de laboratório
| Sistema | ASN | Função |
|---|---:|---|
| ISP-LAB | 64500 | AS do aluno |
| Transit-A | 64501 | Upstream preferencial de exemplo |
| Transit-B | 64502 | Upstream secundário |
| Cliente Alpha | 64510 | Cliente BGP |
| Peer-LAB | 64520 | Peer bilateral de exemplo |
| Cliente Beta | 64530 | Segundo cliente |

## Prefixos de documentação
| Prefixo | Uso no laboratório |
|---|---|
| 203.0.113.0/24 | Prefixo próprio fictício do ISP |
| 198.51.100.0/24 | Rede fictícia do Cliente Alpha |
| 192.0.2.0/24 | Rede fictícia do Cliente Beta |
| 2001:db8:100::/48 | Prefixo IPv6 fictício do ISP |
| 2001:db8:10::/48 | Prefixo IPv6 fictício do Cliente Alpha |

## Links de exemplo
| Link | Lado A | Lado B | Sub-rede |
|---|---|---|---|
| ISP Edge-1 — Transit-A | 192.0.2.0/31 (substituir se conflitar com exemplos de prefixos) | — | Use uma sub-rede de enlace exclusiva em sua implementação |
| ISP Edge-2 — Transit-B | — | — | Use uma sub-rede de enlace exclusiva |
| Edge-1 — Edge-2 | — | — | Use loopbacks e IGP ou enlaces dedicados para iBGP |

**Importante:** os prefixos reservados para documentação não devem ser usados como endereços de enlace reais em redes conectadas à Internet. Escolha blocos de laboratório separados, por exemplo `10.0.0.0/8` e `fd00::/8`, para endereçamento interno.

## Diagrama lógico
```text
                AS64501 Transit-A
                       |
                    eBGP
                       |
             +-------------------+
             | ISP-LAB AS64500   |
             | Edge-1 --- Edge-2 |
             |   iBGP / IGP      |
             +-------------------+
                       |
                    eBGP
                       |
                AS64502 Transit-B

          Edge(s) também conectam a:
       Peer-LAB AS64520 / Clientes AS64510,64530
```
