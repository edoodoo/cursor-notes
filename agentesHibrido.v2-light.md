# Playbook Hibrido v2 Light

## Objetivo

Executar migracao para Android/iOS com:
- 4 agentes de trilha (A/B/C/D) em janelas separadas;
- 1 Orquestrador para consolidar e priorizar;
- subagentes nativos para paralelismo interno em cada trilha.

---

## Quando usar

Use se houver:
- varias frentes paralelas;
- dependencia cruzada;
- prazo apertado.

Nao use para tarefas pequenas e pontuais.

---

## Regras minimas

1. Ciclo de 2 horas.
2. Um objetivo principal por ciclo.
3. Um proximo passo unico por trilha por ciclo.
4. Sem escopo novo sem autorizacao do Orquestrador.
5. Bloqueio critico => replanejar antes de continuar.

Contrato padrao para todos:

```text
Status: done | in_progress | blocked
Entregaveis:
Bloqueios:
Proximo passo unico:
Tempo restante estimado:
```

---

## Scripts de criacao (resumo pronto)

## Agente A - Build Mobile
```text
Voce e o Agente A - Build Mobile.
Foco: empacotamento iOS/Android, IDs, splash, icones, permissoes e scripts de build.
Nao alterar regra de negocio sem alinhamento.
Acionar subagentes nativos para subtarefas independentes.
Responder no contrato padrao.
```

## Agente B - UX Mobile
```text
Voce e o Agente B - UX Mobile.
Foco: navegacao mobile, safe area, legibilidade, loading/erro/feedback.
Nao mexer em billing/compliance sem alinhamento.
Acionar subagentes nativos para subtarefas independentes.
Responder no contrato padrao.
```

## Agente C - Store and Compliance
```text
Voce e o Agente C - Store and Compliance.
Foco: checklist App Store/Play Store, listing, suporte, termos e privacidade.
Nao implementar codigo de produto fora do escopo.
Acionar subagentes nativos para subtarefas independentes.
Responder no contrato padrao.
```

## Agente D - QA and Release
```text
Voce e o Agente D - QA and Release.
Foco: smoke tests, regressao curta, severidade de bugs e recomendacao GO/NO-GO.
Nao abrir escopo novo sem alinhamento.
Acionar subagentes nativos para subtarefas independentes.
Responder no contrato padrao.
```

## Orquestrador
```text
Voce e o Orquestrador do release mobile.
Foco: consolidar A/B/C/D, resolver bloqueios cruzados e manter caminho critico.
Sincronizar a cada 90-120 min.
Definir um proximo passo unico por trilha por rodada.
Responder com: Estado global, Resumo A/B/C/D, Top 5 bloqueios, proximos passos, caminho critico, GO/NO-GO.
```

---

## Comandos explicitos para subagentes (por trilha)

Use estes blocos dentro da janela de cada agente:

## Build (A)
```text
Ative subagentes nativos em paralelo para:
1) IDs, icones, splash e permissoes
2) scripts de build iOS/Android
3) diagnostico de erros de empacotamento
Consolide: status por frente, bloqueios, impacto no caminho critico e proximo passo unico.
```

## UX (B)
```text
Ative subagentes nativos em paralelo para:
1) navegacao/menu e sobreposicao
2) safe area, espacamento e legibilidade
3) loading/erro/feedback
Consolide: status por frente, bloqueios, impacto no caminho critico e proximo passo unico.
```

## Compliance (C)
```text
Ative subagentes nativos em paralelo para:
1) checklist App Store/Play Store
2) textos de listing e suporte
3) termos, privacidade e gaps de submissao
Consolide: status por frente, bloqueios, impacto no caminho critico e proximo passo unico.
```

## QA (D)
```text
Ative subagentes nativos em paralelo para:
1) smoke tests criticos
2) regressao curta orientada a risco
3) severidade de bugs
Consolide: status por frente, bloqueios, impacto no caminho critico e proximo passo unico.
```

---

## Passo a passo (semi-manual)

1. Criar 4 janelas e colar scripts A/B/C/D.
2. Renomear: `A-Build`, `B-UX`, `C-Compliance`, `D-QA`.
3. Criar janela `Orquestrador` e colar script dele.
4. Rodar kickoff (bloco abaixo).
5. Executar ciclo de 2h.
6. Copiar resumo de A/B/C/D e colar no Orquestrador.
7. Repetir a cada 90-120 min.

Kickoff:

```text
Kickoff do ciclo de 2 horas.
Consolidar status de A/B/C/D, listar bloqueios cruzados, definir proximo passo unico por trilha, caminho critico e GO/NO-GO da rodada.
Formato: Estado global, Resumo A/B/C/D, Top 5 bloqueios, Proximo passo A/B/C/D, Caminho critico, Go/No-Go.
```

---

## Fechamento de ciclo (copiar e colar no Orquestrador)

No fim de cada ciclo, colete de A/B/C/D:
- Status
- Entregaveis
- Bloqueios
- Proximo passo unico
- Tempo restante estimado

Cole no Orquestrador:

```text
Fechamento de ciclo (2h)
A: status=..., entregou=..., bloqueio=..., proximo=..., ETA=...
B: status=..., entregou=..., bloqueio=..., proximo=..., ETA=...
C: status=..., entregou=..., bloqueio=..., proximo=..., ETA=...
D: status=..., entregou=..., bloqueio=..., proximo=..., ETA=...

Tarefa do Orquestrador:
1) Priorizar bloqueios
2) Atualizar caminho critico
3) Definir proximo passo unico de A/B/C/D
4) Definir criterio de encerramento do proximo ciclo
5) Registrar Go/No-Go parcial
```

---

## Cronograma macro 72h (referencia)

- H0-H6: kickoff e backlog por trilha
- H6-H24: execucao paralela intensa
- H24-H36: integracao e conflitos
- H36-H48: QA em device e fixes bloqueantes
- H48-H60: pacote de submissao tecnica
- H60-H72: freeze, build final e material de publicacao

---

## Erros comuns e como evitar

- Erro: abrir escopo novo no meio do ciclo; evitar: validar com Orquestrador antes de qualquer desvio.
- Erro: dois agentes atuando no mesmo item; evitar: um proximo passo unico por trilha.
- Erro: checkpoint sem dados objetivos; evitar: sempre usar o contrato padrao.
- Erro: esquecer bloqueio cruzado; evitar: revisar dependencias A/B/C/D em todo fechamento.
- Erro: confiar em handoff automatico entre janelas; evitar: copiar/colar resumo no Orquestrador a cada ciclo.

---

## Automatico vs manual

Automatico:
- cada agente executa sua trilha;
- cada agente pode usar subagentes nativos em paralelo.

Manual:
- criar/renomear janelas;
- disparar scripts;
- transferir resumo de A/B/C/D para o Orquestrador.

Resposta curta: nao e 100% automatico entre janelas; o handoff e semi-manual.
