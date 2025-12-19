# Custom Price Minicart

 Este componente não renderiza nada diretamente no Front da loja no minicart, ele atua fazendo calculos e sincronizando preços dentro do obejto orderForm da VTEX.

## Uso

react/ChangePriceMinicart.js

```jsx
import ChangePriceMinicart from './components/ChangePriceMinicart';

export default ChangePriceMinicart;
```

store/interfaces.json

```json
  "custom-price-minicart": {
    "component": "ChangePriceMinicart"
  },
```

## Exemplos

```jsx
  "minicart-base-content": {
    "blocks": ["minicart-empty-state"],
    "children": [
      "custom-price-minicart"
    ]
  },
```

## Notes

Additional information, gotchas, or important considerations when using this component.
