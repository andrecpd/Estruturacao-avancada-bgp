# FRRouting — exemplo conceitual eBGP

A sintaxe exata pode variar por versão. Execute em containers isolados e consulte a documentação da versão instalada.

```text
router bgp 65010
 bgp router-id 192.0.2.1
 neighbor 192.0.2.2 remote-as 65020
 address-family ipv4 unicast
  network 198.51.100.0/24
  neighbor 192.0.2.2 activate
 exit-address-family
```

Verifique com `show bgp summary`, `show bgp ipv4 unicast` e `show ip route`. Garanta que o prefixo esteja presente na tabela antes de anunciá-lo.
