# Módulo 17 — Automação, versionamento e validação

## Objetivos de aprendizagem
Ao final, o aluno deverá explicar os conceitos do módulo, implementar a política no laboratório e demonstrar o comportamento com evidências observáveis.

## Fundamentos e teoria
Configuração de roteadores é código operacional: deve ter histórico, revisão, testes e rollback. Git registra alterações e permite comparar versões. Uma pipeline pode verificar sintaxe, lint de YAML, consistência de prefixos, existência de filtros, duplicidade de ASN e políticas de exportação permissivas.

Automação não elimina a revisão técnica. Testes sintáticos não provam comportamento de roteamento; combine validação estática, laboratório, testes de aceitação e monitoramento pós-mudança. Segredos e credenciais nunca devem ser commitados.

## Preparação do laboratório
- Use uma topologia isolada com ASNs privados.
- Confira endereçamento e reachability antes de ativar BGP.
- Salve a configuração inicial para permitir rollback.
- Substitua os endereços ilustrativos pelos endereços da sua topologia.

## Prática guiada
1. Armazene arquivos de laboratório no Git.
2. Faça branch para uma nova política.
3. Compare o diff antes de aprovar.
4. Execute testes de consistência simples.
5. Simule falha de teste e bloqueie o merge.
6. Documente commit, janela e rollback.

## Exemplo de configuração
Exemplo de validação simples em Python (conceitual):
```python
from pathlib import Path

for path in Path("configs").rglob("*"):
    if path.is_file():
        text = path.read_text(errors="ignore")
        if "neighbor 0.0.0.0" in text:
            raise SystemExit(f"Peer placeholder encontrado em {path}")
print("Validação básica concluída")
```
Esse exemplo é apenas um ponto de partida; validação real deve usar parser apropriado à plataforma.

## Comandos de verificação
```text
git status
git diff
git log --oneline --decorate -10
# Executar o conjunto de testes documentado antes do merge.

```

## Desafios
1. Explique o comportamento esperado antes de executar a mudança.
2. Introduza uma falha controlada relacionada ao tema e identifique a causa.
3. Faça a correção mínima, valide e documente o rollback.
4. Repita o cenário com IPv6 quando aplicável.

## Critérios de aceite
- Mudanças têm diff revisável.
- Arquivos não contêm senhas/tokens.
- Testes detectam pelo menos um erro intencional.
- O processo de rollback está documentado.

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
