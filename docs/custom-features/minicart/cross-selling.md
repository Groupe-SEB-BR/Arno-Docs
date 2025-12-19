# Cross Selling

 O componente CrossSelling busca e exibe produtos relacionados (cross-selling) ao item que está no carrinho.

## Uso

react/CrossSelling.js

```jsx
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

## Notes

Additional information, gotchas, or important considerations when using this component.
