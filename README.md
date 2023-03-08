# fakeApiTeamSixCourses

Projeto front-end Módulo 3 Turma 15 grupo 6

<a href="https://insomnia.rest/run/?label=API%20fake%20Team%20Six%20&uri=https%3A%2F%2Fgithub.com%2FTeam-Six-Courses%2FfakeApiTeamSixCourses%2Fblob%2Fmain%2FInsomnia_2023-03-07.json" target="_blank"><img src="https://insomnia.rest/images/run.svg" alt="Run in Insomnia"></a>

<h1>Documentação do Team Six</h1>

url base: 'https://teamsixfilms.onrender.com'

<h2>Usuário</h2>

`POST` Para fazer o register use a rota `/register`, requer um corpo:

```json
{
  "email": "test@mail.com",
  "password": "123456",
  "avatar": null,
  "name": "Test"
}
```

Retorno:

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InZhbGRvQG1haWwuY29tIiwiaWF0IjoxNjc4MjUzMTU2LCJleHAiOjE2NzgyNTY3NTYsInN1YiI6IjIifQ.eWRHLY5KHIiybrqpnKf_Xd5Bun6lToXPlv5-x1kYIB8",
  "user": {
    "email": "test@mail.com",
    "avatar": null,
    "name": "Test",
    "id": 2
  }
}
```

`POST` Para fazer o login use a rota `/login`, requer um corpo:

```json
{
  "email": "test@mail.com",
  "password": "123456"
}
```

Retorno:

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InZhbGRvQG1haWwuY29tIiwiaWF0IjoxNjc4MjUzMTU2LCJleHAiOjE2NzgyNTY3NTYsInN1YiI6IjIifQ.eWRHLY5KHIiybrqpnKf_Xd5Bun6lToXPlv5-x1kYIB8",
  "user": {
    "email": "test@mail.com",
    "avatar": null,
    "name": "Test",
    "id": 2
  }
}
```

`GET` Para captura as informações do usuário usse a rota `users/id?_embed=posts&_embed=likePost&_embed=likeComment`, nessecida de token:

Retorno:

```json
{
  "email": "test@mail.com",
  "password": "$2a$10$65T7WoPvQBZhPFeyjcJBbeC3EKxJGhgWG1d0VMMwYT2p8nT6eQGHe",
  "avatar": null,
  "name": "Test",
  "id": 2,
  "posts": [],
  "likePost": [],
  "likeComment": []
}
```

`PATCH` Para atualizar o usuário use essa rota `/user/id`, nessecita de token e de um corpo:

```json
{
  "name": "TestEdit",
  "avatar": null
}
```

Retorno:

```json
{
  "email": "Test@mail.com",
  "password": "$2a$10$MzKu59e76XKDDh8gnVwOcudokLL.4rU5ElpEUgfXbo1s8B37AbPP6",
  "avatar": null,
  "name": "TestEdit",
  "id": 3
}
```

`DELETE` Para deletar um usuário usse esa rota `/users/id`, nessecita de token:

Não retorna nada

<h2>Post</h2>

`POST` Para adicionar um post use essa rota `/posts`, nessecita de um token e de um corpo:

```json
{
  "title": "Teoria de dimenção do amor",
  "description": "A dimensão do amor",
  "userId": 1,
  "like": 0
}
```

Retorno:

```json
{
  "title": "Teoria de dimenção do amor",
  "description": "A dimensão do amor",
  "userId": 1,
  "like": 0,
  "id": 2
}
```

`GET` Para capturar o post use essa rota `/posts?_expand=user&_embed=comments&_embed=likePost`, nesse cita de token:

Retorno:

```json
{
  "title": "Teoria de dimenção do amor",
  "description": "A dimensão do amor",
  "userId": 1,
  "like": 0,
  "id": 2,
  "comments": [],
  "likePost": [],
  "user": {
    "email": "vinicius@mail.com",
    "password": "$2a$10$zqUIReAbpchBiUopdA1ezOPakDU41xUtJYJzpdoN4GcLsojRfgXpS",
    "avatar": null,
    "name": "Vinicius",
    "id": 1
  }
}
```

`GET` Para capturar as postagens de filmes expecificos use essa rota `/posts?filmsId=1&_expand=user&_embed=likePost`:

Retorno:

```json
{
  "title": "Final do Filme - Teoria",
  "description": "Teria aqui!",
  "userId": 1,
  "filmsId": 1,
  "id": 1,
  "likePost": [],
  "user": {
    "email": "vinicius@mail.com",
    "password": "$2a$10$zqUIReAbpchBiUopdA1ezOPakDU41xUtJYJzpdoN4GcLsojRfgXpS",
    "avatar": null,
    "name": "Vinicius",
    "id": 1
  }
},
{
  "title": "Teoria de dimenção do amor",
  "description": "A dimensão do amor",
  "userId": 1,
  "filmsId": 1,
  "id": 2,
  "likePost": [],
  "user": {
    "email": "vinicius@mail.com",
    "password": "$2a$10$zqUIReAbpchBiUopdA1ezOPakDU41xUtJYJzpdoN4GcLsojRfgXpS",
    "avatar": null,
    "name": "Vinicius",
    "id": 1
  }
} 
```

