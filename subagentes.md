# Guia de Subagentes no Cursor

Este arquivo centraliza comandos prontos para usar subagentes com clareza.  
Cada comando foi desenhado para:
- dividir tarefas em frentes paralelas;
- reduzir tempo de investigação;
- aumentar previsibilidade dos entregáveis.

---

## 1) Estudo de codebase (arquitetura e fluxos)

### O que este comando executa
- aciona subagentes em paralelo para mapear estrutura, responsabilidades e fluxo de dados;
- identifica arquivos-chave e pontos de entrada do sistema;
- retorna riscos técnicos e próximos passos priorizados.

### Por que usar
- quando você entrou em um projeto novo e quer entendimento rápido;
- quando precisa planejar refactor sem mexer no código ainda;
- quando quer visão macro antes de pedir implementação.

### Comando completo
```text
Use subagentes em paralelo para mapear este projeto.
Objetivo: entender arquitetura, fluxos principais e pontos de entrada.
Profundidade: média.
Entregáveis:
1) estrutura de pastas e responsabilidades
2) fluxo de dados end-to-end
3) onde ficam regras de negócio
4) riscos técnicos e dívidas
Restrições:
- não editar arquivos
- não executar comandos destrutivos
No final, consolide em:
- visão geral
- mapa de arquivos-chave
- 5 próximos passos priorizados.
```

### Versão curta
```text
Use subagentes em paralelo para mapear arquitetura, fluxo de dados, regras de negócio e riscos do projeto, sem editar arquivos. Entregue visão geral, arquivos-chave e próximos passos priorizados.
```

---

## 2) Debugging (causa raiz com mínimo risco)

### O que este comando executa
- divide investigação de bug em trilhas simultâneas;
- testa hipóteses e converge para causa raiz confirmada;
- produz plano de correção mínima com validação de regressão.

### Por que usar
- quando o bug é intermitente ou atravessa várias camadas;
- quando você quer diagnóstico antes de alterar contrato/API;
- quando precisa reduzir tentativa e erro no conserto.

### Comando completo
```text
Use subagentes em paralelo para investigar este bug.
Bug: <descreva erro + comportamento esperado>.
Contexto: <logs, tela, endpoint, stacktrace>.
Objetivo: identificar causa raiz e propor correção mínima segura.
Profundidade: profunda.
Entregáveis:
1) hipóteses testadas
2) causa raiz confirmada
3) arquivos/símbolos impactados
4) plano de correção com riscos
Restrições:
- não commitar
- não alterar contrato público sem me avisar
No final, consolide em:
- diagnóstico final
- patch sugerido
- plano de teste de regressão.
```

### Versão curta
```text
Use subagentes em paralelo para investigar este bug com base em logs/contexto, confirmar causa raiz e propor correção mínima segura com plano de regressão, sem commit e sem mudar contrato público sem aviso.
```

---

## 3) Preparar PR (qualidade e risco)

### O que este comando executa
- distribui revisão técnica, testes e análise de segurança/performance;
- organiza findings por severidade;
- entrega checklist objetivo para decisão de merge.

### Por que usar
- quando você quer aumentar qualidade antes de abrir PR;
- quando precisa de revisão multidimensional (lógica, testes, segurança);
- quando quer decisão clara: pronto para PR ou bloqueado.

### Comando completo
```text
Use subagentes em paralelo para preparar esta entrega para PR.
Objetivo: revisar mudanças, validar testes e reduzir risco de regressão.
Profundidade: média.
Frentes paralelas:
- subagente 1: revisão de lógica e edge cases
- subagente 2: testes e cobertura
- subagente 3: performance e segurança
Entregáveis:
1) findings por severidade
2) lacunas de testes
3) checklist de PR pronto para merge
Restrições:
- sem push
- sem alterar configs globais
No final, consolide em:
- resumo executivo
- mudanças recomendadas
- decisão: pronto para PR ou bloqueado.
```

### Versão curta
```text
Use subagentes em paralelo para revisar esta entrega para PR (lógica, testes e segurança/performance), listar findings por severidade e concluir com checklist e decisão de merge, sem push e sem alterar configurações globais.
```

---

## Como escolher rapidamente o comando certo

- Use **Estudo de codebase** quando o objetivo é entendimento do sistema.
- Use **Debugging** quando há erro real para diagnosticar e corrigir.
- Use **Preparar PR** quando a mudança já existe e você quer validar qualidade.

## Regra prática

Se a tarefa pode ser quebrada em 2 ou mais frentes independentes, vale subagente.  
Se for ajuste pequeno e direto, normalmente não vale o overhead.
