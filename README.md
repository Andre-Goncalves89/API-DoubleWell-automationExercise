# 🧪 Automation Exercise - API Testing Suite

> Suite automatizada de testes de API desenvolvida com foco em qualidade de software, abrangendo validação de contratos, cenários negativos e ciclo completo de CRUD.

---

## 🛠️ Tecnologias Utilizadas
* **Postman:** Design e desenvolvimento dos cenários de teste e scripts de asserção.
* **Newman:** CLI runner oficial do Postman para execução via linha de comando.
* **JavaScript / Chai:** Validações lógicas e assertions customizadas.
* **Git & GitHub:** Versionamento de código e controle de configuração.

---

## 📁 Estrutura do Projeto
```text
.
├── collections/
│   └── Automation Exercise API.postman_collection.json
├── environment/
│   └── AutomationExercise - dev API.postman_environment.json
├── docs/
│   └── test-cases.md
├── ROADMAP.md
└── README.md
```
---

## ⚙️ Como Executar o Projeto
### Pré-requisitos
Certifique-se de ter o Node.js e o Newman instalados em sua máquina:
```bash
npm install -g newman
```
---
```bash
git clone https://github.com/Andre-Goncalves89/API-DoubleWell-automationExercise.git
```

## Executando os testes via Newman (CLI)
Na raiz do repositório, execute o comando abaixo para rodar a collection utilizando o arquivo de ambiente de desenvolvimento:
```bash
newman run collections/"Automation Exercise API.postman_collection.json" -e environment/"AutomationExercise - dev API.postman_environment.json"
```
---

## 📋 Documentação
Consulte a pasta docs/test-cases.md para visualizar a matriz detalhada de casos de teste mapeados nesta suíte.
---
