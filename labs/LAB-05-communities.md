# LAB-05 — Communities como interface de política

**Objetivo:** marcar rotas no ingresso e aplicar ação no egresso.

## Modelo didático de tags
Use valores reservados ao laboratório e documente-os; não reutilize communities de provedores reais sem autorização. Exemplo interno: `65010:100` = cliente; `65010:200` = preferência alta; `65010:300` = solicitar prepend no upstream de teste.

## Tarefas
1. Marque a rota do cliente com uma community.
2. Confirme a tag na tabela BGP.
3. Faça a route-map de saída casar a tag e aplicar a ação definida.
4. Compare anúncio sem tag e com tag.
5. Verifique se a tag deve ser propagada ou removida na fronteira.

## Perguntas
- Qual a diferença entre standard e large communities?
- Por que `additive` pode ser importante?
- Como impedir que o cliente injete uma community reservada para uso interno?
