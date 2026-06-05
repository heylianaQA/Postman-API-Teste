# 🛒 ServeRest API - Testes Automatizados

> Projeto de testes automatizados de API para a aplicação [ServeRest](https://github.com/ServeRest/ServeRest), utilizando **Postman**, **Newman** e **GitHub Actions** para execução contínua em pipeline CI/CD.

![CI](https://github.com/heylianaQA/Postman-API-Teste/actions/workflows/newman.yaml/badge.svg)
![Postman](https://img.shields.io/badge/tested%20with-Postman-orange?logo=postman)

---

## 📋 Sobre o Projeto

O ServeRest é uma API REST gratuita voltada para estudos de testes de software. Este projeto cobre os principais fluxos da aplicação por meio de testes automatizados organizados por módulo funcional, com geração de relatório HTML ao final de cada execução.

---

## 🗂️ Estrutura do Projeto

```
POSTMAN-API-TESTE/
├── Collections/
│   └── ServeRest API.postman_collection.json
├── Environments/
│   └── ServeRest - localhost.postman_environment.json
├── Pipeline/
│   └── .github/workflow/
│       └── newman.yaml
├── Reports/
│   └── report.html
├── package.json
└── README.md
```

---

## 🧪 Cobertura de Testes

### 👤 Gestão de Usuários — `/usuarios`

| Cenário | Método | Status Esperado |
|---|---|---|
| Cadastro de usuário normal | POST | 201 |
| Cadastro de usuário administrador | POST | 201 |
| Erro ao cadastrar com e-mail já existente | POST | 400 |
| Listar usuários cadastrados | GET | 200 |
| Buscar usuário por ID | GET | 200 |
| Alteração de dados do usuário | PUT | 200 |
| Exclusão de cadastro do usuário | DELETE | 200 |

### 🔐 Login — `/login`

| Cenário | Método | Status Esperado |
|---|---|---|
| Login bem-sucedido | POST | 200 |
| Erro por e-mail inválido (sem @) | POST | 400 |
| Erro por senha incorreta | POST | 401 |

### 📦 Gestão de Produtos — `/produtos`

| Cenário | Método | Status Esperado |
|---|---|---|
| Listar produtos cadastrados | GET | 200 |
| Buscar produto por ID | GET | 200 |
| Erro ao cadastrar produto sem token | POST | 401 |
| Cadastrar produto (autenticado) | POST | 201 |
| Editar dados do produto | PUT | 200 |
| Exclusão de produto | DELETE | 200 |

### 🛒 Gestão de Carrinhos — `/carrinhos`

| Cenário | Método | Status Esperado |
|---|---|---|
| Listar carrinhos cadastrados | GET | 200 |
| Buscar carrinho por ID | GET | 200 |

> ⚠️ **Observação:** Como o ServeRest é uma API com estado compartilhado e limitações nos endpoints de carrinho, alguns cenários de criação e exclusão de carrinho não foram cobertos para evitar inconsistências durante a execução do pipeline.

---

## 🔧 Pré-requisitos

- [Node.js](https://nodejs.org/) v22+
- [Newman](https://www.npmjs.com/package/newman) v6+
- [newman-reporter-htmlextra](https://www.npmjs.com/package/newman-reporter-htmlextra)

---

## ▶️ Como Rodar Localmente

**1. Clone o repositório:**
```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

**2. Instale as dependências:**
```bash
npm install
```

**3. Suba o ServeRest localmente:**
```bash
npx serverest
```

**4. Em outro terminal, execute os testes:**
```bash
npx newman run "Collections/ServeRest API.postman_collection.json" \
  -e "Environments/ServeRest - localhost.postman_environment.json" \
  -r htmlextra \
  --reporter-htmlextra-export "Relatório/report.html"
```

**5. Abra o relatório gerado:**
```
Relatório/report.html
```

---

## ⚙️ Pipeline CI/CD — GitHub Actions

O pipeline é disparado automaticamente a cada **push** ou **pull request** e realiza os seguintes passos:

1. Checkout do repositório
2. Configuração do Node.js v22
3. Instalação das dependências (`npm install`)
4. Inicialização do ServeRest em background
5. Execução dos testes com Newman
6. Upload do relatório HTML como artifact do workflow

O relatório pode ser baixado na aba **Actions** do repositório após cada execução, em **Artifacts → newman-report**.

---

## 📦 Dependências

```json
{
  "dependencies": {
    "newman": "^6.2.2",
    "serverest": "^3.2.0"
  },
  "devDependencies": {
    "newman-reporter-htmlextra": "^1.23.1"
  }
}
```

---

## 🌐 Variáveis de Ambiente

| Variável | Valor |
|---|---|
| `baseUrl` | `http://localhost:3000/` |
| `Authorization` | Token JWT gerado no login |

---

## 📄 Tecnologias Utilizadas

- [Postman](https://www.postman.com/) — criação e organização das requisições
- [Newman](https://www.npmjs.com/package/newman) — execução das collections via linha de comando
- [newman-reporter-htmlextra](https://www.npmjs.com/package/newman-reporter-htmlextra) — geração de relatório HTML detalhado
- [ServeRest](https://github.com/ServeRest/ServeRest) — API REST utilizada como alvo dos testes
- [GitHub Actions](https://github.com/features/actions) — pipeline de integração contínua

## 👩‍💻 Autora

**Ana Inocêncio**
[LinkedIn](https://www.linkedin.com/in/heyana-inocencio/) - heyliana.qa@gmail.com