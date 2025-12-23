# Meta Tags

Este componente gerencia meta tags dinâmicas para SEO, incluindo Open Graph e Twitter Cards, com base no path da página atual.

## Uso

react/MetaTags.tsx

```jsx
import MetaTags from './components/MetaTags';

export default MetaTags;
```

store/interfaces.json

```json
"custom-arno-meta-tags": {
  "component": "MetaTags"
}
```

## Exemplos

```jsx
"store.home": {
  "children": ["custom-arno-meta-tags"]
}
```

## Funcionalidades

### Meta Tags Dinâmicas

O componente injeta meta tags no `<head>` da página:

- **Title**: Título da página
- **Description**: Descrição meta
- **Canonical URL**: URL canônica para SEO
- **Open Graph**: Meta tags para compartilhamento social (Facebook, LinkedIn)
- **Twitter Cards**: Meta tags específicas para Twitter

### Sistema de Matching

- **Path Matching**: Compara path atual com paths configurados
- **Decode automático**: Remove encoding de URLs
- **Trailing slash**: Remove barra final para comparação
- **Fallback**: Log de aviso quando não há match

## Estrutura de Dados

### Propriedades do Componente

```javascript
{
  items: Array<{
    title: string,        // Título da página (obrigatório)
    description: string,  // Descrição meta (obrigatório)
    image: string,        // URL da imagem para OG/Twitter
    pathname: string,     // Path para match (ex: /arno/para-casa)
    canonical: string     // URL canônica (usa window.location.href se vazio)
  }>
}
```

## Comportamento

### Renderização Condicional

O componente não renderiza se:

- Não houver `title` e `description` definidos
- Nenhum item corresponder ao path atual

### Atualização Dinâmica

1. Monitora mudanças em `route.canonicalPath`
2. Busca item correspondente no array `items`
3. Atualiza meta tags via Helmet
4. Emite aviso no console se não encontrar match

## Meta Tags Injetadas

### Tags Básicas

- `<title>`: Título da página
- `<meta name="description">`: Descrição da página
- `<link rel="canonical">`: URL canônica

### Open Graph

- `og:title`: Título para redes sociais
- `og:description`: Descrição para redes sociais
- `og:image`: Imagem de preview (se fornecida)

### Twitter Cards

- `twitter:card`: Tipo de card (summary_large_image quando há imagem)
- `twitter:title`: Título para Twitter
- `twitter:description`: Descrição para Twitter
- `twitter:image`: Imagem para Twitter (se fornecida)

## Configuração via Schema

### Propriedades Principais

```typescript
{
  items: {
    type: 'array',
    items: {
      title: string,        // Título* (obrigatório)
      description: string,  // Description* (obrigatório)
      image: string,        // Image URL (opcional)
      pathname: string,     // Path Name* (ex: /arno/para-casa)
      canonical: string     // Canonical URL (opcional)
    }
  }
}
```

## Dependências

- **react-helmet**: Gerenciamento de meta tags
- **vtex.render-runtime**: Acesso ao route/canonicalPath

## Observações

1. Configuração via Site Editor para cada página
2. Path matching remove trailing slashes automaticamente
3. Canonical URL usa `window.location.href` como fallback
4. Imagem é opcional mas recomendada para compartilhamento social
5. Twitter Card usa `summary_large_image` quando imagem está presente
6. Console logs ajudam a debugar paths não encontrados
