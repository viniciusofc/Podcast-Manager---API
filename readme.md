Aqui está um **README** aprimorado com base nas informações que você forneceu:

---

# PodCast Manager

### Descrição

O **PodCast Manager** é um aplicativo no estilo Netflix que centraliza episódios de podcasts em vídeo, organizados por categorias. Ele permite que os usuários naveguem por diferentes sessões de categorias como saúde, bodybuilder, mentalidade, e humor, além de possibilitar a filtragem de episódios pelo nome do podcast.

### Domínio

Podcasts em formato de vídeo.

### Features

- **Listar Episódios de Podcasts**: 
  - Os episódios são organizados em sessões por categorias, como saúde, bodybuilder, mentalidade e humor.
- **Filtrar Episódios por Nome do Podcast**: 
  - Os usuários podem buscar episódios usando parte do nome do podcast.

## Implementação

### Feature 1: Listar os Episódios de Podcasts em Sessões de Categorias

A API retorna uma lista de episódios com seus respectivos detalhes, organizados em diferentes categorias.

#### Rota: `GET /episodes`

##### Exemplo de Resposta:
```json
[
    {
        "podcastname": "flow",
        "episode": "CBUM - Flow #319",
        "videoId": "sd4f568sdf",
        "categories": ["saúde", "esporte", "bodybuilder"]
    },
    {
        "podcastname": "flow",
        "episode": "RUBENS BARRICHELLO - Flow #339",
        "videoId": "sd4f568sdf",
        "categories": ["esporte", "corrida"]
    }
]
```

### Feature 2: Filtrar Episódios por Nome do Podcast

A API permite que o cliente filtre episódios com base no nome do podcast, retornando os resultados correspondentes.

#### Rota: `GET /episodes?podcastname={nome}`

##### Exemplo de Resposta:
```json
[
    {
        "podcastname": "flow",
        "episode": "CBUM - Flow #319",
        "videoId": "sd4f568sdf",
        "categories": ["saúde", "esporte", "bodybuilder"]
    }
]
```

## Código Base

Aqui está um exemplo de como você pode configurar as rotas do servidor para listar episódios e filtrar pelo nome do podcast.

```typescript
import * as http from "http";
import { getListEpisodes, getFilterEpisodes } from './controllers/podcasts-controller';
import { Routes } from "./routes/routes";
import { HttpMethod } from "./utils/http-methods";

export const app = (async (request: http.IncomingMessage, response: http.ServerResponse) => {

    const baseUrl = request.url?.split("?")[0];

    if (request.method === HttpMethod.GET && baseUrl === Routes.LIST) {
        await getListEpisodes(request, response);
    }

    if (request.method === HttpMethod.GET && baseUrl === Routes.EPISODE) {
        await getFilterEpisodes(request, response);
    }
});
```

### Rotas Definidas:

- **GET `/episodes`**: Retorna todos os episódios de podcasts.
- **GET `/episodes?podcastname={nome}`**: Filtra os episódios com base no nome do podcast fornecido como parâmetro.
