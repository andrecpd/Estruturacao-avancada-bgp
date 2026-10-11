# Cisco IOS/IOS XE — eBGP básico (exemplo de laboratório)

**Topologia:** R1 AS65010 `192.0.2.1/30`; R2 AS65020 `192.0.2.2/30`. LANs de documentação `198.51.100.0/24` e `203.0.113.0/24`. Ajuste a sintaxe à versão.

## R1
```cisco
hostname R1
interface GigabitEthernet0/0
 description eBGP-to-R2
 ip address 192.0.2.1 255.255.255.252
 no shutdown
!
interface Loopback0
 ip address 198.51.100.1 255.255.255.0
!
ip route 198.51.100.0 255.255.255.0 Null0
router bgp 65010
 bgp log-neighbor-changes
 neighbor 192.0.2.2 remote-as 65020
 address-family ipv4
  network 198.51.100.0 mask 255.255.255.0
  neighbor 192.0.2.2 activate
 exit-address-family
```

## R2
```cisco
hostname R2
interface GigabitEthernet0/0
 description eBGP-to-R1
 ip address 192.0.2.2 255.255.255.252
 no shutdown
!
interface Loopback0
 ip address 203.0.113.1 255.255.255.0
!
ip route 203.0.113.0 255.255.255.0 Null0
router bgp 65020
 bgp log-neighbor-changes
 neighbor 192.0.2.1 remote-as 65010
 address-family ipv4
  network 203.0.113.0 mask 255.255.255.0
  neighbor 192.0.2.1 activate
 exit-address-family
```

> Nota: a declaração `network` exige que o prefixo exato exista na tabela de roteamento. A rota Null0 é didática; em produção, use origem/aggregate e filtros alinhados ao desenho real. Não use esses ASNs/prefixos em peers públicos.

## Verificação
```text
show ip bgp summary
show ip bgp
show ip route bgp
show ip bgp neighbors 192.0.2.2 advertised-routes
```
