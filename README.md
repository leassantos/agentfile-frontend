# Codex Workflow Template

Template de workflow para projetos frontend usando o OpenAI Codex como agente de desenvolvimento.
Agnóstico de framework — funciona com React, Next.js, Vue, Angular ou qualquer outra stack.

---

## O que é este template

Uma estrutura de arquivos de configuração que instrui o Codex sobre como trabalhar no seu projeto frontend — quais regras de componentes, estilo e acessibilidade seguir, como planejar antes de implementar, como revisar código e como fazer commits e PRs de forma padronizada.

A diferença em relação ao template backend: este inclui um agente especializado em **acessibilidade e UX** no lugar do auditor de segurança, e o plan mode cobre estados de UI (loading, erro, vazio), responsividade e acessibilidade.

---

## Estrutura

```
.
├── AGENTS.md                              ← lido automaticamente pelo Codex em toda task
└── .codex/
    ├── instructions.md                    ← contexto arquitetural, sistema de design, decisões
    ├── agents/
    │   ├── code-reviewer.md               ← revisão de código, arquitetura, testes, performance
    │   └── accessibility-auditor.md       ← acessibilidade WCAG AA e UX
    └── prompts/
        ├── plan-mode.md                   ← planejamento de features antes de implementar
        └── commit-push-pr.md              ← finalizar com commit semântico e PR estruturado
```

---

## Como usar: passo a passo

### Passo 1 — clone o template para dentro do seu projeto

```bash
git clone https://github.com/seu-usuario/agentfile-frontend.git
cp -r agentfile-frontend/AGENTS.md meu-projeto/
cp -r agentfile-frontend/.codex meu-projeto/
cd meu-projeto
```

### Passo 2 — preencha os arquivos de configuração

Esta é a etapa mais importante. Abra cada arquivo e substitua todos os blocos marcados com `[PREENCHER]`.

#### 2.1 — `AGENTS.md` (obrigatório, prioridade máxima)

O Codex lê este arquivo em toda task. Ele define as regras que o agente nunca pode violar.

Preencha:

**Stack completa** — seja específico:
```markdown
- Framework: Next.js 14 (App Router)
- Linguagem: TypeScript 5
- Gerenciador de pacotes: pnpm
- Estilização: Tailwind CSS
- Gerenciamento de estado: Zustand
- Requisições HTTP: TanStack Query + Axios
- Testes: Vitest + Testing Library
- Linter/formatter: ESLint + Prettier
```

**Regras de arquitetura** — o que o agente deve e não deve fazer:
```markdown
- Chamadas de API nunca dentro de componentes — sempre em hooks customizados
- Componentes máximo 150 linhas — extrair em subcomponentes se ultrapassar
- Props sempre tipadas com interface, nunca type inline
- Nunca usar `any` em TypeScript sem comentário justificando
```

**Regras de estilização**:
```markdown
- Mobile-first: escrever o estilo base para mobile e usar md:/lg: para desktop
- Nunca usar valores de cor fora da paleta do Tailwind configurada
- Nunca usar px hardcoded para espaçamento — usar escala do Tailwind
```

**Regras de testes**:
```markdown
- Testar comportamento do usuário, não implementação
- Sempre cobrir: estado de loading, estado de erro, estado vazio e sucesso
- Seletores por role ou data-testid, nunca por classe CSS
```

#### 2.2 — `.codex/instructions.md`

Contexto mais profundo para o agente tomar decisões consistentes.

Preencha com o que já foi decidido no projeto:

- **Decisões arquiteturais com justificativa** — por que Zustand e não Redux? Por que App Router e não Pages Router? Documente o "por quê" para o agente não reverter essas decisões.
- **Estrutura de pastas** — adapte o exemplo fornecido à estrutura real do seu projeto.
- **Módulos planejados** — lista de features com status (planejado, em desenvolvimento, concluído).
- **Integração com a API** — URL base, como o token é enviado, formato das responses.
- **Variáveis de ambiente** — quais existem e o que cada uma representa.
- **Sistema de design** — tokens de cor, tipografia e breakpoints para o agente usar valores corretos.
- **Glossário de domínio** — termos específicos do negócio para nomear componentes e variáveis corretamente.

> Não precisa estar completo no dia 1. Adicione as decisões conforme elas forem sendo tomadas.

#### 2.3 — `.codex/prompts/commit-push-pr.md`

Preencha apenas o bloco "Configurações do projeto" no topo:

```markdown
- Comando de testes: pnpm test
- Comando de lint: pnpm lint
- Comando de formatação: pnpm format
- Comando de build: pnpm build
- Labels padrão do PR: feature, needs-review
- Reviewers padrão: @seu-tech-lead
```

#### 2.4 — `.codex/agents/code-reviewer.md` e `accessibility-auditor.md`

Substitua `[NOME DO PROJETO]` nos dois arquivos.

