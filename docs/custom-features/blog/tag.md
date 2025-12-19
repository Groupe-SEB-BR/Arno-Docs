# Blog Tag

Este componente renderiza os posts relacionados à tag atual do blog.

![image](../../assets/post-tag.png)

## Uso

react/Tag.tsx

```jsx
import Tag from './Pages/Tag'

export default Tag
```

store/interfaces.json

```json
"lojaarno-blog-tag": {
  "component": "Tag"
},
```

## Exemplos

```jsx
"store.custom#blog-tag": {
  "children": ["lojaarno-blog-tag"]
},
```

## Route

```json
"store.custom#blog-tag": {
  "path": "/blog/tag/:tagUrl",
  "isSitemapEntry": true
},
```

## Estrutura

O componente `Tag` possui a seguinte estrutura hierárquica:

```text
Tag (Component)
└── main
  ├── section (Cabeçalho)
  │ ├── Breadcrumb (navegação)
  │ └── Tag Info (título da tag)
  ├── section (Posts)
  │ └── PostCard[] (lista de posts)
  └── section (Rodapé - condicional)
    └── button (Carregar mais)
```

### Props

- **`params`**: Objeto contendo os parâmetros da rota
  - `tagUrl`: String com a URL da tag atual

### Estados Gerenciados

- **`currentTag`**: String que armazena a tag atual da URL
- **`posts`**: Array de posts filtrados pela tag
- **`postCount`**: Número de posts carregados (padrão: 12)
- **`hasMorePosts`**: Booleano que indica se há mais posts disponíveis
- **`loading`**: Estado de carregamento dos dados

### Funcionalidades

#### fetchPosts

Função responsável por buscar e filtrar posts pela tag atual.

**Comportamento:**

- Busca todos os posts via API do Masterdata
- Filtra posts que contêm a tag atual (comparando URL slugificada)
- Atualiza o estado com os posts filtrados
- Controla o estado de carregamento
- Determina se há mais posts disponíveis

**Filtro aplicado:**

- Verifica se `posttags` é uma string
- Separa as tags por vírgula
- Converte cada tag para slug
- Compara com a `tagUrl` do parâmetro

#### handleLoadMorePosts

Função responsável por carregar mais posts quando o usuário clica no botão.

**Comportamento:**

- Carrega 12 posts adicionais por vez
- Incrementa o contador de posts
- Desativa o botão se não houver mais posts
- Mantém os posts anteriores e adiciona os novos

### Componentes Renderizados

#### Breadcrumb

Navegação hierárquica do blog:

- Link para página inicial do blog
- Nome da tag atual

#### Tag Info

Seção com informações da tag:

- Título com hashtag e nome da tag

#### Posts Section

Lista de posts filtrados pela tag:

- Renderiza componente `PostCard` para cada post
- Exibe `Loading` durante carregamento
- Mostra mensagem "Nenhum post encontrado" se não houver posts

#### Load More Button

Botão "Carregar mais" (condicional):

- Aparece apenas se houver 12 ou mais posts
- Desaparece quando não há mais posts disponíveis

## Observações

1. Busca todos os posts via API do Masterdata e filtra localmente pela tag. Para mais detalhes visualizar [Blog API Masterdata](/custom-features/blog/api-masterdata/)
2. A tag é identificada pela URL slugificada (ex: `/blog/tag/receitas-rapidas`)
3. Os posts são carregados em lotes de 12

### Tratamento de Erros

- Em caso de erro na API, registra no console
- Finaliza o carregamento mesmo com falhas
- Mantém a interface funcional

### Performance

- Usa `useCallback` para memorizar a função `fetchPosts`
- Carregamento paginado para melhor performance
- Filtragem otimizada usando slugs

