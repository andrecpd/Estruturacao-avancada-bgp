# Estruturação Avançada de BGP
### Curso prático do nível intermediário ao avançado — ISP, trânsito IP, peering e multihoming

> Material educacional independente. Os exemplos usam ASNs privados e endereços reservados para documentação/laboratório. Não copie configurações para produção sem revisão, adaptação à plataforma e plano de mudança.

## Objetivo
Formar o aluno para projetar, implementar, validar e solucionar problemas BGP em redes com múltiplos upstreams, clientes BGP, peering, políticas de importação/exportação, communities, IPv4/IPv6, segurança de roteamento e alta disponibilidade.

## Para quem
- Profissionais de redes com fundamentos de IPv4/IPv6 e roteamento estático.
- Operadores de ISP, NOC, equipes de backbone e engenharia de tráfego.
- Administradores que precisam entender políticas BGP e multihoming.

## Como estudar
Em cada módulo, siga a sequência:
1. Leia `teoria.md`.
2. Desenhe a topologia e confira o plano de endereçamento.
3. Execute o laboratório em ambiente isolado.
4. Registre os resultados dos comandos de verificação.
5. Faça os desafios sem consultar a solução.
6. Só avance quando os critérios de aceite forem atendidos.

## Trilha de módulos

| # | Módulo | Resultado esperado |
|---|---|---|
| 01 | Fundamentos e sessão BGP | Explicar e estabelecer eBGP/iBGP |
| 02 | Seleção de rotas e atributos | Prever qual rota será escolhida |
| 03 | Prefix-lists e filtros | Controlar os prefixos aceitos/anunciados |
| 04 | Route-maps e políticas | Implementar políticas de import/export |
| 05 | Communities | Classificar rotas e acionar políticas |
| 06 | Engenharia de tráfego | Controlar saída e influenciar entrada |
| 07 | Trânsito IP | Construir política segura para upstreams |
| 08 | Multihoming e failover | Projetar borda redundante |
| 09 | IX.br e peering | Separar peering de trânsito |
| 10 | iBGP e Route Reflectors | Escalar o plano de controle interno |
| 11 | Clientes e múltiplos ASNs | Aplicar políticas por cliente |
| 12 | IPv6 e MP-BGP | Operar famílias IPv4 e IPv6 |
| 13 | VRF e VPNv4/VPNv6 | Entender isolamento e L3VPN |
| 14 | Segurança, RPKI e IRR | Reduzir risco de anúncios inválidos |
| 15 | Alta disponibilidade | Planejar convergência e recuperação |
| 16 | Troubleshooting | Diagnosticar falhas sistematicamente |
| 17 | Automação e Git | Validar mudanças antes de implantar |
| 18 | Projeto final de ISP | Integrar os conceitos num cenário completo |

## Laboratório recomendado
- **FRRouting + Containerlab** para laboratórios reproduzíveis e multiplataforma.
- **EVE-NG/GNS3** para imagens virtuais de fabricantes, respeitando licenciamento.
- Roteadores físicos apenas em janela controlada e com plano de rollback.

## Topologia de referência
- `AS64500`: ISP do aluno.
- `AS64501`: Transit-A.
- `AS64502`: Transit-B.
- `AS64510`: cliente Alpha.
- `AS64520`: peer de laboratório.
- `AS64530`: cliente Beta.
- `203.0.113.0/24`, `198.51.100.0/24` e `192.0.2.0/24`: prefixos de documentação.
- `2001:db8::/32`: prefixo IPv6 reservado para documentação.

Os ASNs 64512–65534 são privados de 16 bits; os ASNs e prefixos usados aqui são apenas exemplos. Não anuncie prefixos de documentação na Internet pública.

## Política de referência
- Anúncios de saída são **allow-list**: anunciar apenas prefixos próprios e de clientes explicitamente autorizados.
- Aplicar filtros de entrada por vizinho.
- Definir `maximum-prefix` conforme o contrato e o perfil real do vizinho.
- Não presumir que prepend, MED ou communities garantam um caminho de entrada específico.
- Manter política IPv4 e IPv6 revisadas separadamente.
- Validar RPKI/IRR e manter processo de exceção documentado.

## Critérios de conclusão
O aluno deverá demonstrar: sessões estáveis, filtros efetivos, políticas de preferência, anúncios corretos, ausência de vazamento entre clientes, failover validado, evidências de segurança e documentação de mudança.

## Aviso
Os comandos variam por versão e fabricante. Os exemplos Cisco IOS/IOS XE não são necessariamente compatíveis com IOS XR, NX-OS, Juniper Junos ou FRR. Teste em laboratório e consulte a documentação da plataforma.
# Estruturacao-avancada-bgp
