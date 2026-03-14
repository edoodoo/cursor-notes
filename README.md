# cursor-notes

Repositório para persistir conversas e decisões por tema/projeto.

## Estrutura
- app-auraflow/
- financas/
- estudos/
- templates/
- immersif/

## Padrão de arquivo
AAAA-MM-DD-assunto-curto.md

Exemplo:
2026-03-11-planejamento-financeiro.md


## Ritual rápido (30s)
1. Crie/atualize uma nota na pasta do tema:
   - app-auraflow/
   - financas/
   - immersif/
   - estudos/
2. Nome do arquivo:
   AAAA-MM-DD-assunto-curto.md
3. Salve e rode no terminal:
   git add .
   git commit -m "docs(<tema>): resumo da sessão"
   git push
Exemplos:
- docs(financas): resumo da sessão de orçamento
- docs(app-auraflow): decisões do fluxo mensal
- docs(immersif): registro da sessão


O chat está ficando longo. Gere um resumo operacional do estado atual e atualize o arquivo `context.md` com:
1) Objetivo atual
2) O que já foi feito
3) Decisões tomadas
4) Pendências
5) Próximo passo único (somente 1)
6) Riscos/observações
Regras:
- Seja direto e prático
- Remova duplicações
- Mantenha no máximo ~120 linhas
- Preserve apenas o que é necessário para retomar o trabalho sem perder contexto

Antes de qualquer ação, leia `context.md` e use como fonte principal de continuidade.

Depois:
1) me confirme em 5 bullets o que entendeu
2) diga qual é o próximo passo único
3) execute esse próximo passo sem recomeçar do zero

git add context.md
git commit -m "checkpoint: atualizar contexto da sessao"
git push