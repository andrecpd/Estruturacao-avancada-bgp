# Objetivos e método do curso

## Competências finais
Ao concluir, o aluno será capaz de:
1. Explicar a máquina de estados BGP, atributos e processo de seleção.
2. Diferenciar política de importação, política de exportação e encaminhamento de pacotes.
3. Construir filtros por prefixo, comprimento, AS-PATH e comunidades.
4. Projetar uma política de trânsito IP com um ou mais upstreams.
5. Aplicar Local Preference para escolher a saída dentro do próprio AS.
6. Influenciar, sem garantir, a entrada de tráfego usando anúncios, prepend e communities aceitas pelo upstream.
7. Implementar multihoming, peering, route reflection e IPv6.
8. Aplicar controles de segurança como max-prefix, RPKI origin validation, IRR e filtros anti-bogon.
9. Fazer troubleshooting usando evidências da sessão, da RIB BGP, da RIB global e da FIB.
10. Versionar configurações e validar mudanças com revisão e rollback.

## Pré-requisitos
- IPv4 e subnetting; noções de IPv6.
- Roteamento estático e noções de IGP (OSPF/IS-IS).
- CLI de roteadores e conceitos de VLAN/interfaces.
- Familiaridade básica com Linux ajuda para Containerlab/FRR.

## Método de laboratório
Para cada experiência, anote:
- hipótese inicial;
- configuração aplicada;
- comando usado para observar o resultado;
- resultado esperado e resultado real;
- explicação técnica;
- procedimento de rollback.

## Segurança operacional
Não use sessões com roteadores reais da Internet para testes de anúncio. Use ASNs privados e prefixos reservados. Nunca aplique uma política de exportação sem confirmar exatamente quais prefixos serão anunciados.
