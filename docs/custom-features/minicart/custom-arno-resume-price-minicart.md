# Minicart Resumo Custom

 O componente React que mostra um resumo de preços no minicart (subtotal, descontos, entrega, total à vista no PIX e parcelamento).

## Uso

react/ResumePriceMinicart.js

```jsx
import ResumePriceMinicart from './components/ResumePriceMinicart';

export default ResumePriceMinicart;
```

store/interfaces.json

```json
  "custom-arno-resume-price-minicart": {
    "component": "ResumePriceMinicart"
  },
```

## Exemplos

```jsx
  "flex-layout.col#minicart-footer": {
    "children": [
      "custom-arno-resume-price-minicart",
    ]
  },
```

## Notes

Additional information, gotchas, or important considerations when using this component.
