# Zatch Bell Brasil

Site estatico do Zatch Bell Brasil pronto para publicar como `index.html`.

## API

Os episodios sao carregados em tempo real pela Jikan API/MyAnimeList, sem salvar a lista de episodios no projeto.
O anime usado e o MAL ID `250`, que retorna os 150 episodios.

Para video, o campo de API propria e opcional e deve apontar para uma fonte autorizada com endpoints como:

```text
GET /episodes
GET /episodes/{id}/sources?type=sub
GET /watch/{id}
```

## Leitor de manga

O leitor de manga tambem fica leve. O catalogo e os capitulos do manga vem pela MangaDex API, usando o titulo `Zatch Bell!!` no MangaDex:

```text
https://api.mangadex.org/manga/63e54dfd-f7a9-473e-a591-28558e229c5b/feed
https://api.mangadex.org/at-home/server/{chapterId}
```

As paginas sao montadas no navegador com a resposta MangaDex@Home, sem salvar imagens no projeto.

Como fallback, o leitor tambem aceita paginas vindas de uma API propria/autorizada.

Endpoints aceitos pelo leitor:

```text
GET /manga/chapters/{capitulo}/pages
GET /manga/pages?chapter={capitulo}
```

Resposta esperada:

```json
{
  "pages": [
    "https://seu-cdn.com/capitulo-1/pagina-1.jpg",
    "https://seu-cdn.com/capitulo-1/pagina-2.jpg"
  ]
}
```

Tambem da para colar URLs de paginas direto no leitor para testar no navegador, sem salvar arquivos no projeto.

O site permanece estatico e leve para o plano gratis da Azure; os dados vem por API no navegador.

## Status oficial dos providers

O site tambem consulta o repositório oficial `consumet/providers-status` para mostrar quais providers estao online:

```text
https://raw.githubusercontent.com/consumet/providers-status/main/README.md
https://raw.githubusercontent.com/consumet/providers-status/main/status.json
```

Esse status alimenta a barra "Providers oficiais" do site. Ela mostra anime, manga, meta e news com os providers online no momento.

## Dominio

Dominio pretendido:

```text
zatchbellbrasil.site
```

Para usar no Azure, adicione esse dominio como custom domain no recurso do site/app e depois ajuste os registros DNS no Hostinger conforme os valores que o Azure mostrar.

Para GitHub Pages, use estes registros DNS no Hostinger:

```text
A     @     185.199.108.153
A     @     185.199.109.153
A     @     185.199.110.153
A     @     185.199.111.153
CNAME www   lucasotirrar-lgtm.github.io
```

O arquivo `CNAME` ja aponta para `zatchbellbrasil.site`.
