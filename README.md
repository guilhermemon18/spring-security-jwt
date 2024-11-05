# API USUÁRIOS

**Introdução**

Esta API fornece funcionalidades para gerenciar usuários e suas devidas permissões de acesso na API, por meio do respectivo cadastro de roles para qual está habilitado a acessar.
Ela é construída em Spring Boot e utiliza o banco de dados H2 em memória.

**Como usar a API**

Para utilizar esta API, você precisará de um cliente HTTP como Postman ou Insomnia para fazer as requisições.
Para cadastrar um usuário é possivel definir as roles como "USERS" E/OU "MANAGERS", e assim logar e tentar acessar os recursos da API como: users ou managers, de acordo com a devida permissão dada ao usuário.

**Endpoints**

| Método | URL | Parâmetros | Resposta | Descrição |
|---|---|---|---|---|
| POST | /users | Body: { "name" : "nomeUSER", "username": "notAdmin", "password": "123","roles": ["USERS"]} | - | Cria um novo usuário com as respectivas roles ("USERS" E/OU "MANAGERS") definidas como acesso |
| POST | /login| {Body:  "username": "notAdmin","password": "123"} | JSON ({"login": "notadmin","token": "codigo-acesso-token"}) | Loga o usuário e retorna o token de acesso |
| GET | /users | Headers: {Authorization: token_sem_aspas} | Mensagem ilustrativa da rota ou 403 (forbidden)| Acessa a rota de users se for um usuário com a devida permissão configurada |
| GET | /managers | Headers: {Authorization: token_sem_aspas} | Mensagem ilustrativa da rota ou 403 (forbidden) | Acessa a rota de managers se for um usuário com a devida permissão configurada |
