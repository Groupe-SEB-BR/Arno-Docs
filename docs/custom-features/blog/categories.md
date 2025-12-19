# Blog Categories

Esse componente lista todas as categorias cadastradas, independentemente se tiverem posts ou não.

![image](../../assets/categorias.png)

## Uso

react/Categories.tsx

```jsx
import Categories from './Pages/Categories';

export default Categories;
```

store/interfaces.json

```json
"lojaarno-blog-categories": {
  "component": "Categories"
}
```

## Exemplos

```jsx
"store.custom#blog-categories": {
  "children": ["lojaarno-blog-categories"]
}
```

## Route

```json
"store.custom#blog-categories": {
  "path": "/blog/categorias"
},
```

## Props do Componente Categories

| Prop                               | Tipo | Obrigatório? | Descrição | Valor Padrão |
| ---------------------------------- | ---- | ------------ | --------- | ------------ |
| _Este componente não recebe props_ | -    | -            | -         | -            |

## Observações

1. **Este componente não recebe nenhuma prop como parâmetro**
2. É um componente auto-suficiente que busca seus próprios dados
3. Gerencia seu estado interno (`categories` e `loading`)
4. Busca categorias usando a API do Masterdata. Para mais detalhes visualizar [Blog API Masterdata](/custom-features/blog/api-masterdata/)

## Funcionamento do Componente

### Estados Internos

- **`categories`**: Array de categorias obtidas da API, ordenadas alfabeticamente
- **`loading`**: Boolean que indica se os dados estão sendo carregados

### Ciclo de Vida

1. **Montagem**: Ao ser renderizado, o componente busca automaticamente as categorias
2. **Busca de Dados**: Chama `fetchCategories()` da API
3. **Processamento**: Ordena as categorias alfabeticamente por nome
4. **Renderização**: Exibe as categorias com imagem e nome

### Tratamento de Erros

- Em caso de erro na API, registra no console e finaliza o carregamento
- Mantém a interface funcional mesmo com falhas na API

## Comportamento

1. Exibe "Loading..." durante a busca de dados
2. Apresenta categorias em ordem alfabética
3. Cada categoria é um link para sua página específica
4. Breadcrumb de navegação fixo (não dinâmico)
