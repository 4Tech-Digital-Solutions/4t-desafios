# Desafio Técnico — Full Stack Pleno

## Instruções Gerais

- Faça um **fork** do código existente no [repositório](https://github.com/4Tech-Digital-Solutions/cadastro-beneficiarios-desafio)
- **Stack obrigatória**: .NET Core 9 (backend) e Angular 18+ (frontend).
- Caso não finalize todos os requisitos, documente claramente o que foi implementado e o que ficou pendente.
- Entregue um **README** com passo a passo completo para executar a aplicação localmente.
- Após finalizar, envie o link do fork e aguarde nossa avaliação.

---

## Entrevista Técnica

Após a entrega, você será convocado para uma **entrevista técnica** onde irá apresentar a aplicação rodando em sua máquina local. Nessa sessão:

- Faremos **code review** colaborativo como se você já fosse parte do time.
- Discutiremos **decisões de arquitetura**, trade-offs e padrões aplicados.
- Você explicará seu raciocínio e como evoluiria o projeto.

> **Dica do mentor:** Não altere o código após a entrega. Mantenha-o funcional e preparado para demonstração ao vivo. Caso não tenha finalizado, aproveite o momento para argumentar sobre suas decisões, dificuldades encontradas.

---

## Conselho do Mentor

Este desafio avalia sua capacidade de:

- Trabalhar com **código legado** e identificar pontos de melhoria.
- **Reestruturar** APIs para aplicar padrões de projeto adequados.
- Implementar **novas funcionalidades** com base em requisitos técnicos.
- Tomar **decisões fundamentadas** quando não há todas as respostas explícitas.

Use **IA com moderação**. Queremos avaliar **seu raciocínio** e capacidade de explicar escolhas na entrevista técnica.

---

## Objetivo: Sistema de Cadastro de Beneficiários e Planos

Você deve evoluir o sistema baseado no desafio [backend-jr](backend-jr.md). Antes de implementar as novas funcionalidades:

1. **Revise o código base** e garanta que está funcional.
2. **Complete o CRUD** caso algo esteja faltando.
3. **Refatore** a API aplicando **padrões de projeto**.

> **Dica do mentor:** Avalie a estrutura atual da API. Ela está seguindo as melhores práticas? Como você melhoraria a separação de responsabilidades? A refatoração é parte importante da avaliação.

---

## Front-end (Angular)

Desenvolva uma **aplicação web** com as seguintes funcionalidades:

### Funcionalidades Obrigatórias

#### Beneficiários
- **Cadastro** de novo beneficiário.
- **Listagem** com filtros (status, plano).
- **Atualização** de beneficiário existente.
- **Exclusão** (deve marcar como pendente, não excluir imediatamente).

#### Planos
- **Cadastro** de novo plano.
- **Listagem** de planos.
- **Edição** de plano existente.
- **Exclusão** com validação de vínculo:
  - Não permitir se houver beneficiários vinculados.
  - Registrar exclusões bem-sucedidas em log/auditoria.

### Requisitos Técnicos

- **Integração completa** com a API .NET Core.
- **Validações** nos formulários.
- **Feedback visual** (mensagens de sucesso/erro, loading states).
- **Tabelas** com paginação, ordenação e filtros.
- **Componentização** adequada e reuso de código.

> **Dica do mentor:** Organize seu código Angular seguindo as convenções da comunidade. Use services para chamadas HTTP, interceptors para tratamento global de erros, e considere usar bibliotecas UI (Angular Material, PrimeNG, etc.) para acelerar o desenvolvimento.

---

## Back-end (.NET Core 9)

### 1) Garantir Funcionalidades Base

Revise e implemente **todas as funcionalidades** descritas em [backend-jr.md](backend-jr.md):

- CRUD completo de **Planos**.
- CRUD completo de **Beneficiários**.
- Validações (CPF único, vínculo com plano existente).
- Tratamento de erros padronizado.
- Documentação Swagger/OpenAPI.

> **Dica do mentor:** Se a API atual está desorganizada, este é o momento de aplicar padrões como Repository Pattern, Testes de Unidade, etc.

---

### 2) Novas Funcionalidades

#### A) Exclusão Suave de Beneficiários com Worker

A exclusão de beneficiários **não deve ser imediata**. Implementar:

1. **Endpoint de solicitação de exclusão** (`DELETE /api/beneficiarios/{id}`):
   - Não exclui fisicamente.
   - Marca o beneficiário com flag  de pendente de exclusão.
   - Atribui uma **prioridade** (1, 2 ou 3).
   - Registra data de solicitação de exclusão.

2. **Worker/Background Service**:
   - Executar a cada **1 minuto**.
   - Processar beneficiários pendentes **em ordem de prioridade** (1 < 2 < 3).
   - Para mesma prioridade, processar por ordem cronológica (data de solicitação de exclusão).
   - Realizar a exclusão física do registro.
   - Logar as exclusões processadas.

> **Dica do mentor:** Se não conhecer o conceito de Worker/Background Service, comece por [aqui](https://learn.microsoft.com/en-us/dotnet/core/extensions/workers) para entender os conceitos. Implemente logs estruturados para rastrear as exclusões.

---

## Critérios de Avaliação

Vamos avaliar especialmente:

### 1) Arquitetura e Padrões de Projeto
- Organização do projeto.
- Aplicação de Design Patterns adequados.
- Separação de responsabilidades.

### 2) Qualidade do Código Backend
- Código limpo e legível.
- Tratamento de erros e logs estruturados.
- Worker funcionando corretamente (lógica de prioridades).

### 3) Desenvolvimento Front-end

### 4) Capacidade de Leitura de Requisitos
- Implementação completa das funcionalidades descritas.
- Decisões técnicas fundamentadas.
- Capacidade de preencher lacunas com boas práticas.

### 5) Documentação
- README executável (comandos claros).
- Swagger configurado e funcional.
- Decisões arquiteturais documentadas.

> **Dica do mentor:** Seu código será revisado como se você já fizesse parte do time. Priorize clareza, manutenibilidade e boas práticas ao invés de soluções complexas sem necessidade. Na entrevista, saiba explicar suas escolhas.

---
## Observações Finais

- Este desafio simula um cenário real: código legado + novos requisitos.
- **Não há uma única solução correta**. Avaliamos o processo de decisão e a qualidade da implementação.
- **Dúvidas razoáveis são esperadas**. Tome decisões fundamentadas e documente-as.
- Na entrevista, você terá oportunidade de explicar e defender suas escolhas.

> **Dica do mentor:** Organize seu tempo. Priorize ter algo funcional end-to-end antes de refinar detalhes. Uma aplicação funcionando com código razoável é melhor que uma aplicação perfeita pela metade. Boa sorte!