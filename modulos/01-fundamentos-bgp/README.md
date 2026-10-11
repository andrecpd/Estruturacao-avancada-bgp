# Módulo 01 — Fundamentos e sessão BGP

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
BGP é um protocolo de roteamento interdomínio baseado em políticas. Ao contrário de um IGP, seu objetivo não é simplesmente escolher o caminho de menor custo; ele permite que cada AS aplique regras comerciais, operacionais e de segurança ao intercâmbio de alcançabilidade.

Uma sessão BGP usa TCP/179. A máquina de estados inclui Idle, Connect, Active, OpenSent, OpenConfirm e Established. Established indica que a sessão foi formada, mas não garante que existam rotas úteis ou que o encaminhamento esteja correto.

Mensagens essenciais: OPEN negocia parâmetros; KEEPALIVE mantém a sessão; UPDATE anuncia e retira NLRI e atributos; NOTIFICATION encerra a sessão em condições de erro; ROUTE-REFRESH solicita reavaliação de rotas quando suportado.

eBGP conecta ASNs diferentes. iBGP distribui rotas dentro do mesmo AS e tem regras próprias de propagação: uma rota aprendida por iBGP normalmente não é anunciada a outro peer iBGP, salvo mecanismos como Route Reflector. O next-hop precisa ser alcançável para a rota ser utilizável.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Crie dois roteadores FRR/Cisco em ASNs privados diferentes.
2. Configure endereçamento IP e confirme ping entre os endereços de peering.
3. Configure eBGP nos dois lados.
4. Anuncie um prefixo de laboratório que exista na tabela de roteamento.
5. Verifique o estado da sessão e a rota aprendida.
6. Derrube a interface e observe o estado; restaure e observe a recuperação.

## Exemplo de configuração
Cisco IOS/IOS XE (modelo ilustrativo):
```cisco
router bgp 64500
 bgp log-neighbor-changes
 neighbor 10.0.0.1 remote-as 64501
 address-family ipv4
  neighbor 10.0.0.1 activate
  network 203.0.113.0 mask 255.255.255.0
 exit-address-family
```
O `network` exige que o prefixo exato exista na tabela de roteamento em muitas implementações. Ajuste endereços e sintaxe ao seu ambiente.

## Comandos de verificação
```text
show ip bgp summary
show ip bgp
show ip route
show ip bgp neighbors

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- A sessão chega a Established.
- O prefixo é recebido e aparece na tabela BGP.
- O next-hop está alcançável e a rota pode ser instalada.
- O aluno explica a diferença entre sessão Established e conectividade fim a fim.

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
