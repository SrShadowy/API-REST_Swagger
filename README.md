## Esse Repositorio foi fruto de um Desafio Back-End

#### Requisitos Gerais:

Uma livraria da cidade teve um aumento no número de seus exemplares e está com um problema para identificar todos os livros que possui em estoque.
Para ajudar a livraria foi solicitado a você desenvolver uma aplicação web para gerenciar estes exemplares. Requisitos:

* O sistema deverá mostrar todos os livros cadastrados ordenados de forma ascendente pelo nome.
* Ao persistir, validar se o livro já foi cadastrado.
* O sistema deverá permitir consultar, criar, editar e excluir um livro.
* Os livros devem ser persistidos em um banco de dados.
* Criar algum mecanismo de log de registro e de erro.


## Nesse Caso eu fiz essa API:

###### É possível utilizar com DOCKER COMPOSER!

É só da up no *docker-compose.yml*

---


###### Oque é possivel fazer com essa api:

Ela é uma livraria, isso é uma plataforma de bibliotecas.

Tendo isso como uma ideia o usuário, pode listar os livros da biblioteca.

---



###### Regras:

###### [Anonimos]

O todos usuário mesmo deslogado consegue listar todos os livros.

###### [Usuários comuns]

Usando o token de autenticação, consegue listar os livros por Nome e ID e primariamente ID caso queira pesquisar com o argumento (Title)EoTituloEmQuestão.

###### [ADMINISTRADOR]

Esse token, tem o poder de tudo, editar, apagar e inserir.

---




### BANCO DE DADOS:

O banco de dado é o SQLServer usando em DOCKER, eo Armazenamento em DISCO na pasta \db do projeto.

---
