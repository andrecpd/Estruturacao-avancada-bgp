# Módulo 09 — IX.br, route servers e peering

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Peering é uma relação de troca de tráfego com política definida; trânsito fornece alcançabilidade para destinos além dos peers. Em um IXP, uma sessão com route server normalmente facilita a troca de rotas entre participantes, mas o route server não deve ser confundido com o caminho de dados. Cada participante continua responsável por sua política.

Separe políticas de importação e exportação para trânsito, peering bilateral e route server. Aceite apenas rotas que atendam às regras do IXP e aos acordos. Use documentação atual do IX e de cada peer para communities e requisitos técnicos; não assuma valores universais.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Adicione um AS peer de laboratório.
2. Anuncie apenas prefixos próprios/cliente autorizados.
3. Faça o peer anunciar um prefixo de teste.
4. Configure preferência de saída para o peer sobre trânsito para esse prefixo.
5. Simule a retirada do anúncio e confirme retorno ao trânsito.

## Exemplo de configuração
Política conceitual:
```text
IMPORT-PEER:
  aceitar prefixos autorizados do peer
  atribuir Local Preference de acordo com a política local
  rejeitar o restante

EXPORT-PEER:
  anunciar apenas prefixos próprios e rotas de clientes elegíveis
  não exportar rotas de outros peers/trânsitos sem acordo
```
Implemente a lógica com prefix-lists, AS-PATH e route-maps na plataforma escolhida.

## Comandos de verificação
```text
show ip bgp summary
show ip bgp <prefixo>
show ip bgp neighbors <IP> advertised-routes
traceroute <destino>

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- O tráfego para o prefixo do peer prefere peering.
- O peer não recebe default ou full routes sem acordo explícito.
- A política de exportação é diferente da política de trânsito.

## Perguntas de revisão
1. Qual problema operacional este recurso resolve?
2. Qual seria o risco de aplicá-lo sem filtros ou política explícita?
3. Que evidência comprova que a configuração funcionou?
4. Como o comportamento muda quando um peer ou next-hop falha?

## Registro de evidências
Preencha no seu caderno ou em `evidencias/`:
- Data e versão do software:
- Topologia:
- Configuração aplicada:
- Comandos e saídas:
- Resultado esperado:
- Resultado observado:
- Problemas encontrados:
- Rollback:
