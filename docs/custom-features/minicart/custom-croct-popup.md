# Custom Croct Popup

 Este componente exibe um pop-up com um cupom de desconto quando um cliente adiciona itens ao carrinho, após um período de tempo determinado.

## Uso

react/CroctPopUp.js

```jsx
import CroctPopUp from './components/CroctPopUp/index';

export default CroctPopUp;
```

store/interfaces.json
```json
  "custom-croct-popup": {
    "component": "CroctPopUp",
    "composition": "children"
  },
```

## Props

| Prop | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| desktopImage | string | Yes | false | Imagem para o Desktop |
| mobileImage | string | Yes | array | Imagem para o Mobile |
| displayMinutes | number | Yes | 1 | Tempo de exibição (minutos)  |
| desktopCoupon | string | Yes | false | Cupom Desktop |
| mobileCoupon | string | Yes | false | Cupom Mobile |

### Schema
```json
  title: 'Minicart Checker',
    description: 'Componente para exibir pop-up com cupom e imagens.',
    type: 'object',
    properties: {
      desktopImage: {
        title: 'Imagem Desktop',
        type: 'string',
        widget: {
          'ui:widget': 'image-uploader',
        },
      },
      mobileImage: {
        title: 'Imagem Mobile',
        type: 'string',
        widget: {
          'ui:widget': 'image-uploader',
        },
      },
      displayMinutes: {
        title: 'Tempo de exibição (minutos)',
        type: 'number',
        default: 1,
      },
      desktopCoupon: {
        title: 'Cupom Desktop',
        type: 'string',
        default: 'VOLTA5',
      },
      mobileCoupon: {
        title: 'Cupom Mobile',
        type: 'string',
        default: 'VOLTA5',
      },
    },
```

## Exemplos

```jsx
  "flex-layout.row#mainContent-desk-croct-popup": {
    "title": "Croct Pop-up Desktop",
    "children": ["custom-croct-popup"],
    "props": {
      "blockClass": "mainContent-desk-croct-popup"
    }
  }
```

## Notes

Additional information, gotchas, or important considerations when using this component.