Em `code-reviewer.md`, preencha os blocos `[PREENCHER]` com:
- Riscos de segurança específicos do seu projeto
- Antipadrões da sua stack (ex: padrões do Vue que devem ser evitados)
- Convenções de teste que você adota

Em `accessibility-auditor.md`, adicione no bloco "Específicos do projeto":
- Fluxos críticos que precisam ser 100% acessíveis
- Componentes com requisitos especiais (ex: player de vídeo, mapa interativo, gráficos)

#### 2.5 — commite os arquivos preenchidos

```bash
git add AGENTS.md .codex/
git commit -m "chore: add codex workflow configuration"
git push origin main
```

A partir daqui, toda task do Codex vai ler o `AGENTS.md` automaticamente.

---

### Passo 3 — use o workflow em cada feature

#### 3.1 — planejamento (sempre o primeiro passo)

Abra uma nova task no Codex CLI:

```bash
codex
```

Cole o conteúdo de `.codex/prompts/plan-mode.md` e substitua o placeholder pela descrição da feature:

```
[DESCREVA AQUI O QUE PRECISA SER IMPLEMENTADO]
```

Exemplo real:
```
Implementar a tela de login com formulário de email e senha.
A tela deve chamar POST /api/v1/auth/login, armazenar o token JWT no localStorage
e redirecionar para /dashboard em caso de sucesso.
Deve mostrar mensagem de erro genérica em caso de falha.
```

Aguarde o plano. Revise:
- Os componentes propostos fazem sentido?
- Os estados de loading, erro e sucesso foram considerados?
- A acessibilidade foi mencionada?
- O plano de testes cobre os casos de borda?

Só aprove quando estiver correto — é mais barato ajustar um plano do que refatorar código.

#### 3.2 — execução em tasks paralelas (features maiores)

Para features que envolvem múltiplos componentes, divida em tasks simultâneas:

| Task | Exemplo de escopo |
|------|-------------------|
| Task A | Componentes de UI (formulário, inputs, botões) |
| Task B | Hook de autenticação, integração com API, gerenciamento de estado |
| Task C | Testes e tratamento de estados de erro/loading |

Instrua cada task a rodar os testes ao final:
```
Após implementar, rode [comando de testes] e corrija qualquer falha antes de encerrar.
```

#### 3.3 — revisão de código

Após a implementação, invoque o agente de revisão:

```
Usando as instruções em .codex/agents/code-reviewer.md,
revise os seguintes arquivos: [lista dos arquivos modificados]
```

#### 3.4 — auditoria de acessibilidade

Para features com formulários, fluxos críticos ou novos componentes interativos:

```
Usando as instruções em .codex/agents/accessibility-auditor.md,
audite os seguintes arquivos: [lista dos arquivos relevantes]
```

#### 3.5 — commit e PR

Cole o conteúdo de `.codex/prompts/commit-push-pr.md` em uma task.
O agente vai verificar o estado do repo, rodar testes, lint e build, escrever o commit em Conventional Commits e abrir o PR com screenshots placeholder e checklist.

---

## Fluxo resumido

```
Nova feature
    │
    ▼
[plan-mode.md] → plano gerado → revisão humana → aprovação
    │
    ▼
Execução (tasks paralelas se for grande)
    │
    ▼
Feedback loop automático (testa → corrige → testa)
    │
    ▼
[code-reviewer.md] → relatório de revisão → correções
    │
    ▼
[accessibility-auditor.md] → auditoria → correções (se houver)
    │
    ▼
[commit-push-pr.md] → commit + push + PR aberto
```

---

## Diferenças em relação ao template backend

| Aspecto | Backend | Frontend |
|---------|---------|----------|
| Agente especializado | Security Auditor | Accessibility & UX Auditor |
| Plan mode cobre | Arquitetura de camadas, segurança | Estados de UI, responsividade, a11y |
| Commit types extras | `security` | `style`, `perf`, `a11y` |
| Checklist do PR | Migrations, secrets | Screenshots, responsividade, a11y |
| Regras específicas | Injeção de dependência, TDD | Tamanho de componente, prop typing |

---

## Dicas de uso

**Refine o `AGENTS.md` ao longo do projeto.** Toda vez que o agente entregar algo fora do padrão esperado — um componente muito grande, uma chamada de API dentro do JSX, cores hardcoded — adicione uma regra explícita. O template melhora com o uso.

**Use o glossário do `instructions.md`.** Se o domínio tem termos específicos (ex: "lote" e "lance" em um sistema de leilão), documente. O agente vai nomear componentes e variáveis de acordo, evitando nomes genéricos como `ItemCard` onde `LoteCard` seria mais claro.

**Versione tudo no Git.** Esses arquivos são tão importantes quanto o código. Quando um novo desenvolvedor ou uma nova sessão do Codex começa, as regras já estão lá.

---

## Licença

MIT — use, adapte e distribua à vontade.
