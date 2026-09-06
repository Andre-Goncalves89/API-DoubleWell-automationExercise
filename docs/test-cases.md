# 📋 Especificação de Casos de Teste - Automation Exercise API

Este documento detalha a matriz de testes automatizados implementada para a API do projeto **Automation Exercise**, contemplando cenários de sucesso (caminho feliz), cenários negativos e validação de contratos.

---

## 1. Módulo de Produtos

### **API01: GET - All products List**
* **ID:** CT-API-01
* **Método:** `GET`
* **Endpoint:** `/api/productsList`
* **Objetivo:** Validar o retorno da listagem completa de produtos cadastrados na plataforma e a integridade de seu contrato JSON.
* **Pré-condições:** API online e acessível.
* **Passos:**
  1. Enviar requisição `GET` para o endpoint de listagem de produtos.
* **Resultados Esperados:**
  * Status code retornado deve ser `200 OK`.
  * O corpo da resposta deve conter um array contendo a lista de produtos.
  * Validação de contrato (`JSON Schema Validation`) aprovada com sucesso.

### **API05: POST - Search Product**
* **ID:** CT-API-02
* **Método:** `POST`
* **Endpoint:** `/api/searchProduct`
* **Objetivo:** Validar a busca de um produto específico através de parâmetro enviado no corpo da requisição (`search_product`).
* **Pré-condições:** Existência de produtos cadastrados.
* **Passos:**
  1. Enviar requisição `POST` contendo o parâmetro de busca no corpo (`x-www-form-urlencoded` ou `form-data`).
* **Resultados Esperados:**
  * Status code retornado deve ser `200 OK`.
  * A resposta deve retornar apenas os produtos correspondentes ao termo pesquisado.

---

## 2. Módulo de Usuários e Autenticação (CRUD)

### **API11: POST - Create/Register user Account**
* **ID:** CT-API-03
* **Método:** `POST`
* **Endpoint:** `/api/createAccount`
* **Objetivo:** Validar o cadastro bem-sucedido de uma nova conta de usuário na base de dados.
* **Passos:**
  1. Enviar requisição `POST` com os dados obrigatórios do usuário (nome, e-mail, senha, endereço, etc.).
* **Resultados Esperados:**
  * Status code retornado deve ser `201 Created` (ou `200 OK` conforme o contrato da API).
  * Mensagem de sucesso confirmando a criação da conta.

### **API: POST - Create/Register user Account ALREADY exist**
* **ID:** CT-API-04 (Cenário Negativo)
* **Método:** `POST`
* **Endpoint:** `/api/createAccount`
* **Objetivo:** Validar o comportamento da API ao tentar registrar um usuário utilizando um e-mail já existente na base.
* **Passos:**
  1. Enviar requisição `POST` utilizando dados de um usuário previamente cadastrado.
* **Resultados Esperados:**
  * Status code deve retornar o código de erro adequado (ex: `400 Bad Request` ou `200` com flag de erro).
  * Mensagem informando que o e-mail já está em uso.

### **API07: POST - Verify login with valid email and password**
* **ID:** CT-API-05
* **Método:** `POST`
* **Endpoint:** `/api/verifyLogin`
* **Objetivo:** Validar a autenticação de um usuário utilizando credenciais válidas.
* **Passos:**
  1. Enviar requisição `POST` com e-mail e senha corretos.
* **Resultados Esperados:**
  * Status code `200 OK`.
  * Confirmação de login bem-sucedido no payload de resposta.

### **API13: PUT - Update account**
* **ID:** CT-API-06
* **Método:** `PUT`
* **Endpoint:** `/api/updateAccount`
* **Objetivo:** Validar a atualização bem-sucedida dos dados cadastrais de um usuário existente.
* **Passos:**
  1. Enviar requisição `PUT` alterando os dados permitidos do usuário.
* **Resultados Esperados:**
  * Status code `200 OK`.
  * Confirmação de que os dados foram atualizados com sucesso.

### **API: PUT - Try Update account with invalid email/password**
* **ID:** CT-API-07 (Cenário Negativo)
* **Método:** `PUT`
* **Endpoint:** `/api/updateAccount`
* **Objetivo:** Garantir que a API rejeite atualizações de conta quando submetidas com credenciais inválidas ou não autorizadas.
* **Passos:**
  1. Enviar requisição `PUT` simulando alteração com dados incorretos.
* **Resultados Esperados:**
  * Status code de erro correspondente (`400`/`401`/`404`).
  * Mensagem de falha na validação da conta.

### **API14: GET - User detail by email param**
* **ID:** CT-API-08
* **Método:** `GET`
* **Endpoint:** `/api/getUserDetailByEmail`
* **Objetivo:** Validar a consulta de detalhes de um usuário específico utilizando o e-mail como parâmetro de busca.
* **Passos:**
  1. Enviar requisição `GET` passando o e-mail do usuário nos parâmetros da query.
* **Resultados Esperados:**
  * Status code `200 OK`.
  * Retorno do perfil detalhado do usuário correspondente.

### **API12: DELETE - Delete an exist account**
* **ID:** CT-API-09
* **Método:** `DELETE`
* **Endpoint:** `/api/deleteAccount`
* **Objetivo:** Validar a exclusão bem-sucedida de uma conta de usuário existente, completando o ciclo de CRUD.
* **Passos:**
  1. Enviar requisição `DELETE` informando as credenciais ou dados do usuário a ser removido.
* **Resultados Esperados:**
  * Status code `200 OK`.
  * Confirmação de conta deletada com sucesso.