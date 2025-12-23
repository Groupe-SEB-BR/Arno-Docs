# Cross-Selling Minicart

Este componente exibe sugestões de produtos relacionados no minicart, permitindo ao usuário adicionar produtos complementares ao carrinho sem sair da página atual.

![image](../../assets/cross-selling.png)

## Uso

react/CrossSelling.js

```javascript
import CrossSelling from './components/CrossSelling';

export default CrossSelling;
```

store/interfaces.json

```json
"custom-arno-minicart-cross-selling": {
  "component": "CrossSelling"
},
```

## Exemplos

```jsx
"minicart-base-content": {
  "blocks": ["minicart-empty-state"],
  "children": [
    "custom-arno-minicart-cross-selling",
  ]
},
```

## Funcionalidades

### Sugestões de Produtos

- Carrega produtos relacionados via API de cross-selling
- Filtra produtos disponíveis em estoque
- Remove produtos já adicionados ao carrinho
- Remove produtos duplicados

### Seleção de SKU

- Seletor visual de variações do produto
- Atualização dinâmica baseada na seleção
- Suporte para múltiplos SKUs por produto

### Exibição de Preços

- Mostra preço de lista quando há desconto
- Destaca preço de venda
- Formatação automática com `FormattedPrice`

### Carrossel de Produtos

- Navegação por setas
- Indicadores de slide (dots)
- Responsivo e configurável

## Comportamento

### Fluxo de Carregamento

1. Verifica se há itens no carrinho
2. Busca produtos relacionados ao primeiro item
3. Filtra produtos disponíveis e válidos
4. Agrupa SKUs por produto
5. Remove produtos já no carrinho
6. Exibe carrossel de sugestões

### Fluxo de Adição

1. Usuário seleciona SKU (se necessário)
2. Clica em adicionar ao carrinho
3. Produto é adicionado via componente `AddToCart`
4. Lista é atualizada removendo produto adicionado

## Dependências

- `react`: Hooks `useEffect`, `useState`
- `react-slick`: Componente de carrossel `Slider`
- `vtex.order-manager/OrderForm`: Hook `useOrderForm` para acesso ao carrinho
- `vtex.formatted-price`: Componente `FormattedPrice` para formatação de preços
- `./AddToCart`: Componente para adicionar produtos ao carrinho
- `../Loading`: Componente de loading
- `./SkuSelector`: Componente para seleção de SKU
- `./styles.css`: Estilos customizados

## Estados Gerenciados

- `products`: Lista completa de produtos relacionados
- `productToList`: Lista filtrada de produtos a exibir
- `loading`: Estado de carregamento
- `sectionTitle`: Título da seção de cross-selling
- `selectedSku`: SKU selecionado pelo usuário
- `skuInfo`: Informações agrupadas de SKUs por produto

## API

### Endpoint Utilizado

```text
GET /api/catalog_system/pub/products/crossselling/suggestions/{productId}
```

### Resposta

```json
[
  {
    "productId": "123",
    "productName": "Produto Exemplo",
    "linkText": "produto-exemplo",
    "items": [
      {
        "itemId": "456",
        "images": [...],
        "sellers": [
          {
            "commertialOffer": {
              "AvailableQuantity": 10,
              "Price": 99.90,
              "ListPrice": 149.90
            }
          }
        ]
      }
    ]
  }
]
```

## Configurações do Carrossel

```javascript
{
  dots: true,              // Exibe indicadores
  infinite: true,          // Loop infinito
  speed: 500,             // Velocidade de transição (ms)
  slidesToShow: 1,        // Produtos por slide
  slidesToScroll: 1,      // Produtos por scroll
  arrows: true            // Exibe setas de navegação
}
```

## Observações

1. Produtos são ordenados do mais recente para o mais antigo (por productId)
2. Apenas produtos com estoque disponível são exibidos
3. Produtos duplicados são removidos automaticamente
4. SKUs são agrupados por produto para seleção
5. Lista é atualizada em tempo real quando produtos são adicionados ao carrinho
6. Componente não renderiza se não houver produtos disponíveis
7. Imagens são otimizadas para 150x150px
8. Tratamento de erros com fallback seguro
