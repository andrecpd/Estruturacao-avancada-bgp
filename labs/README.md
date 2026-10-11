# Laboratórios práticos

## Laboratório 1 — eBGP básico
- Dois roteadores em ASNs privados.
- Estabelecer sessão, anunciar um prefixo e validar.
- Falha induzida: ASN remoto incorreto.

## Laboratório 2 — Importação e Local Preference
- Dois upstreams anunciam o mesmo prefixo.
- Definir preferência de saída.
- Retirar a rota preferida e observar failover.

## Laboratório 3 — Exportação em allow-list
- Anunciar somente prefixos autorizados.
- Tentar anunciar prefixo de teste não autorizado.
- Confirmar bloqueio no vizinho simulado.

## Laboratório 4 — Communities
- Marcar rotas de cliente e aplicar política baseada na etiqueta.
- Verificar preservação/remoção conforme desenho.

## Laboratório 5 — Multihoming
- Dois upstreams e um AS de cliente.
- Medir comportamento de falha de link, sessão e next-hop.

## Laboratório 6 — Peering
- Adicionar peer simulado e preferir sua rota para o prefixo acordado.
- Retirar o anúncio e confirmar uso do trânsito.

## Laboratório 7 — RPKI e filtros
- Usar estados didáticos Valid/Invalid/NotFound.
- Aplicar política documentada e verificar logs.

## Laboratório 8 — Troubleshooting
- Injetar um erro por vez: família desativada, filtro incorreto, next-hop sem reachability.
- Identificar causa antes de alterar configuração.

## Laboratório 9 — Projeto final
- Integrar os módulos e entregar evidências.
