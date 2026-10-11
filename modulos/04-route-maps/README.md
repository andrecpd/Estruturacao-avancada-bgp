# Módulo 04 — Route-maps e políticas de importação/exportação

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Route-maps encadeiam cláusulas sequenciais de permit/deny e podem casar prefix-lists, AS-PATH, communities ou outros atributos. Em cláusulas permit, ações `set` modificam atributos. A ordem importa e uma rota que não corresponde a cláusulas permitidas pode ser negada ao final. Em políticas BGP, trate importação e exportação como controles separados.

Import policy: decide o que aceitar e como classificar as rotas recebidas. Export policy: decide o que anunciar a cada peer. Não confunda a política que seleciona a saída de pacotes com a política que influencia como outros AS alcançam seus prefixos.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Crie uma política de importação por upstream.
2. Classifique rotas do Transit-A com Local Preference maior.
3. Crie uma política de exportação que anuncie apenas prefixos próprios e de clientes autorizados.
4. Verifique o resultado antes e depois de aplicar a política.
5. Faça uma mudança deliberadamente incorreta no laboratório e diagnostique o deny implícito.

## Exemplo de configuração
Modelo:
```cisco
route-map TRANSIT-A-IN permit 10
 match ip address prefix-list ACCEPTED-FROM-A
 set local-preference 200
route-map TRANSIT-A-IN deny 100
!
router bgp 64500
 neighbor 10.0.0.1 route-map TRANSIT-A-IN in
```
Use a sintaxe adequada à address-family e à plataforma; valide a política efetiva após aplicar.

## Comandos de verificação
```text
show route-map
show ip bgp neighbors <IP> received-routes
show ip bgp neighbors <IP> routes
show ip bgp neighbors <IP> advertised-routes

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Políticas independentes por vizinho.
- Exportação em allow-list.
- Evidência de rotas recebidas e anunciadas.
- Explicação do efeito de cada sequência.

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
