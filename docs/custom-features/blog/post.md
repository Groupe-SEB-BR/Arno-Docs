# Blog Post

Esse componente renderiza o conteúdo do post selecionado baseado na URL.

![image](../../assets/blog-post.png)

## Usage

react/Post.tsx

```jsx
import Post from './Pages/Post'

export default Post
```

store/interfaces.json

```json
"lojaarno-blog-post": {
  "component": "Post"
},
```

## Examples

```jsx
"store.custom#blog-post": {
  "children": ["lojaarno-blog-post"]
},
```

## Route

```json
"store.custom#blog-post": {
  "path": "/blog/post/:postUrl",
  "isSitemapEntry": true
},
```

## Estrutura

O componente `Post` possui a seguinte estrutura hierárquica:

```text
PostProvider (Context)
└── main
  ├── Breadcrumb (Componente)
  ├── PostContent (Componente)
  ├── Tags (Componente)
  ├── Collection (Componente)
  └── Categories (Componente)
```

### Componentes Filhos

- **`Breadcrumb`**: Componente responsável pela navegação hierárquica do blog
- **`PostContent`**: Componente que renderiza o conteúdo completo do post selecionado
- **`Tags`**: Componente que exibe as tags associadas ao post atual
- **`Collection`**: Componente que mostra uma vitrine de produtos com os produtos relacionados ao post
- **`Categories`**: Componente que mostra posts relacionados

#### Breadcrumb

Componente responsável por renderizar o breadcrumb de navegação.

Este componente utiliza o contexto `usePost` para obter:

- `post`: Título e URL do post
- `loading`: Estado de carregamento dos dados

**Estrutura renderizada:**

- Breadcrumb com navegação hierárquica (Início > Post atual)

#### PostContent

Componente responsável por renderizar o conteúdo do post atual.

Este componente utiliza o contexto `usePost` para obter:

- `post`: Objeto contendo os dados completos do post atual
- `spreadLines`: Função que processa e formata o texto do post
- `loading`: Estado de carregamento dos dados do post

**Estrutura renderizada:**

- Seção com conteúdo do post
- Informações da receita (se aplicável):
  - Tempo de preparo
  - Complexidade
  - Lista de ingredientes
- Vídeo incorporado (se `useVideo` for true) ou imagem do post
- Descrição completa do post
- Modo de preparo (se aplicável)

**Props do contexto utilizadas:**

- `post`: Objeto contendo os dados completos do post
  - `videoIframe`: URL do vídeo do YouTube
  - `ingredients`: Ingredientes da receita (opcional)
  - `recipeTime`: Tempo de preparo da receita
  - `complexity`: Nível de complexidade da receita
  - `useVideo`: Boolean que indica se deve exibir vídeo
  - `imageMobile`: URL da imagem do post
  - `title`: Título do post
  - `description`: Conteúdo HTML do post
  - `instructions`: Instruções de preparo da receita (opcional)
- `spreadLines`: Função que processa e renderiza linhas de texto
- `loading`: Estado de carregamento dos dados

#### Tags

Componente responsável por renderizar os posts da categoria ativa.

Este componente utiliza o contexto `usePost` para obter:

- `post`: Posts atual baseado na URL
  - `posttags`: Tags do post atual
- `spreadCategories`: Booleano que indica se os dados estão sendo carregados

**Estrutura renderizada:**

- Seção contendo as tags relacionadas ao post
- Título "Assuntos relacionados"
- Lista de tags com links para páginas de tags específicas

**Props do contexto utilizadas:**

- `post`: Objeto contendo os dados do post atual
  - `posttags`: String ou array contendo as tags associadas ao post
- `spreadCategories`: Função que processa e converte as tags em array
- `loading`: Estado de carregamento dos dados

#### Collection

Componente responsável por renderizar uma vitrine de produtos relacionados ao post.

Este componente utiliza o contexto `usePost` para obter:

- `post`: Dados do post com produtos relacionados
  - `collection`: Id da coleção relacionada ao post atual

#### Categories

Componente responsável por renderizar posts relacionados por categoria.

Este componente utiliza o contexto `usePost` para obter:

- `post`: Dados dos posts relacionados
  - `categories`: Categorias relacionadas ao post
- `spreadCategories`: Função que processa e converte as categorias em array

### Context

- **`PostProvider`**: Provedor de contexto que gerencia o estado compartilhado entre os componentes filhos

## Observações

1. Busca o post baseado na URL atual usando a API do Masterdata. Para mais detalhes visualizar [Blog API Masterdata](/custom-features/blog/api-masterdata/)

### Tratamento de Erros

- Em caso de erro na API, registra no console e finaliza o carregamento
- Mantém a interface funcional mesmo com falhas na API
