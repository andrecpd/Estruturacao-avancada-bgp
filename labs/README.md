# Catálogo de laboratórios BGP

Este diretório contém os seis laboratórios com configuração Cisco IOS/IOS XE disponível atualmente. Cada guia inclui objetivo, topologia visual, explicação do conceito, configurações por roteador, tarefas e comandos de validação.

| Lab | Objetivo principal | Topologia | Guia |
|---|---|---|---|
| LAB-01 | Estabelecer eBGP e anunciar prefixos | [SVG](../topologias/lab-01.svg) | [Abrir](LAB-01-ebgp-basico.md) |
| LAB-02 | Selecionar saída com LOCAL_PREF | [SVG](../topologias/lab-02.svg) | [Abrir](LAB-02-local-pref.md) |
| LAB-03 | Filtrar prefixos autorizados | [SVG](../topologias/lab-03.svg) | [Abrir](LAB-03-prefix-filtering.md) |
| LAB-04 | Evitar route leak entre upstreams | [SVG](../topologias/lab-04.svg) | [Abrir](LAB-04-route-leak.md) |
| LAB-05 | Aplicar communities e prepend | [SVG](../topologias/lab-05.svg) | [Abrir](LAB-05-communities.md) |
| LAB-06 | Diagnosticar falhas BGP | [SVG](../topologias/lab-06.svg) | [Abrir](LAB-06-troubleshooting.md) |

## Método recomendado para cada laboratório
1. Estude o desenho e confirme o inventário dos roteadores, ASNs e endereços.
2. Configure interfaces e valide a conectividade IP antes de configurar BGP.
3. Configure vizinhos e família IPv4 usando `address-family ipv4`.
4. Valide a sessão com `show ip bgp summary`; depois confira rotas recebidas, melhor caminho e anúncios.
5. Faça o teste negativo indicado, colete evidências e aplique rollback.

> Os módulos LAB-07 a LAB-16 ainda precisam ser criados como guias individuais. Os desenhos SVG são editáveis e versionados em `topologias/`.
