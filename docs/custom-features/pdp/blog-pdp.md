# Blog PDP

Este componente exibe o post de blog mais acessado relacionado ao produto na página de detalhes do produto (PDP), baseado em tags compartilhadas entre o produto e os posts.

![image](../../assets/blog-pdp.png)

## Uso

react/BlogPDP.js

```javascript
import BlogPDP from './components/BlogPDP';

export default BlogPDP;
```

store/interfaces.json

```json
"custom-arno-pdp-blog-session": {
  "component": "BlogPDP"
},
```

## Exemplos

```json
"flex-layout.row#blog-pdp": {
  "children": ["custom-arno-pdp-blog-session"],
  "props": {
    "blockClass": "pdp-blog-session"
  }
},
```

## Funcionalidades

### Busca de Posts

- Busca posts no Master Data (entidade BP)
- Filtra posts por categoria
- Suporta ordenação customizada
- Paginação com até 100 registros

### Correspondência de Tags

- Compara tags dos posts com o nome do produto
- Busca case-insensitive
- Retorna primeiro post correspondente
- Fallback para null se nenhum post encontrado

### Renderização de Conteúdo

- Exibe imagem ou vídeo do post
- Formata data de criação
- Trunca descrição em 200 caracteres
- Remove tags HTML e CSS da descrição
- Exibe complexidade e tempo (para receitas)

## Comportamento

### Fluxo de Carregamento

1. Busca todos os posts disponíveis
2. Filtra posts que contêm tags no nome do produto
3. Busca detalhes completos do post encontrado
4. Atualiza estado com dados do post
5. Renderiza conteúdo do post

### Tratamento de Vídeo

1. Verifica flag `useVideo` do post
2. Converte URL do YouTube para formato embed
3. Renderiza iframe com vídeo ou imagem fallback

## Dependências

- `react`: Hooks `useState`, `useEffect`
- `vtex.product-context`: Hook `useProduct` para acesso aos dados do produto
- `vtex.render-runtime`: Hook `useRuntime` para acesso às rotas
- `./styles.css`: Estilos CSS do componente

## Estados Gerenciados

- `post`: Objeto contendo dados do post encontrado

## API Functions

### getPosts

Busca posts do Master Data com filtros e ordenação.

```javascript
const getPosts = async (
  start = 0,
  orderName = 'updatedIn',
  orderType = 'DESC',
  filterCategory = ''
) => {
  const options = {
    method: 'GET',
    headers: { 'REST-Range': `resources=${start}-${start + 100}` },
  }

  const response = await fetch(
    `/api/dataentities/BP/search?categories=*${filterCategory}*&_fields=imageCard,title,url,id,createdIn,updatedIn,useVideo,videoIframe,categories,posttags,filters&_sort=${orderName} ${orderType}`,
    options
  )
  return response.json()
}
```

### getPost

Busca detalhes completos de um post específico por URL.

```javascript
const getPost = async url => {
  const options = {
    method: 'GET',
    headers: { 'REST-Range': 'resources=0-1' },
  }

  const response = await fetch(
    `/api/dataentities/BP/search?_fields=brand,createdIn,category,categories,complexity,description,id,imageDesktop,imageMobile,metaTitle,metaDescription,ingredients,instructions,posttags,recipeTime,title,url,collection,views,filters,useVideo,videoIframe&_where=url=${url}`,
    options
  )
  return response.json()
}
```

## Funções Auxiliares

### formatDateWritten

Formata data no padrão brasileiro (dia de mês de ano).

```javascript
const formatDateWritten = dateStr => {
  if (!dateStr) return ''
  const date = new Date(dateStr)
  return date.toLocaleDateString('pt-BR', {
    day: 'numeric',
    month: 'long',
    year: 'numeric',
  })
}
```

## Campos do Post

### Campos Principais

- `title`: Título do post
- `description`: Descrição/conteúdo do post
- `imageDesktop`: Imagem principal (desktop)
- `imageMobile`: Imagem para mobile
- `url`: URL do post
- `createdIn`: Data de criação
- `updatedIn`: Data de atualização

### Campos de Vídeo

- `useVideo`: Flag para usar vídeo ao invés de imagem
- `videoIframe`: URL do vídeo (YouTube)

### Campos de Receita

- `complexity`: Complexidade da receita
- `recipeTime`: Tempo de preparo
- `ingredients`: Ingredientes
- `instructions`: Instruções

### Campos de Categorização

- `categories`: Categorias do post
- `posttags`: Tags separadas por vírgula
- `filters`: Filtros aplicáveis

### Campos SEO

- `metaTitle`: Título meta para SEO
- `metaDescription`: Descrição meta para SEO

## Observações

1. Retorna `null` se nenhum post correspondente for encontrado
2. Tags são comparadas com o nome do produto (lowercase)
3. Descrição é sanitizada (remove HTML/CSS) e truncada
4. Suporta vídeos do YouTube via iframe
5. Formato de data em português brasileiro
6. Campos de complexidade e tempo são opcionais
7. Usa Master Data (entidade BP) como fonte de dados
8. Recarrega quando produto ou rota mudam
