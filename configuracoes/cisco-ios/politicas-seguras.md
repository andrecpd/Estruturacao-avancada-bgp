# Exemplo de filtros e política de cliente (adaptar antes de usar)

```cisco
ip prefix-list CUSTOMER-A-IN seq 10 permit 198.51.100.0/24
! deny implícito para todo o restante
!
route-map CUSTOMER-A-IN permit 10
 match ip address prefix-list CUSTOMER-A-IN
 set local-preference 200
!
router bgp 65010
 address-family ipv4
  neighbor 192.0.2.6 route-map CUSTOMER-A-IN in
 exit-address-family
```

Este fragmento é ilustrativo: confirme endereço/ASN do peer, política de exportação, origem autorizada, maximum-prefix, RPKI/IRR, logging e sintaxe da versão. Um filtro inbound não substitui filtro outbound. Antes de ativar em produção, valide em laboratório e revise o diff.
