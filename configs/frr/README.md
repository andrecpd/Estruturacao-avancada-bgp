# FRRouting (FRR)

Use FRR para laboratórios reproduzíveis com Linux/Containerlab. A sintaxe depende da versão e da configuração de daemon. Monte primeiro um laboratório mínimo e valide `vtysh`, `show bgp summary`, `show bgp ipv4 unicast` e a instalação de rotas.

Não copie diretamente comandos Cisco para FRR. Crie arquivos `frr.conf` separados por roteador, fixe a versão da imagem usada e registre os resultados dos testes.
