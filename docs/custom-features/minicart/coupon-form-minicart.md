# Form de Cupom Minicart

Esse componente React permite aplicar e remover um cupom no minicart, atualizando o orderForm (via useOrderForm) chamando a API pública de checkout, exibindo feedback de sucesso/erro e um spinner durante operações assíncronas.

## Uso

react/CustomFormMinicart.js

```jsx
import CustomFormMinicart from './components/CustomFormMinicart';

export default CustomFormMinicart;
```

store/interfaces.json

```json
  "custom-cupom-minicart": {
    "component": "CustomFormMinicart"
  },
```

## Exemplos

```jsx
  "toggle-layout#content-cupom-minicart": {
    "title": "Cupom Minicart",
    "children": ["custom-cupom-minicart"],
    "props": {
      "blockClass": "content-cupom-minicart"
    }
  },
```

## Notes

Additional information, gotchas, or important considerations when using this component.
