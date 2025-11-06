# Desafio Técnico — Cadastro de Planos e Beneficiários (FrontEnd Júnior)

## **Atenção: Utilizar o mínimo possível de IA. Isso será verificado e avaliado! Precisamos saber do seu conhecimento, potencial e capacidade.**

## Objetivo

Construir uma aplicação **"Single Page Application" (SPA)** em **Angular** que irá consumir API REST para gerenciar beneficiários e seus planos de saúde, permitindo que os administradores gerenciem o sistema.

> Permissa: Necessário usar **Angular** para esse desafio.

---

## Instruções Gerais

- **Stack obrigatória**: Angular 19 ou 20 (frontend).
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

## Requisitos Técnicos

* **Stack:** Angular (versão 19 ou 20), Angular CLI, TypeScript, HTML, CSS/SCSS.
* **Estrutura:** O projeto deve ser criado com o Angular CLI (`ng new`).
* **Services:** Toda a lógica de chamada HTTP (`HttpClient`) deve ser abstraída em `Services` injetáveis (ex: `BeneficiarioService`, `PlanoService`). Nenhum componente deve chamar o `HttpClient` diretamente.
* **Roteamento (SPA):** A aplicação deve ser uma SPA e conter no mínimo as seguintes rotas:
  * `/beneficiarios`: Lista de beneficiários.
  * `/beneficiarios/novo`: Formulário para criar um novo beneficiário.
  * `/beneficiarios/editar/`:id: Formulário para editar um beneficiário existente.
  * `/planos`: Lista de planos.
  * `/planos/novo`: Formulário para criar um novo plano.
  * `/planos/editar/:id`: Formulário para editar um plano existente.
  * 
---

## Simulação do Back-end
#### Para que você tenha total autonomia, você não irá consumir uma API real. Você usará o json-server para simular 100% do back-end localmente.

#### 1) Crie um arquivo `db.json` na raiz do seu projeto (ou em uma pasta `/mock-api`) com a seguinte estrutura de dados, baseada nos exemplos do desafio de back-end:
```json
{
  "planos": [
    {"id": 1, "nome":"Plano Bronze","codigo_registro_ans":"ANS-100001"},
    {"id": 2, "nome":"Plano Prata","codigo_registro_ans":"ANS-100002"},
    {"id": 3, "nome":"Plano Ouro","codigo_registro_ans":"ANS-100003"}
  ],
  "beneficiarios": [
    {
      "id": 1,
      "nome_completo": "João Pereira",
      "cpf": "11144477735",
      "data_nascimento": "1988-01-10",
      "status": "ATIVO",
      "plano_id": 2,
      "data_cadastro": "2025-01-10T10:30:00Z"
    },
    {
      "id": 2,
      "nome_completo": "Ana Souza",
      "cpf": "98765432100",
      "data_nascimento": "1995-09-03",
      "status": "ATIVO",
      "plano_id": 1,
      "data_cadastro": "2025-02-15T11:00:00Z"
    },
    {
      "id": 3,
      "nome_completo": "Maria Santos",
      "cpf": "10987654321",
      "data_nascimento": "1992-07-22",
      "status": "INATIVO",
      "plano_id": 3,
      "data_cadastro": "2025-03-20T12:45:00Z"
    }
  ]
}
```
#### 2) Instale o `json-server` (ex: `npm install -g json-server` dentro do seu prompt cmd).

#### 3) Na pasta do arquivo `db.json`, rode o comando: `json-server --watch db.json`.

#### 4) Pronto! Você terá uma API RESTful (`http://localhost:3000`) que simula os endpoints abaixo:

#### Planos

* `POST /api/planos` — cria plano
* `GET /api/planos` — lista todos
* `GET /api/planos/{id}` — detalhe
* `PUT /api/planos/{id}` — atualiza
* `DELETE /api/planos/{id}` — remove 

#### Beneficiários

* `POST /api/beneficiarios` — cria beneficiário
* `GET /api/beneficiarios` — listar
* `GET /api/beneficiarios/{id}` — detalhe
* `PUT /api/beneficiarios/{id}` — atualiza 
* `DELETE /api/beneficiarios/{id}` — remove

---
## Funcionalidades (Telas)

### Módulo de Planos (`/planos`)

#### 1)  **Listagem (Tabela):**

* Deve exibir uma tabela com `Nome` e `Código ANS` dos planos.
* Deve ter um botão "Novo Plano" (leva para `/planos/novo`).
* Cada linha deve ter botões "Editar" (leva para `/planos/editar/:id`) e "Excluir".
* O botão "Excluir" deve chamar `DELETE /planos/:id` e atualizar a lista.

#### 2) **Formulário (Criar/Editar):**

* Recomendado o uso de Angular Reactive Forms.
* Deve conter campos para `Nome` e `Código ANS`.
* O componente deve ser reutilizável para "Criar" (`POST`) e "Editar" (`PUT`).
* Ao salvar, deve redirecionar o usuário de volta para a lista.


