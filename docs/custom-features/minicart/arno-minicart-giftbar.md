# Minicart Gift Bar

Este componente exibe um pop-up com um cupom de desconto quando um cliente adiciona itens ao carrinho, após um período de tempo determinado.

## Uso

react/MinicartGiftBar.js

```jsx
import MinicartGiftBar from './components/MinicartGiftBar/index';

export default MinicartGiftBar;
```

store/interfaces.json

```json
  "arno-minicart-giftbar": {
    "component": "MinicartGiftBar"
  },
```

## Props

| Prop | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| priceFreeShipping | string | Yes | false | Valor para frete grátis |
| priceGift | string | Yes | array | Valor para ganhar o brinde |
| gift | string | Yes | 1 | Nome do brinde |
| showGift | boolean | Yes | false | Ativar exibição do brinde? |
| giftTooltip | string | Yes | false | Texto do pop-up ao passar o mouse sobre o presente |
| shippingIcon | string | Yes | false | Ícone do frete |
| giftIcon | string | Yes | false | Ícone do brinde |

### Schema

```json
  title: 'Minicart - Barra de brinde com frete',
    description: 'Exibe barra com metas: frete grátis e brinde',
    type: 'object',
    properties: {
      priceFreeShipping: {
        type: 'string',
        title: 'Valor para frete grátis',
        default: '499.99',
      },
      priceGift: {
        type: 'string',
        title: 'Valor para ganhar o brinde',
        default: '599.00',
      },
      gift: {
        type: 'string',
        title: 'Nome do brinde',
        default: 'um copo TEFAL',
      },
      showGift: {
        type: 'boolean',
        title: 'Ativar exibição do brinde?',
        default: true,
      },
      giftTooltip: {
        type: 'string',
        title: 'Texto do pop-up ao passar o mouse sobre o presente',
        default: 'Mês das mães: compras acima de R$ 599 ganham um copo Tefal!',
      },
      shippingIcon: {
        type: 'string',
        title: 'Ícone do frete',
        default: '🚚',
      },
      giftIcon: {
        type: 'string',
        title: 'Ícone do brinde',
        default: '🎁',
      },
    },
```

## Exemplos

```jsx
  "flex-layout.row#content-giftbar-v2": {
    "title": "Progress Bar",
    "props": {
      "blockClass": "content-giftbar-v2"
    },
    "children": ["arno-minicart-giftbar"]
  },
```

## Notes

Additional information, gotchas, or important considerations when using this component.
