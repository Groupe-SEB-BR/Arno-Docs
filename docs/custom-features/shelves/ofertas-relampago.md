# Ofertas Relâmpago

Esse componente é reponsável pela vitrine de ofertas relâmpago, cada produto recebe uma data e horário para iniciar e finalizar a oferta.

## TODO

Refatorar o código de ofertas relâmpago para não depender da vitrine de Black Friday. Criar um componente para vitrine customizada que possa ser reutilizado facilmente, e outro para ofertas relâmpago que possa ser usado em qualquer página.

## Uso

react/FlashSalesHome.js

```jsx
import FlashSalesHome from './components/PDP/FlashSalesHome';

export default FlashSalesHome;
```

store/interfaces.json

```json
  "custom-flash-sales-home": {
    "component": "FlashSalesHome"
  }
```

## Props

| Prop         | Type             | Required | Default | Description                                  |
| ------------ | ---------------- | -------- | ------- | -------------------------------------------- |
| activePromotions         | Array of objects | Yes      | []      | Array de objetos com os produtos |

### Props de `activePromotions`

Cada objeto no array de `activePromotions` deve ter as seguintes propriedades:

| Property | Type   | Required | Description                           |
| -------- | ------ | -------- | ------------------------------------- |
| productClusterId    | string | Yes      | Id da coleção cadastrada na VTEX      |
| image    | string | No       | Banner acima da vitrine                        |
| title | string | No       | Título da vitrine        |
| description     | string | No      | Descrição da vitrine           |
| ctaButton | string | No       | Texto do botão abaixo da vitrine                    |
| ctaButtonLink | string | No       | Link do botão                    |
| items | Array of objects | Yes       | Produtos da vitrine                    |

### Props de `items`

| Property | Type   | Required | Description                           |
| -------- | ------ | -------- | ------------------------------------- |
| id    | string | Yes      | Id do produto      |
| initialDate    | Date | Yes       | Data e horário inicial da oferta                        |
| endDate | Date | Yes       | Data e horário final da oferta        |

## Exemplos

```jsx
  "store.home": { 
    "blocks": [
      "custom-flash-sales-home",
    ]
  }
```

## Notes

Os produtos dentro da coleção na VTEX devem estar na ordem das datas que eles vão ser ofertados.
