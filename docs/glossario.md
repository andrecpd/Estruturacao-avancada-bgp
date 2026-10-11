# Glossário BGP

- **AS/ASN:** sistema autônomo e seu número.
- **eBGP:** sessão entre AS diferentes.
- **iBGP:** sessão entre roteadores do mesmo AS.
- **NLRI:** informação de alcançabilidade anunciada pelo BGP.
- **RIB/FIB:** bases de rotas e encaminhamento; a rota BGP escolhida pode não ser instalada se houver conflito ou next-hop inválido.
- **LOCAL_PREF:** preferência de saída dentro do AS.
- **AS_PATH:** sequência de AS associada à rota.
- **MED:** atributo opcional usado para sugerir ponto de entrada a um AS vizinho, sujeito à política.
- **Community:** tag usada por políticas de roteamento.
- **Route leak:** anúncio indevido de rotas além da relação/política pretendida.
- **RPKI/ROA:** infraestrutura de chaves e autorização criptográfica de origem de prefixos.
- **Route Reflector:** mecanismo para escalar distribuição iBGP sem full mesh entre todos os roteadores.
- **MP-BGP:** extensões multiprotocolo para diferentes famílias de endereços/serviços.
