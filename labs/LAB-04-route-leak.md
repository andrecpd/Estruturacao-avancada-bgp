# LAB-04 — Prevenção de route leak

**Objetivo:** impedir que rotas aprendidas de um upstream sejam exportadas para outro upstream sem autorização.

## Topologia simplificada
EDGE (AS65010) liga-se aos dois upstreams: Transit A (AS65001) e Transit B (AS65002). Prefixo próprio do ISP: 198.51.100.0/24. O exemplo implementa uma política de saída explícita para cada trânsito.

| Link | EDGE | Upstream |
|---|---|---|
| EDGE–A | 192.0.2.2/30 | A: 192.0.2.1/30 |
| EDGE–B | 192.0.2.6/30 | B: 192.0.2.5/30 |

## EDGE — AS65010
```cisco
hostname EDGE
interface GigabitEthernet0/0
 description TRANSIT-A-AS65001
 ip address 192.0.2.2 255.255.255.252
 no shutdown
interface GigabitEthernet0/1
 description TRANSIT-B-AS65002
 ip address 192.0.2.6 255.255.255.252
 no shutdown
interface Loopback0
 description ISP-OWNED-PREFIX
 ip address 198.51.100.1 255.255.255.0
!
ip prefix-list OWN-PREFIXES seq 10 permit 198.51.100.0/24
route-map EXPORT-TRANSIT permit 10
 match ip address prefix-list OWN-PREFIXES
!
router bgp 65010
 bgp log-neighbor-changes
 neighbor 192.0.2.1 remote-as 65001
 neighbor 192.0.2.5 remote-as 65002
 !
 address-family ipv4
  network 198.51.100.0 mask 255.255.255.0
  neighbor 192.0.2.1 activate
  neighbor 192.0.2.5 activate
  neighbor 192.0.2.1 route-map EXPORT-TRANSIT out
  neighbor 192.0.2.5 route-map EXPORT-TRANSIT out
 exit-address-family
```

## Transit A — AS65001
```cisco
hostname TRANSIT-A
interface GigabitEthernet0/0
 ip address 192.0.2.1 255.255.255.252
 no shutdown
router bgp 65001
 bgp log-neighbor-changes
 neighbor 192.0.2.2 remote-as 65010
 !
 address-family ipv4
  neighbor 192.0.2.2 activate
 exit-address-family
```

## Transit B — AS65002
```cisco
hostname TRANSIT-B
interface GigabitEthernet0/0
 ip address 192.0.2.5 255.255.255.252
 no shutdown
router bgp 65002
 bgp log-neighbor-changes
 neighbor 192.0.2.6 remote-as 65010
 !
 address-family ipv4
  neighbor 192.0.2.6 activate
 exit-address-family
```

A política `EXPORT-TRANSIT` permite somente o prefixo próprio listado. Por isso, rotas aprendidas de um trânsito não são anunciadas ao outro. Para permitir prefixos de clientes, adicione-os explicitamente à prefix-list após validar autorização.

## Teste e validação
```cisco
show ip bgp summary
show ip bgp
show ip bgp neighbors 192.0.2.1 advertised-routes
show ip bgp neighbors 192.0.2.5 advertised-routes
show ip prefix-list OWN-PREFIXES
```
Introduza uma rota aprendida de um upstream e confirme que ela não aparece nos anúncios de saída para o outro.

## Critério de aceitação
Nenhuma rota de Transit A é anunciada a Transit B, salvo se o AS fornecer explicitamente trânsito entre eles.
