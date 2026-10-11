# Estruturação Avançada de BGP — curso prático para ISP

Curso em português para estudo intermediário/avançado de BGP, com foco em operação de ISP, trânsito, multihoming, peering, políticas, communities, segurança, IPv6, alta disponibilidade e troubleshooting.

> **Aviso:** material educacional. Exemplos usam ASNs e prefixos reservados para documentação; não os anuncie na Internet. A sintaxe varia por fabricante/versão. Todo laboratório deve ser validado antes de qualquer uso operacional.

## Comece aqui
- [Índice dos 18 módulos](./modulos/README.md)
- [Topologias e endereçamento](./topologias/README.md)
- [Catálogo de laboratórios](./labs/README.md)
- [Configurações Cisco IOS/IOS XE](./configuracoes/cisco-ios/)
- [Exemplo FRRouting](./configuracoes/frr/ebgp-basico.md)
- [Glossário](./docs/glossario.md)
- [Metodologia e avaliação](./docs/metodologia.md)

## Trilha de aprendizagem
1. Fundamentos, FSM e sessão BGP.
2. Seleção de rotas e atributos.
3. Filtros e políticas.
4. Communities e engenharia de tráfego.
5. Trânsito, multihoming e IXP.
6. iBGP, route reflectors, clientes e IPv6.
7. VRF/MPLS VPN, segurança, alta disponibilidade e troubleshooting.
8. Automação e projeto final ISP.

## Como estudar
Para cada módulo, desenhe a topologia, configure a sessão, verifique rotas recebidas/escolhidas/anunciadas, crie um teste negativo, simule uma falha e registre rollback. Não valide apenas o estado `Established`: confirme a política e a tabela de encaminhamento.

## Estrutura do repositório
```text
modulos/                 Conteúdo didático em 18 módulos
topologias/              Diagramas Mermaid e plano de endereçamento
labs/                    Catálogo de experiências práticas
configuracoes/cisco-ios/ Exemplos Cisco IOS/IOS XE
configuracoes/frr/       Exemplo FRRouting
exercicios/              Orientação para avaliações
gabaritos/               Orientação para gabaritos por versão
docs/                    Glossário e metodologia
scripts/                 Reservado para automação e validações futuras
```

## Referências-base
- RFC 4271 — BGP-4.
- RFC 7454 — BGP Operations and Security.
- RFC 8212 — Default External BGP (eBGP) Route Propagation Behavior without Policies.
- RFC 9234 — Route Leak Prevention and Detection Using Roles in BGP.
- Documentação oficial da plataforma usada no laboratório.

## Status do material
O repositório contém uma base didática ampliada e exemplos iniciais. Ainda é necessário executar cada laboratório na imagem e versão escolhidas, capturar saídas reais e revisar os exemplos específicos de plataforma antes de considerá-los testados.
