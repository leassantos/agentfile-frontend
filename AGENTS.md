# [NOME DO PROJETO] — Instruções para o agente

> Arquivo lido automaticamente pelo Codex em toda task.
> Preencha todas as seções marcadas com `[PREENCHER]` antes de começar o projeto.
> Remova os comentários em `>` após preencher.

## Contexto do projeto

> Descreva em 2-3 frases o que o projeto faz e para quem.

[PREENCHER: descrição do projeto]

Stack:
- Framework: [PREENCHER: ex. React 18 / Next.js 14 / Vue 3 / Angular 17]
- Linguagem: [PREENCHER: ex. TypeScript 5 / JavaScript]
- Gerenciador de pacotes: [PREENCHER: ex. npm / pnpm / yarn]
- Estilização: [PREENCHER: ex. Tailwind CSS / CSS Modules / Styled Components / SCSS]
- Gerenciamento de estado: [PREENCHER: ex. Zustand / Redux Toolkit / Pinia / Context API / nenhum]
- Requisições HTTP: [PREENCHER: ex. Axios / Fetch nativo / TanStack Query]
- Testes: [PREENCHER: ex. Vitest + Testing Library / Jest + Testing Library / Cypress]
- Linter/formatter: [PREENCHER: ex. ESLint + Prettier / Biome]

---

## Regras obrigatórias de desenvolvimento

> Adapte cada seção à sua stack. Remova o que não se aplica. Adicione o que falta.

### Linguagem e nomenclatura
- Código em: [PREENCHER: inglês / português]
- Documentação externa em: [PREENCHER: português / inglês]
- Convenção de nomes de componentes: [PREENCHER: ex. PascalCase]
- Convenção de nomes de funções e variáveis: [PREENCHER: ex. camelCase]
- Convenção de nomes de arquivos: [PREENCHER: ex. PascalCase para componentes, kebab-case para utils]
- Convenção de nomes de CSS classes: [PREENCHER: ex. BEM / utility-first / camelCase]

### Arquitetura e organização
- [PREENCHER: estrutura de pastas adotada — ex. feature-based / layer-based]
- [PREENCHER: onde ficam componentes globais vs específicos de feature]
- [PREENCHER: regra para criação de componentes — ex. um componente por arquivo]
- [PREENCHER: quando usar componente vs hook customizado]
- [PREENCHER: como separar lógica de UI — ex. container/presentational, hooks extraídos]
- [PREENCHER: política de prop drilling — ex. máximo de 2 níveis antes de usar contexto/store]

### Componentes
- [PREENCHER: tamanho máximo de um componente — ex. máximo 150 linhas]
- [PREENCHER: como nomear props — ex. sempre tipadas com interface, nunca type inline]
- [PREENCHER: uso de default props — ex. sempre declarar valores padrão]
- [PREENCHER: regra para componentes genéricos vs específicos]
- Nunca usar índice do array como `key` em listas — sempre usar ID único do item.

### Estilização
- [PREENCHER: abordagem de responsividade — ex. mobile-first / desktop-first]
- [PREENCHER: sistema de design — ex. usar apenas tokens definidos, nunca valores hardcoded]
- [PREENCHER: breakpoints padrão do projeto]
- [PREENCHER: regra para cores — ex. sempre usar variáveis CSS, nunca hex direto no componente]
- Nunca usar `!important` sem comentário justificando.
- Nunca usar valores de pixel hardcoded para espaçamentos — usar escala de design definida.

### Gerenciamento de estado
- [PREENCHER: o que vai para estado global vs estado local]
- [PREENCHER: quando usar Context API vs biblioteca de estado]
- [PREENCHER: convenção de nomenclatura de actions/mutations/stores]
- [PREENCHER: como lidar com estado derivado — ex. sempre com seletores/computed]

### Requisições e dados
- [PREENCHER: onde ficam as chamadas de API — ex. nunca dentro de componentes, sempre em hooks ou services]
- [PREENCHER: como lidar com loading e error states — ex. sempre mostrar feedback ao usuário]
- [PREENCHER: política de cache — ex. stale-while-revalidate, tempo de cache por recurso]
- [PREENCHER: onde ficam os tipos/interfaces das respostas da API]
- Nunca expor tokens ou secrets no código do frontend.
- Variáveis de ambiente públicas prefixadas com: [PREENCHER: ex. VITE_ / NEXT_PUBLIC_ / VUE_APP_]

### Testes
- [PREENCHER: estratégia — ex. testar comportamento do usuário, não implementação]
- Cobertura mínima: [PREENCHER: ex. 70% para componentes críticos]
- [PREENCHER: o que testar em componentes — ex. renderização, interações, estados]
- [PREENCHER: quando usar testes de integração vs unitários]
- [PREENCHER: política para testes E2E — ex. apenas fluxos críticos]
- Convenção de nomes: [PREENCHER: ex. should [comportamento esperado] when [condição]]

### Acessibilidade
- [PREENCHER: nível de conformidade WCAG — ex. AA]
- Sempre usar elementos HTML semânticos — nunca `div` onde existe elemento adequado.
- Todo elemento interativo deve ser acessível via teclado.
- Imagens sempre com `alt` descritivo ou `alt=""` para imagens decorativas.
- [PREENCHER: ferramenta de auditoria — ex. axe-core nos testes / Lighthouse no CI]

### Performance
- [PREENCHER: estratégia de code splitting — ex. lazy loading por rota]
- [PREENCHER: política de otimização de imagens]
- [PREENCHER: métricas Core Web Vitals mínimas aceitas — ex. LCP < 2.5s, CLS < 0.1]
- Nunca importar bibliotecas inteiras quando um import específico resolve.

### Build e qualidade
- Comando para rodar os testes: [PREENCHER: ex. npm test / pnpm test]
- Comando de lint: [PREENCHER: ex. npm run lint]
- Comando de formatação: [PREENCHER: ex. npm run format]
- Comando de build: [PREENCHER: ex. npm run build]
- O build nunca deve ter warnings de TypeScript — tratar como erros.

---

## O que NÃO fazer

> Liste antipadrões específicos da sua stack que o agente deve evitar.

- [PREENCHER: ex. Não usar `any` em TypeScript sem comentário justificando]
- [PREENCHER: ex. Não fazer fetch diretamente dentro de componentes]
- [PREENCHER: ex. Não usar `useEffect` para lógica que poderia ser derivada]
- [PREENCHER: ex. Não commitar arquivos `.env` ou secrets]
- [PREENCHER: ex. Não criar componentes com mais de X linhas]
- [PREENCHER: ex. Não usar `console.log` — remover antes de commitar]
- Nunca usar índice como `key` em listas renderizadas dinamicamente.
- Nunca desabilitar regras de ESLint com `eslint-disable` sem comentário justificando.
