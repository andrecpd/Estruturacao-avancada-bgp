# Glossário BGP

- **AS / ASN:** Sistema Autônomo / número que identifica um sistema de roteamento.
- **eBGP:** sessão entre sistemas autônomos diferentes.
- **iBGP:** sessão entre roteadores do mesmo AS.
- **NLRI:** informação de alcançabilidade anunciada, como prefixos.
- **RIB:** base de informações de roteamento.
- **FIB:** estrutura usada para encaminhar pacotes no plano de dados.
- **Local Preference:** atributo usado dentro de um AS para influenciar a saída; maior costuma ser preferido.
- **AS-PATH:** sequência de ASNs atravessados; usado para prevenção de loops e como atributo de seleção.
- **MED:** sinal opcional para indicar preferência de entrada entre pontos de interconexão com o mesmo AS vizinho; comportamento depende da política e implementação.
- **Community:** etiqueta associada à rota para classificação e aplicação de políticas.
- **Route leak:** propagação de rotas além do escopo pretendido.
- **RPKI origin validation:** valida se o ASN de origem e o comprimento do prefixo são autorizados por um ROA.
- **IRR:** registros de roteamento usados como fonte para construir filtros, com qualidade variável.
- **Upstream / trânsito IP:** rede que fornece conectividade para destinos além dos peers diretos.
- **Peering:** troca de tráfego entre redes conforme política/acordo, sem significar necessariamente trânsito global.
- **Route Reflector:** mecanismo para reduzir a necessidade de full mesh iBGP.
