# Resumo de Preço do Minicart

Este componente exibe o resumo detalhado de preços no minicart, incluindo subtotal, descontos, frete e opções de pagamento (PIX e parcelamento).

![image](../../assets/resumo-minicart.png)

Descontos aplicados:
![image](../../assets/modal-desconto.png)

## Uso

react/ResumePriceMinicart.js

```javascript
import ResumePriceMinicart from './components/ResumePriceMinicart'

export default ResumePriceMinicart

```

store/interfaces.json

```json
"custom-arno-resume-price-minicart": {
  "component": "ResumePriceMinicart"
},
```

## Exemplos

```json
"flex-layout.col#minicart-footer": {
  "children": [
    "custom-cupom-minicart",
    "custom-arno-resume-price-minicart",
    "minicart-checkout-button"
  ]
},
```

## Funcionalidades

### Cálculo de Valores

- Subtotal de itens
- Descontos aplicados (PIX, cupons, outros)
- Valor de frete (ou "à calcular" se não houver endereço)
- Total à vista no PIX
- Parcelamento no cartão de crédito

### Desconto PIX

- Busca percentual de desconto via API (Master Data)
- Aplica desconto sobre subtotal já com outros descontos
- Exibe valor final com desconto PIX
- Não aplica desconto duplicado se pagamento já for PIX

### Parcelamento

- Calcula opções de parcelamento via API de simulação
- Respeita valor mínimo de parcela (R$ 50,00)
- Exibe maior parcelamento disponível
- Mostra valor por parcela

### Modal de Descontos

- Detalhamento de todos os descontos aplicados
- Desconto PIX com percentual
- Demais descontos (promoções, campanhas)
- Total consolidado de descontos
- Fecha ao clicar fora ou pressionar ESC

## Comportamento

### Fluxo de Carregamento

1. Verifica orderForm disponível
2. Busca percentual de desconto PIX no Master Data
3. Calcula opções de parcelamento via simulação
4. Processa todos os totalizadores do orderForm
5. Calcula descontos individuais e consolidados
6. Exibe resumo formatado

### Fluxo de Cálculo

1. **Subtotal**: Soma de todos os itens
2. **Descontos**: Cupons + Promoções + PIX
3. **Frete**: Valor da entrega ou "à calcular"
4. **Total PIX**: Subtotal - Descontos - Desconto PIX + Frete
5. **Total Crédito**: Subtotal - Descontos (sem PIX) + Frete
6. **Parcelamento**: Simulação com valor total crédito

## Dependências

- `react`: Hooks `useEffect`, `useState`, `useRef`, `useCallback`
- `vtex.order-manager/OrderForm`: Hook `useOrderForm` para acesso ao carrinho
- `../ModalMinicart`: Componente Modal para detalhamento de descontos
- `./styles.css`: Estilos customizados

## Estados Gerenciados

- `values`: Objeto com todos os valores calculados do resumo
- `isLoaded`: Estado de carregamento dos dados
- `hasAddress`: Indica se há endereço de entrega selecionado
- `showModal`: Controla exibição do modal de descontos
- `modalRef`: Referência para detecção de cliques fora do modal

## API

### Endpoint de Simulação de Parcelamento

```text
POST /api/checkout/pub/orderForms/simulation
```

**Request Body:**
```json
{
  "items": [
    {
      "id": "123",
      "quantity": 1,
      "seller": "1"
    }
  ]
}
```

**Response:**
```json
{
  "paymentData": {
    "installmentOptions": [
      {
        "installments": [
          {
            "count": 12,
            "value": 5000,
            "interestRate": 0
          }
        ]
      }
    ]
  }
}
```

### Endpoint de Desconto PIX (Master Data)

```text
GET /api/dataentities/ST/search?_fields=pixDiscount
```

**Response:**
```json
[
  {
    "pixDiscount": "5"
  }
]
```

## Estrutura de Valores

```javascript
{
  shippingValue: 0,           // Valor do frete
  discounts: 0,               // Descontos do orderForm
  itemsSubTotal: 0,           // Subtotal de itens
  total: 0,                   // Total geral
  pixDiscount: 0,             // Desconto PIX calculado
  totalComPix: 0,             // Total com desconto PIX
  installment: {...},         // Objeto de parcelamento
  totalDiscounts: 0,          // Total de todos os descontos
  isPixPayment: false,        // Se pagamento é PIX
  pixDiscountPercent: 0,      // Percentual de desconto PIX
  totalCredit: 0,             // Total para parcelamento
  couponDiscount: 0,          // Desconto de cupom (desabilitado)
  otherDiscounts: 0,          // Outros descontos
  hasCoupon: false            // Se tem cupom (desabilitado)
}
```

## Formatação de Valores

```javascript
const formatCurrency = value =>
  new Intl.NumberFormat('pt-BR', {
    style: 'currency',
    currency: 'BRL',
  }).format(value / 100)
```

## Constantes

```javascript
const MIN_INSTALLMENT_VALUE = 5000  // R$ 50,00 (valor em centavos)
```

## Observações

1. Valores são processados em centavos e formatados para exibição
2. Desconto PIX é calculado sobre subtotal já com descontos aplicados
3. Sistema de cupons está desabilitado no código atual
4. Modal é renderizado em portal global (`global-modal-root`)
5. Parcelamento só é exibido se houver opções acima do valor mínimo
6. Frete exibe "À CALCULAR" quando não há endereço selecionado
7. Componente exibe loading até todos os cálculos serem concluídos
8. Se pagamento já for PIX, desconto não é aplicado novamente
9. Tratamento de erros com fallback seguro em todas as APIs
10. Modal fecha com ESC ou clique fora da área de conteúdo

