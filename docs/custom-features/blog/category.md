# Blog Category

Esse componente lista todos os posts da categoria selecionada.

![image](../../assets/blog-category.png)

## Uso

react/Category.tsx

```jsx
import Category from './Pages/Category'

export default Category

```

store/interfaces.json

```json
"lojaarno-blog-category": {
  "component": "Category"
},
```

## Exemplos

```jsx
"store.custom#blog-category": {
  "children": ["lojaarno-blog-category"]
},
```

## Route

```json
"store.custom#blog-category": {
  "path": "/blog/categoria/:categoryUrl",
  "isSitemapEntry": true
},
```

## Estrutura

O componente `Category` possui a seguinte estrutura hierárquica:

```text
CategoryProvider (Context)
└── main
  ├── Head (Componente)
  ├── Filters (Componente)
  └── Posts (Componente)
```

### Componentes Filhos

- **`Head`**: Componente responsável pelo cabeçalho da página de categoria
- **`Filters`**: Componente de filtros para refinamento dos posts
- **`Posts`**: Componente que lista os posts da categoria selecionada

#### Head

Componente responsável por renderizar o cabeçalho da página de categoria do blog.
Exibe o breadcrumb de navegação e as informações da categoria (título e descrição).

Este componente utiliza o contexto `useCategory` para obter:

- `params`: Parâmetros da URL, incluindo `categoryUrl`
- `category`: Objeto contendo informações da categoria (name, description)

**Estrutura renderizada:**

- Breadcrumb com navegação hierárquica (Início > Categorias > Categoria Atual)
- Título da categoria (h1)
- Descrição da categoria (h2)

#### Filters

Componente responsável por renderizar os filtros dos posts da categoria.

Este componente utiliza o contexto `useCategory` para obter:

- `filters`: Array com os filtros da categoria
- `activeFilter`: Filtro selecionado
- `handleFilterPosts`: Função que filtra os posts pelo filtro selecionado
- `isOpenFilter`: Booleano para mostrar ou não o modal de filtros no mobile
- `handleOpenFilter`: Função que abre o modal de filtros no mobile
- `handleClearFilter`: Função que limpa o filtro selecionado

#### Posts

Componente responsável por renderizar os posts da categoria ativa.

Este componente utiliza o contexto `useCategory` para obter:

- `filteredPosts`: Posts da categoria atual
- `loading`: Booleano que indica se os dados estão sendo carregados
- `handleLoadMorePosts`: Função que lida com a paginação da categoria
- `hasMorePosts`: Booleano que indica se deve mostrar o botão de ver mais posts
- `DEFAULT_POST_COUNT`: Constante que indica a quantidade de posts que deve ser renderizadas

### Context

- **`CategoryProvider`**: Provedor de contexto que gerencia o estado compartilhado entre os componentes filhos

## Observações

1. Busca a categoria usando a API do Masterdata. Para mais detalhes visualizar [Blog API Masterdata](./api-masterdata.md)

### Tratamento de Erros

- Em caso de erro na API, registra no console e finaliza o carregamento
- Mantém a interface funcional mesmo com falhas na API
