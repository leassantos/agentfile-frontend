# Prompt template: commit + push + PR

> Como usar: cole este arquivo em uma task do Codex após a feature estar implementada
> e os testes passando. Adapte apenas o bloco "Configurações do projeto" na primeira vez.

---

## Configurações do projeto

> ✏️ Preencha uma vez, na configuração inicial do template.

- Comando de testes: [PREENCHER: ex. npm test / pnpm test / npm run test:ci]
- Comando de lint: [PREENCHER: ex. npm run lint / pnpm lint]
- Comando de formatação: [PREENCHER: ex. npm run format / pnpm format]
- Comando de build (verificação): [PREENCHER: ex. npm run build / pnpm build]
- Labels padrão do PR: [PREENCHER: ex. feature, needs-review]
- Reviewers padrão: [PREENCHER: ex. @username ou deixar vazio]

---

## Instruções para o agente

Execute as etapas abaixo em sequência. Pare e me informe se qualquer etapa falhar.
Não avance para a próxima etapa sem confirmar que a atual foi concluída com sucesso.

### Etapa 1 — verificar estado do repositório
```
git status
git diff --stat
```
Liste os arquivos modificados. Confirme que não há arquivos não relacionados à feature incluídos.
Se houver arquivos inesperados, informe antes de continuar.

### Etapa 2 — rodar os testes
```
[PREENCHER: comando de testes]
```
Se algum teste falhar, corrija antes de continuar.
Não faça commit de código com testes falhando.

### Etapa 3 — verificar lint
```
[PREENCHER: comando de lint]
```
Corrija todas as violações antes de continuar.
Nunca usar `eslint-disable` para suprimir erros sem justificativa documentada.

### Etapa 4 — verificar build
```
[PREENCHER: comando de build]
```
O build não deve ter erros de TypeScript nem warnings não tratados.
Se houver erros, corrija antes de continuar.

### Etapa 5 — preparar o commit
Adicione apenas os arquivos relacionados à feature atual:
```
git add <arquivos relevantes>
```
Nunca use `git add .` sem listar e confirmar cada arquivo incluído.
Confirme que nenhum arquivo `.env` ou com secrets está sendo incluído.

### Etapa 6 — escrever a mensagem de commit
Siga o padrão Conventional Commits:

```
<tipo>(<escopo>): <descrição curta em inglês, imperativo, sem ponto final>

<corpo opcional: explique o "por quê", não o "o quê">

Closes #<número da issue, se houver>
```

Tipos válidos:
- `feat` — nova tela, componente ou funcionalidade visível ao usuário
- `fix` — correção de bug visual ou funcional
- `test` — adição ou correção de testes
- `refactor` — refatoração sem mudança de comportamento
- `style` — ajustes de CSS/estilo sem mudança funcional
- `perf` — melhoria de performance
- `a11y` — melhorias de acessibilidade
- `docs` — documentação
- `chore` — tarefas de manutenção (deps, config, etc.)

Exemplos:
```
feat(auth): add login form with JWT integration
fix(auth): prevent form submission when fields are empty
style(auth): align login button to full width on mobile
a11y(auth): add aria-label to password visibility toggle
test(auth): add tests for invalid credentials error state
```

### Etapa 7 — fazer o push
```
git push origin <branch-atual>
```

### Etapa 8 — abrir o Pull Request
Crie um PR com a seguinte estrutura:

**Título**: mesma mensagem do commit principal

**Descrição**:
```markdown
## O que foi feito
[descrição objetiva do que foi implementado]

## Screenshots
<!-- Adicione capturas de tela ou gravação do fluxo implementado -->
| Antes | Depois |
|-------|--------|
| -     | [imagem] |

## Como testar
1. [passo 1]
2. [passo 2]
3. [resultado esperado]

## Checklist
- [ ] Testes passando
- [ ] Build sem erros de TypeScript
- [ ] Lint sem violações
- [ ] Responsivo (mobile e desktop)
- [ ] Acessível via teclado
- [ ] Estados de loading e erro implementados
- [ ] Sem `console.log` no código
- [ ] Sem secrets ou variáveis de ambiente expostas
```

Retorne a URL do PR criado ao finalizar.
