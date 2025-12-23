# Compare Products V2

Este componente exibe uma lista de produtos para comparação na página de detalhes do produto (PDP), filtrando produtos da mesma categoria e excluindo kits.

![image](../../assets/comparador.png)

## Uso

react/CompareProductsV2.js

```javascript
import CompareProductsV2 from './components/CompareProductsV2';

export default CompareProductsV2;
```

store/interfaces.json

```json
"custom-arno-pdp-compare-session": {
  "component": "CompareProductsV2"
},
```

## Exemplos

```json
"flex-layout.row#compare-pdp": {
  "children": ["custom-arno-pdp-compare-session"],
  "props": {
    "blockClass": "pdp-compare-session"
  }
},
```

## Funcionalidades

### Busca de Produtos

- Busca produtos por categoria
- Filtra produtos da mesma categoria do produto atual
- Exclui produtos com "kit" no nome
- Suporta até 4 produtos para comparação

### Responsividade

- Layout diferente para mobile e desktop
- Detecção automática de dispositivo
- Renderização condicional de componentes

### Construção de Dados

- Constrói objeto de dados do produto da página
- Formata dados dos produtos para comparação
- Extrai nome da categoria do produto

## Comportamento

### Fluxo de Carregamento

1. Aguarda dados do produto via `useProduct`
2. Extrai nome da categoria
3. Busca produtos pela árvore de categorias
4. Filtra produtos por categoria e remove kits
5. Atualiza estado com produtos para comparação
6. Renderiza componente apropriado (mobile/desktop)

### Filtragem de Produtos

1. Remove o produto da página da lista
2. Limita a 4 produtos para exibição
3. Mantém lista completa para seleção dinâmica

### Condições de Retorno Nulo

- Sem produtos na categoria
- Categoria é "Acessórios"
- URL do produto contém "kit"

## Dependências

- `react`: Hooks `useState`, `useEffect`
- `vtex.product-context`: Hook `useProduct`
- `vtex.device-detector`: Hook `useDevice`
- `./components/Desktop`: Componente desktop
- `./components/Mobile`: Componente mobile
- `./helpers/fetchProductsByCategory`: Busca de produtos
- `./helpers/buildProductData`: Construção de dados
- `./helpers/getCategoryName`: Extração de nome da categoria
- `./styles.css`: Estilos CSS

## Estados Gerenciados

- `productOfPage`: Dados do produto atual
- `productsToCompare`: Lista completa de produtos para comparar
- `productsToList`: Lista limitada a 4 produtos para exibição
- `categoryName`: Nome da categoria do produto
- `loading`: Estado de carregamento

## Props dos Componentes

### Desktop / Mobile

- `productOfPage`: Dados do produto da página
- `productsToCompare`: Lista completa de produtos
- `productsToList`: Lista de até 4 produtos
- `setProductsToList`: Função para atualizar lista exibida

## Observações

1. Retorna `null` se sem produtos ou categoria é "Acessórios"
2. Exclui produtos com "kit" na URL ou nome
3. Limita visualização a 4 produtos
4. Recarrega quando produto muda
5. Detecta automaticamente dispositivo (mobile/desktop)
6. Filtra por ID da categoria do produto atual
