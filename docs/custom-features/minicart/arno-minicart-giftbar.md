# Minicart - Barra de Brinde com Frete

Este componente exibe uma barra de progresso no minicart com metas de frete grátis e brinde, mostrando o progresso da compra em relação aos valores estabelecidos.

![image](../../assets/frete-gratis.png)

## Uso

react/MinicartGiftBar.js

```javascript
import MinicartGiftBar from './components/MinicartGiftBar';

export default MinicartGiftBar;
```

store/interfaces.json

```json
"custom-arno-minicart-giftbar": {
  "component": "MinicartGiftBar"
}
```

## Props

| Propriedade         | Tipo    | Padrão            | Descrição                      |
| ------------------- | ------- | ----------------- | ------------------------------ |
| `priceFreeShipping` | string  | '499.99'          | Valor para ativar frete grátis |
| `priceGift`         | string  | '599.00'          | Valor para ganhar brinde       |
| `gift`              | string  | 'um copo TEFAL'   | Nome do brinde                 |
| `showGift`          | boolean | false             | Exibir meta de brinde          |
| `giftTooltip`       | string  | 'Mês das mães...' | Texto do tooltip               |
| `shippingIcon`      | string  | '🚚'              | Ícone do frete                 |
| `giftIcon`          | string  | '🎁'              | Ícone do brinde                |

## Funcionalidades

- Barra de progresso com metas dinâmicas
- Calcula subtotal com descontos aplicados
- Ícone de frete avança conforme progresso
- Ícone de brinde fixo na meta
- Mensagens contextualizadas por estágio
- Tooltip ao passar mouse sobre brinde
- Formatação de valores em BRL

## Estados

- `valueCart`: Valor atual do carrinho em reais

## Dependências

- `react`: Hooks `useEffect`, `useState`
- `vtex.order-manager/OrderForm`: Hook `useOrderForm`
- `./styles.css`: Estilos customizados
