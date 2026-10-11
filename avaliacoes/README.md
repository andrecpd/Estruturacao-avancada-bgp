# Avaliações

## Questionário conceitual
1. Qual a diferença entre eBGP e iBGP?
2. O que significa uma sessão Established e por que isso não garante tráfego?
3. Qual a diferença entre import policy e export policy?
4. Para que serve Local Preference?
5. Por que AS-PATH prepend não garante um caminho de entrada?
6. Qual a diferença entre RIB e FIB?
7. O que RPKI origin validation valida e o que não valida?
8. Por que uma exportação em allow-list reduz risco?
9. O que muda entre default-only e full routes?
10. Por que um Route Reflector precisa de desenho e redundância?

## Exercício de análise
Um ISP recebe o mesmo prefixo por dois upstreams. A rota via Transit-A tem Local Preference 200 e a via Transit-B tem 100. A rota A desaparece. Explique o comportamento esperado e quais comandos comprovam a troca.

## Exercício de segurança
Um cliente anuncia `0.0.0.0/0` e um prefixo que não está em sua lista autorizada. Descreva as políticas de entrada necessárias e como comprovar que não foram propagados.

## Avaliação prática final
Use a rubrica do Módulo 18. O avaliador deve verificar as evidências, não apenas a configuração digitada.