`POST` Para dar like no post use essa rota `/likePost`, nessecita do um token e de um corpo:

```json
{
  "userId": 2,
  "postId": 2
}
```

Retorno:

```json
{
  "userId": 2,
  "postId": 2,
  "id": 3
}
```

`PATCH` Para editar o post use essa rota `/posts/id`, nessecita de um token e de um corpo onde o description e o title são opcionais:

```json
{
  "description": "Teoria alterada",
  "title": "Titulo alterado"
}
```

`DELETE` para deletar o post use essa rota `/posts/id`, nessecita de um token:

Não retorna nada.

<h2>Comentários</h2>

`GET` Para capturar todo os comentários da web use a rota `/comments?_embed=likeComment`, nessecita de token:

Retorno:

```json
[
  {
    "postId": 1,
    "comment": "Comentário teste",
    "userId": 1,
    "id": 1,
    "likeComment": []
  },
  {
    "postId": 1,
    "comment": "Sim, verdade",
    "userId": 2,
    "id": 2,
    "likeComment": []
  }
]
```

`POST` Para adicionar os comentários use essa rota `/comments`, nessecita de token e de um corpo:

```json
{
  "postId": 1,
  "comment": "Comentário",
  "userId": 2
}
```

Retorno:

```json
{
  "postId": 1,
  "comment": "Comentário",
  "userId": 2,
  "id": 2
}
```

`POST` Para poder curtir um comentário use essa rota `likeComent`, nessecita de corpo:

```json
{
  "userId": 2,
  "commentId": 2
}
```

Retorno:

```json
{
  "userId": 2,
  "commentId": 2,
  "id": 2
}
```

`PATCH` Para o usuário editar o próprio comentário use essa rota `comments/id`, nessecida de corpo:

```json
{
  "comment": "comentário editado"
}
```

Retorno:

```json
{
  "postId": 1,
  "comment": "comentário editado",
  "userId": 2,
  "id": 2
}
```

`DELETE` Para um usuário deleta o próprio comentário use essa rota `comments/id`, nessecita de token:

Não retorna nada.

<h2>Filmes</h2>
<p>Ainda em produção</p>

`GET` Para capturar os filmes use a rota `/films?_embed=posts`

Retorno:

```json
[
  {
    "title": "Interestelar",
    "year": 2014,
    "classification": 12,
    "date": "06/11/2014 (BR)",
    "category": ["Aventura", "Drama", "Ficção cientifica"],
    "duration": "2h 49m",
    "trailer": "https://youtu.be/mbbPSq63yuM",
    "synoyisis": "As reservas naturais da Terra estão chegando ao fim e um grupo de astronautas recebe a missão de verificar possíveis planetas para receberem a população mundial, possibilitando a continuação da espécie. Cooper é chamado para liderar o grupo e aceita a missão sabendo que pode nunca mais ver os filhos. Ao lado de Brand, Jenkins e Doyle, ele seguirá em busca de um novo lar.",
    "director": "Christopher Nole",
    "poster": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/55JWKCqNTn54016voGvig52ikjb.jpg",
    "id": 1,
    "posts": []
  }
]
```

`POST` Para adicionar um filme use a rota `/films`, nessecita de token e de um corpo:

```json
{
      "title": "2001: Odyce space",
      "year": 2014,
      "classification": 12,
      "date": "06/11/2014 (BR)",
      "category": [
        "Aventura",
        "Drama",
        "Ficção cientifica"
      ],
      "duration": "2h 49m",
      "trailer": "https://youtu.be/mbbPSq63yuM",
      "synoyisis": "As reservas naturais da Terra estão chegando ao fim e um grupo de astronautas recebe a missão de verificar possíveis planetas para receberem a população mundial, possibilitando a continuação da espécie. Cooper é chamado para liderar o grupo e aceita a missão sabendo que pode nunca mais ver os filhos. Ao lado de Brand, Jenkins e Doyle, ele seguirá em busca de um novo lar.",
      "director": "Christopher Nole",
      "poster": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/55JWKCqNTn54016voGvig52ikjb.jpg"
    }
```

Retorno: 

```json
{
	"title": "2001: Odyce space",
	"year": 2014,
	"classification": 12,
	"date": "06/11/2014 (BR)",
	"category": [
		"Aventura",
		"Drama",
		"Ficção cientifica"
	],
	"duration": "2h 49m",
	"trailer": "https://youtu.be/mbbPSq63yuM",
	"synoyisis": "As reservas naturais da Terra estão chegando ao fim e um grupo de astronautas recebe a missão de verificar possíveis planetas para receberem a população mundial, possibilitando a continuação da espécie. Cooper é chamado para liderar o grupo e aceita a missão sabendo que pode nunca mais ver os filhos. Ao lado de Brand, Jenkins e Doyle, ele seguirá em busca de um novo lar.",
	"director": "Christopher Nole",
	"poster": "https://www.themoviedb.org/t/p/w600_and_h900_bestv2/55JWKCqNTn54016voGvig52ikjb.jpg",
	"id": 3
}
```
