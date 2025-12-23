# Meta Data Category

Componente que gerencia meta tags dinâmicas e dados estruturados (schema.json) para páginas de categoria, buscando informações em uma entidade de dados customizada.

## Uso

react/MetaDataCategory.js

```javascript
import MetaDataCategory from './components/MetaDataCategory';

export default MetaDataCategory;
```

store/interfaces.json

```json
"custom-arno-meta-tags-category": {
  "component": "MetaDataCategory"
},
```

## Exemplos

```json
"search-result-layout.desktop": {
  "children": [
    "custom-arno-meta-tags-category",      
    "custom-color-title-category",
    "arno-search-banner",
    "flex-layout.row#search-breadcrumb",
    "flex-layout.row#search-title",
    "flex-layout.row#category"
  ],
  "props": {
    "pagination": "show-more",
    "blockClass": "desktop"
  }
},
```

## Funcionalidades

### Gerenciamento de Meta Tags

- Define title, description e og:image dinamicamente
- Suporta meta tags Open Graph para redes sociais
- Implementa meta tags Twitter Card
- Define canonical URL para evitar conteúdo duplicado

### Busca de Dados

- Busca metadados via API de Data Entities
- Usa pathname da página como identificador
- Suporta scripts JSON-LD customizados
- Remove protocol e domain da URL automaticamente

### Dados Estruturados

- Renderiza JSON-LD para SEO
- Suporta schema.json customizado
- Melhora indexação nos motores de busca

## Dependências

- `react`: Hooks `useState`, `useEffect`
- `react-helmet`: Renderização de meta tags
- `vtex.render-runtime`: Hook `useRuntime`

## Estados Gerenciados

- `json`: Dados estruturados JSON-LD
- `meta`: Objeto com title, description, image, canonical

## Observações

1. Busca dados da entidade "MD" com campo pathname2
2. Renderiza apenas meta tags com conteúdo disponível
3. Recarrega ao mudar canonicalPath da rota
4. Suporta scripts JSON-LD customizados