### Módulo de Beneficiários (`/beneficiarios`)

#### 1)  **Listagem (Tabela):**

* Deve exibir `Nome Completo`, `CPF`, `Data de Nascimento`, `Status` (ATIVO/INATIVO) e o **Nome do Plano**.
  * Desafio: A API (`GET /beneficiarios`) retorna `plano_id`. Você deve exibir o nome do plano, não o ID. (Dica: `json-server` aceita `GET /beneficiarios?_expand=plano`). 

* Deve ter um botão "Novo Beneficiário" (leva para `/beneficiarios/novo`).
* Cada linha deve ter botões **"Editar"** e **"Excluir"**.


#### 2)  **Filtros (Bônus):**

* Implementar dois dropdowns acima da tabela para **filtrar a lista**.
* Um filtro por **Status** (Todos, ATIVO, INATIVO). 
* Um filtro por **Plano** (populado dinamicamente com `GET /planos`).
* Alterar os filtros deve chamar a API novamente (ex: `GET /beneficiarios?status=ATIVO&plano_id=2`).


#### 3)  **Formulário (Criar/Editar):**

* Deve usar **Angular Reactive Forms**.
* Deve conter campos para `Nome Completo`, `CPF`, `Data de Nascimento`.
* **Campo Chave (Plano)**: Deve ser um dropdown (`<select>`) populado dinamicamente com os planos (chamada `GET /planos`). O formulário deve salvar o `plano_id` selecionado.
* Campo Chave (Status): Deve ser um dropdown (`<select>`) com as opções `ATIVO` e `INATIVO`. O padrão de criação deve ser `ATIVO`.

---
## Requisitos de Teste (Unitários)

* **Ferramentas:** Utilize a stack padrão do Angular (Jasmine e Karma).
* **Execução:** Os testes devem rodar com sucesso via `ng test`.

### Cobertura Mínima Esperada:

1.  **Service (Ex: `BeneficiarioService`)**
    * **O que testar:** A lógica de consumo da API.
    * **Como:** Use `HttpClientTestingModule` e `HttpTestingController` para "mockar" as requisições HTTP.
    * **Cenário 1:** Testar se `getBeneficiarios()` realmente chama `GET http://localhost:3000/beneficiarios`.
    * **Cenário 2:** Testar se `createBeneficiario(novoBeneficiario)` chama `POST http://localhost:3000/beneficiarios` com o *payload* (corpo) correto.

2.  **Componente de Formulário (Ex: `BeneficiarioFormComponent`)**
    * **O que testar:** A lógica do componente e as validações do Reactive Form.
    * **Como:** "Mockar" (simular) os `Services` (`BeneficiarioService`, `PlanoService`) e o `Router` para isolar o componente.
    * **Cenário 1 (Validação):** Testar se `form.valid` é `false` quando o componente é iniciado.
    * **Cenário 2 (Validação):** Testar se, ao preencher o `nome_completo` mas deixar o `plano_id` vazio, o `form.valid` continua `false`.
    * **Cenário 3 (Lógica de Salvar):** Testar se, ao chamar o método `salvar()` com o formulário *inválido*, o `BeneficiarioService.createBeneficiario` **não** é chamado.
    * **Cenário 4 (Lógica de Salvar):** Testar se, ao chamar o método `salvar()` com o formulário *válido*, o `BeneficiarioService.createBeneficiario` **é** chamado.

---

## 5. Entrega

### Repositório público (GitHub/GitLab/Azure DevOps) contendo obrigatoriamente:

* **1. Conclusão Funcional (O "CRUD"):**
    * A aplicação permite criar, listar, editar e excluir **Planos**?
    * A aplicação permite criar, listar, editar e excluir **Beneficiários**?

* **2. Abstração de Lógica (Services):**
    * Criação correta de Services

* **3. Fundamentos de Roteamento:**
    * Utilização do `RouterModule`

* **4. Fundamentos de Formulários (Forms):**
    * Utilização de `Reactive Forms` e `Validators.required`

* **5. Organização de Módulos**
    * Utilização correta de `NgModules`

* **6. Execução dos Testes Unitários:**
    * OEntrega dos testes mínimos solicitados (Service e Component Form)?
    * Os testes rodam com sucesso via `ng test`?

* **7. README Básico:**
    * O `README.md` explica, no mínimo, como rodar o projeto (`ng serve`) e o `json-server`?


> ### Como rodar (exemplo esperado no README)
> ### Apresentação e explicação técnica do que foi entregue

---

## 5. Critérios de avaliação (Bônus)

### As opções abaixo que fizer e estiver funcionando no projeto, será utilizada como pontos bônus na sua avaliação

* **Validação de Formulários**
* **Qualidade do Layout (UI)**
* **Lazy Loading**
* **Feedback ao Usuário**
* **Tratamento de Erros**
* **Containerização (Docker) - (Bônus Forte)**
