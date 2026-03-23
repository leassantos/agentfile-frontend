# Prompt template: plan mode (nova feature)

> Como usar: cole este arquivo inteiro em uma nova task do Codex.
> Substitua apenas o bloco "Feature solicitada" antes de enviar.
> NÃO modifique o restante — ele instrui o agente a trabalhar corretamente.

---

## Instruções para o agente

Antes de escrever qualquer código, gere um plano detalhado para a feature descrita abaixo.
**NÃO implemente nada ainda.** Apresente o plano completo e aguarde minha aprovação explícita.

### Feature solicitada

<!-- ✏️  SUBSTITUA ESTE BLOCO ANTES DE ENVIAR -->
[DESCREVA AQUI O QUE PRECISA SER IMPLEMENTADO]
<!-- Inclua: quais telas/componentes, comportamentos esperados, integrações com API, estados de loading/erro -->

---

### Contexto do projeto
- Leia o arquivo `AGENTS.md` na raiz do projeto para as regras obrigatórias.
- Leia o arquivo `.codex/instructions.md` para o contexto arquitetural, sistema de design e decisões já tomadas.
- Analise os componentes e padrões já existentes — siga o que já está estabelecido antes de propor algo novo.

### O plano deve conter obrigatoriamente

**1. Entendimento da feature**
- O que o usuário vê e pode fazer nessa feature?
- Quais são os fluxos principais (happy paths)?
- Quais são os estados intermediários: loading, erro, vazio, sucesso?
- Há animações ou transições esperadas?
- Há ambiguidades que precisam ser esclarecidas antes de começar?

**2. Impacto no projeto existente**
- Quais componentes existentes serão reutilizados?
- Quais componentes existentes serão modificados?
- Quais componentes novos serão criados?
- Há mudanças necessárias no estado global?
- Há novas rotas a adicionar?
- Há novos endpoints de API a consumir?

**3. Estrutura proposta**
- Liste cada arquivo a ser criado ou modificado com sua responsabilidade.
- Mostre a interface de props de cada componente novo (sem implementação).
- Mostre a estrutura de estado se houver store/context novo.
- Indique onde cada arquivo ficará na estrutura de pastas.

**4. Plano de testes**
- Quais interações do usuário serão testadas?
- Quais estados (loading, erro, sucesso, vazio) serão cobertos?
- Há necessidade de mock de API? Como será feito?
- Algum fluxo crítico que precisa de teste E2E?

**5. Considerações de acessibilidade**
- Há elementos interativos que precisam de suporte a teclado?
- Há imagens que precisam de texto alternativo?
- Há feedback para leitores de tela (aria-live, aria-label)?

**6. Considerações de performance**
- Há listas longas que precisam de virtualização?
- Há assets pesados que precisam de lazy loading?
- Há operações custosas que precisam de memoização?

**7. Estimativa de complexidade**
- Baixa / Média / Alta — com justificativa.

---
Após apresentar o plano completo, aguarde minha aprovação antes de qualquer implementação.
Se houver dúvidas ou ambiguidades, liste-as antes do plano.
