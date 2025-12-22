# Track Add to Cart Button Event

Este componente rastreia cliques no botão de adicionar ao carrinho e envia eventos para Google Analytics via dataLayer.

## Uso

react/SendEventPdp.js

```javascript
import SendEventPdp from './components/SendEventPdp/index'

export default SendEventPdp
```

store/interfaces.json

```json
"custom-sendevent-seb": {
  "component": "SendEventPdp"
},
```

## Exemplos

```json
"store.product": {
  "children": [
    "custom-sendevent-seb",
  ]
},
```

## Funcionalidades

### Rastreamento de Eventos

- Intercepta cliques no botão de adicionar ao carrinho
- Captura a classe CSS do elemento span filho
- Envia evento para Google Analytics via dataLayer
- Remove listener ao desmontar o componente

### Dados Enviados

- `event`: Nome do evento (click_category_ver_também)
- `send_to`: ID do Google Analytics (G-WBSPVQFS2L)
- `span_class`: Classe CSS do span dentro do botão

## Dependências

- `react`: Hook `useEffect`

## Seletores

- `#add-to-cart-event-test`: ID do botão
- `#add-to-cart-event-test > span`: Elemento span filho
