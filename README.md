# Desafio Back-End ASP.NET CORE SWAGGER UI

#### Requisitos Gerais:

Uma livraria da cidade teve um aumento no número de seus exemplares e está com um problema para identificar todos os livros que possui em estoque.

Para ajudar a livraria foi solicitado a você desenvolver uma aplicação web para gerenciar estes exemplares. Requisitos:

* O sistema deverá mostrar todos os livros cadastrados ordenados de forma ascendente pelo nome.
* Ao persistir, validar se o livro já foi cadastrado.
* O sistema deverá permitir consultar, criar, editar e excluir um livro.
* Os livros devem ser persistidos em um banco de dados.
* Criar algum mecanismo de log de registro e de erro.

## A API:

###### É possível utilizar com DOCKER-COMPOSE!

É só da up no *docker-compose.yml*

---

###### O'Que é possível fazer com essa api:

Basicamente é um CRUD de uma livraria, é possível: Listar, Editar, Adicionar e Deletar.

---

###### Regras:

Autenticação usando Token JWT (Bearer).

Cada usuário pode obter 1 cargo de dois sendo eles *ADMIN* e *USER*.

Caso não venha nenhum token esse usuário será considerado anônimo.

Segue abaixo todas permissões disponíveis:

###### [Anônimos] (TODOS)

É possível fazer um REQUEST GET básico, que irá listar todos os livros.

###### [Usuários logados] (CONSISTEM EM UM LOGIN TANTO DE UM ADMINISTRADOR COMO USUÁRIO)

O GET Fornecido permitem a listagem por **ID** ou **título** do livro em questão usando apenas o número para indicar o ID e o parâmetro (title) para o título.

Segue o exemplo:

Busca por ID:

`/api/Book/1`

Retornará o livro pertencente ao ID 1.

Retorno:

```json
{  
    "id":1,  
    "title": "A Filosofia na Idade Trágica dos Gregos",   
    "saga": "Pensamento",  
    "description": "Nesta obra, o autor busca revelar a polifonia que vê no pensamento grego a partir de pequenos ensaios sobre filósofos como Tales de Mileto, Anaximandro, Heráclito, Parmênides e Anaxágoras. Este livro apresenta a reflexão de Nietzsche sobre o espírito filosófico de seu tempo, sobre a ciência e o homem, reafirmando que o maior legado dos pré-socráticos é a liberdade de pensar por si mesmo",  
    "author": "Friedrich Nietzsche",  
    "date": "Escrito entre 1873 e 1874"  
}
```

Busca por título:

`/api/Book/(title)Caixa`

Retornará todos os livros que contém no título a palavra "Caixa".

```json
{

    {
        "id":2,
        "title": "Caixa de Pássaros: Não abra os olhos",
        "saga": "",
        "description": "Romance de estreia de Josh Malerman, Caixa de pássaros é um thriller psicológico tenso e aterrorizante, que explora a essência do medo",
        "author": "Josh Malerman",
        "date": "26 janeiro 2015"

    },
    {

        "id":10,
        "title": "O mistério da caixa vermelha",
        "saga": "",
        "description": "Uma caixa vermelha aparece no meio da rua. Cada pessoa que a vê (um executivo, uma jovem com seu cãozinho, um idoso e uma criança) experimenta um sentimento e mostra uma reação.",
        "author": " Semíramis Paterno",
        "date": "1 janeiro 2008"

    },
...
}

```

###### [ADMINISTRADOR] (APENAS COM O TOKEN DE ADMINISTRADOR)

O Administrador, tem acesso a adição, edição, listagem (como as anteriores) e exclusão.

Segue os exemplos abaixo:

* Adição (POST), autenticado como administrador passando o **token** na requisição é necessário informar o campo do corpo em **JSON** com os dados **id, title, saga, description, author e date**:

  URL: `/api/Book/`

  *Corpo da requisição JSON:*

  ```json
  {
    "id":1,
    "title": "A Filosofia na Idade Trágica dos Gregos",
    "saga": "Pensamento",
    "description": "Nesta obra, o autor busca revelar a polifonia que vê no pensamento grego a partir de pequenos ensaios sobre filósofos como Tales de Mileto, Anaximandro, Heráclito, Parmênides e Anaxágoras. Este livro apresenta a reflexão de Nietzsche sobre o espírito filosófico de seu tempo, sobre a ciência e o homem, reafirmando que o maior legado dos pré-socráticos é a liberdade de pensar por si mesmo",
    "author": "Friedrich Nietzsche",
    "date": "Escrito entre 1873 e 1874"
    }
  ```

* Edição (PUT), autenticado como administrador passando o **token** na requisição é necessário com o parâmetro na **URL** informando o **ID** do livro em questão:

  URL:  `/api/Book/5`

 *Corpo da requisição JSON:*

  ```json
{
    "id":5,
    "title": "O Poder do Hábito",
    "saga": "",
    "description": "Charles Duhigg, repórter investigativo do New York Times, mostra que a chave para o sucesso é entender como os hábitos funcionam - e como podemos transformá-los.",
    "author": "Charles Duhigg",
    "date": "24 setembro 2012"
}
  ```


* Exclusão (DELETE), autenticado como administrador passando o **token** na requisição é necessário com o parâmetro na **URL** informando o **ID** do livro em questão:

  URL: `/api/Book/5`

---

### BANCO DE DADOS:

O banco de dados é o **SQL Server** utilizando em **Docker**, e o **armazenamento em disco** na pasta **\db** do projeto.

---

