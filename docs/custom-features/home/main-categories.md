# Main Categories

Este componente exibe uma grade de categorias principais com imagens e links na página inicial, com tracking de cliques via Google Analytics.

![image](../../assets/main-categories.png)

## Uso

react/MainCategories.tsx

```jsx
import MainCategories from './components/MainCategories';

export default MainCategories;
```

store/interfaces.json

```json
"custom-arno-home-categories": {
  "component": "MainCategories"
},
```

## Exemplos

```jsx
"store.home": {
  "children": ["custom-arno-home-categories"]
}
```

## Funcionalidades

### Grade de Categorias

O componente exibe uma grade de categorias com:

- **Imagens de Categoria**: Imagens representativas de cada categoria
- **Títulos**: Nome da categoria
- **Links**: Navegação para páginas de categoria
- **Tag Decorativa**: Elemento visual opcional

### Sistema de Tracking

- **Google Analytics**: Evento disparado ao clicar em cada categoria
- **Evento Personalizado**: `clicou_buscando_{index}` baseado na posição
- **ID de Tracking**: `G-WBSPVQFS2L`

## Estrutura de Dados

### Propriedades do Componente

```javascript
{
  shouldRender: boolean,  // Controla exibição do componente
  categories: Array<{
    title: string,        // Título da categoria
    description: string,  // Descrição da categoria
    href: string,         // URL de destino
    image: string,        // URL da imagem da categoria
    tag: string          // Tag opcional (ex: "Novidades")
  }>
}
```

## Comportamento

### Renderização Condicional

O componente não renderiza se:

- `shouldRender` for `false`
- Array `categories` estiver vazio

### Navegação com Tracking

1. Previne comportamento padrão do link
2. Envia evento para `dataLayer`
3. Redireciona para URL da categoria

## Categorias Padrão

O componente vem com 6 categorias pré-configuradas:

1. **Grill e churrasqueira**
2. **Ventilador**
3. **Airfryer**
4. **Liquidificador**
5. **Dolce Gusto**
6. **Batedeira e planetária**

## Configuração via Schema

### Propriedades Principais

```typescript
{
  shouldRender: {
    type: 'boolean',
    title: 'Deve aparecer',
    default: false
  },
  categories: {
    type: 'array',
    items: {
      title: string,        // Título da categoria
      description: string,  // Descrição da categoria
      href: string,         // Link da categoria
      image: string        // Imagem (com image-uploader)
    }
  }
}
```

## Estrutura de Classes CSS

- `.MainCategories`: Container principal
- `.MainCategoriesTitle`: Título "O que você está buscando?"
- `.Categories`: Grid de categorias
- `.CategoryItem`: Link de categoria individual
- `.CategoryImageWrapper`: Container da imagem
- `.CategoryImage`: Imagem da categoria
- `.CategoryTag`: Tag decorativa
- `.CategoryName`: Nome da categoria

## Dependências

- CSS Modules: Importação de estilos via `./styles.css`

## Observações

1. Requer configuração via Site Editor para personalização
2. Imagens devem ter dimensões 300x300px
3. Tracking requer Google Analytics configurado
4. Suporta upload de imagens via Site Editor
5. Campos `title` e `description` são obrigatórios no schema
