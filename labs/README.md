# Trilha progressiva de BGP — do básico ao avançado

A trilha foi organizada para que cada laboratório reutilize os conceitos do anterior. **Siga a ordem LAB-01 → LAB-06**: primeiro estabeleça conectividade e sessões; depois tome decisões de roteamento; em seguida proteja os anúncios; por fim aplique políticas avançadas e faça troubleshooting integrado.

## Como estudar cada laboratório

1. Leia o objetivo, pré-requisitos e topologia antes de configurar.
2. Monte o cenário no EVE-NG ou GNS3 e confirme interfaces, endereços e ASNs.
3. Valide a conectividade IP antes de iniciar o BGP.
4. Use o padrão Cisco IOS/IOS XE com `address-family ipv4` para ativar vizinhos e aplicar políticas IPv4.
5. Execute primeiro o cenário esperado; depois faça os testes negativos e registre a evidência.
6. Não avance até conseguir explicar o resultado de cada comando e recuperar o cenário sem copiar cegamente o gabarito.

## Fase 1 — Fundamentos e políticas essenciais

| Ordem | Nível | Competência | Topologia | Guia |
|---|---|---|---|---|
| LAB-01 | Básico | eBGP, ASN, sessão TCP/179, `network`, tabela BGP | [SVG](../topologias/lab-01.svg) | [Abrir laboratório](LAB-01-ebgp-basico.md) |
| LAB-02 | Básico–intermediário | Multihoming e seleção de saída com LOCAL_PREF | [SVG](../topologias/lab-02.svg) | [Abrir laboratório](LAB-02-local-pref.md) |
| LAB-03 | Intermediário | Prefix-list e filtragem de anúncios recebidos | [SVG](../topologias/lab-03.svg) | [Abrir laboratório](LAB-03-prefix-filtering.md) |
| LAB-04 | Intermediário | Política de exportação e prevenção de route leak | [SVG](../topologias/lab-04.svg) | [Abrir laboratório](LAB-04-route-leak.md) |
| LAB-05 | Intermediário–avançado | Communities, route-map e AS-path prepend | [SVG](../topologias/lab-05.svg) | [Abrir laboratório](LAB-05-communities.md) |
| LAB-06 | Avançado inicial | Troubleshooting integrado por camadas | [SVG](../topologias/lab-06.svg) | [Abrir laboratório](LAB-06-troubleshooting.md) |

## Fase 2 — Próximos laboratórios recomendados

Estes módulos compõem a continuação sugerida da trilha. Ainda precisam ser criados como guias completos com topologias, configurações, validação, falhas intencionais e gabarito.

| Ordem | Nível sugerido | Tema | O que acrescenta |
|---|---|---|---|
| LAB-07 | Intermediário–avançado | AS-path filtering e regex | Filtrar origens e caminhos por expressão regular |
| LAB-08 | Avançado | MED, weight e desempate BGP | Comparar atributos e ordem de seleção de rotas |
| LAB-09 | Avançado | Engenharia de tráfego inbound/outbound | Combinar LOCAL_PREF, prepend, MED e communities |
| LAB-10 | Avançado | Dois clientes e dois upstreams | Políticas separadas por vizinho e prevenção de trânsito indevido |
| LAB-11 | Avançado | Route reflectors e iBGP | Escalar o plano de controle dentro do AS |
| LAB-12 | Avançado | BGP multipath e redundância | ECMP, convergência e caminhos redundantes |
| LAB-13 | Avançado | Agregação de prefixos | `aggregate-address`, summary-only e controle de mais específicos |
| LAB-14 | Avançado | Segurança de roteamento | Prefixos bogon, max-prefix, filtros e higiene de sessão |
| LAB-15 | Avançado | IPv6 e MP-BGP | `address-family ipv6`, vizinhos e políticas IPv6 |
| LAB-16 | Projeto final | ISP multihomed integrado | Dois trânsitos, cliente, communities, filtros, redundância e troubleshooting |

## Critério para concluir um laboratório

- A topologia e o endereçamento estão documentados.
- Todas as sessões esperadas ficam em `Established`.
- Os prefixos corretos são recebidos, selecionados e instalados na tabela de roteamento.
- Os prefixos não autorizados são bloqueados.
- A política de saída é confirmada com comandos de advertised-routes, quando suportados pela imagem.
- O aluno consegue explicar a causa e a correção de pelo menos uma falha.

> Use prefixos de documentação (RFC 5737) apenas em laboratório. As imagens e configurações devem ser validadas na versão de IOS/IOS XE usada no EVE-NG/GNS3; alguns comandos variam por plataforma.
