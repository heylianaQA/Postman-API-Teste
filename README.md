# Testes de API com Postman - ServeRest Users

Projeto de testes automatizados focado na API de usuários do ServeRest utilizando Postman.

## 💡 Sobre o Projeto

Suite de testes automatizados para validar operações CRUD na API de usuários do ServeRest, garantindo a integridade das operações de listagem, busca, cadastro, edição e exclusão.

## 🛠️ Tecnologias Utilizadas

- Postman - Plataforma de testes de API
- ServeRest - API de testes
- Newman (opcional) - Executor de testes via CLI

## 📋 Testes Implementados

- Listagem de usuários cadastrados
- Validação de usuário duplicado
- Busca de usuário por ID
- Validação de erro na exclusão
- Edição de cadastro

## 🚀 Como Executar

1. Instale o ServeRest:
```bash
npm install -g serverest
```

2. Inicie o ServeRest:
```bash
npx serverest
```

3. Importe a collection no Postman

4. Execute a collection de testes

## ⚙️ Pré-requisitos

- ServeRest instalado
- Postman Desktop instalado OU extensão "Postman" no VSCode
- Porta local disponível (normalmente 3000)

## 💻 Ambiente de Teste

Você pode escolher entre duas opções para executar os testes:

1. **Postman Desktop**
   - Interface completa do Postman
   - Recomendado para desenvolvimento extensivo de testes

2. **Plugin Postman no VSCode**
   - Integração direta no VSCode
   - Ideal para quem já utiliza o VSCode como ambiente principal
   - Oferece as mesmas funcionalidades essenciais para execução dos testes

## 📝 Notas Importantes

- ServeRest deve estar em execução durante os testes
- Os testes são independentes e podem ser executados isoladamente
- Ambiente local configurado na collection

## 🤝 Contribuição

Contribuições são bem-vindas!

