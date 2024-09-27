# PodCast Manager

### Descrição

Um app ao estilo netflix, aonde possa centralizar diferentes episodios podcasts 
separados por categoria

### Domínio

Podcasts feitos em videos

### Features

- Listar os episódios podcasts em sessões de categorias 
    - [saude, bodybuilder, mentalidade, humor]   
- Filtrar episódios por nome de podcast

## Como

#### Feature:
Listar os episódios podcasts em sessões de categorias 

### Como vou implementar

GET: retorna lista de episódios

reponse:
```js
[
    {
    podcastname: "flow",
    episode: "CBUM - Flow #319",
    videoId: "sd4f568sdf",
    cover: "https://teste.com.br",
    link: "https://www.youtube.com.br",
    categories: ["saúde", "esporte", "bodybuilder"]
    },
    {
    podcastname: "flow",
    episode: "RUBENS BARRICHELLO - Flow #339",
    videoId: "sd4f568sdf",
    cover: "https://teste.com.br",
    link: "https://www.youtube.com.br",
    categories: ["esporte", "corrida"]
    }
]

``` 

GET: retorna lista de episódios baseado em um parametro enviado 
pelo cliente do nome podcast