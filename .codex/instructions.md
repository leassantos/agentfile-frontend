# Contexto estendido — [NOME DO PROJETO]

> Este arquivo complementa o AGENTS.md com contexto arquitetural mais profundo.
> O agente consulta isso para tomar decisões consistentes com o que já foi definido.
> Preencha conforme o projeto evolui — não precisa estar completo no dia 1.

---

## Decisões arquiteturais registradas

> Para cada decisão importante, documente o "por quê", não apenas o "o quê".
> Isso evita que o agente reverta decisões já tomadas.

### [PREENCHER: nome da decisão — ex. Por que Zustand e não Redux?]
[PREENCHER: contexto e justificativa da decisão]

### [PREENCHER: outra decisão — ex. Por que CSS Modules e não Tailwind?]
[PREENCHER: justificativa]

---

## Estrutura de pastas do projeto

> Documente a estrutura adotada para o agente seguir consistentemente.
> Ajuste conforme a organização real do seu projeto.

```
src/
├── assets/          # Imagens, fontes, ícones estáticos
├── components/      # Componentes globais reutilizáveis
│   ├── ui/          # Componentes base (Button, Input, Modal...)
│   └── layout/      # Estruturas de layout (Header, Sidebar...)
├── features/        # Módulos de feature (cada feature é autocontida)
│   └── [feature]/
│       ├── components/   # Componentes específicos da feature
│       ├── hooks/        # Hooks específicos da feature
│       ├── services/     # Chamadas de API da feature
│       ├── store/        # Estado da feature (se aplicável)
│       └── types/        # Tipos TypeScript da feature
├── hooks/           # Hooks globais reutilizáveis
├── services/        # Serviços globais (api client, auth...)
├── store/           # Estado global
├── styles/          # Estilos globais, tokens, variáveis
├── types/           # Tipos globais e interfaces da API
└── utils/           # Funções utilitárias puras
```

> ✏️ Adapte a estrutura acima à realidade do seu projeto antes de usar.

---

## Módulos/features planejados

> Liste as features do projeto em ordem de prioridade.
> Marque o status de cada uma para o agente saber o que já existe.

| Feature | Status | Descrição |
|---------|--------|-----------|
| [PREENCHER] | Em desenvolvimento | [PREENCHER] |
| [PREENCHER] | Planejado | [PREENCHER] |
| [PREENCHER] | Planejado | [PREENCHER] |

---

## API e integração com backend

> Documente como o frontend se comunica com a API.

### URL base
```
[PREENCHER: ex. VITE_API_URL=https://api.meu-projeto.com]
```

### Autenticação
[PREENCHER: como o token é armazenado e enviado — ex. localStorage + header Authorization Bearer]

### Formato padrão de response esperado do backend
```json
[PREENCHER: cole aqui o formato de sucesso que o backend retorna]
```

```json
[PREENCHER: cole aqui o formato de erro que o backend retorna]
```

### Endpoints consumidos

| Método | Path | Descrição | Feature |
|--------|------|-----------|---------|
| [PREENCHER] | [PREENCHER] | [PREENCHER] | [PREENCHER] |

---

## Variáveis de ambiente esperadas

```
[PREENCHER: NOME_DA_VAR]=<descrição do valor esperado>
[PREENCHER: OUTRA_VAR]=<descrição>
```

---

## Sistema de design

> Documente os tokens de design para o agente usar valores corretos.

### Cores principais
```
[PREENCHER: ex. --color-primary: #0066CC]
[PREENCHER: ex. --color-danger: #DC2626]
```

### Tipografia
```
[PREENCHER: ex. fonte principal, escala de tamanhos]
```

### Breakpoints
```
[PREENCHER: ex. sm: 640px / md: 768px / lg: 1024px / xl: 1280px]
```

---

## Contexto de negócio

> Explique termos do domínio que o agente precisa conhecer para nomear componentes e variáveis corretamente.

- **[PREENCHER: termo do domínio]**: [PREENCHER: definição]
- **[PREENCHER: outro termo]**: [PREENCHER: definição]
