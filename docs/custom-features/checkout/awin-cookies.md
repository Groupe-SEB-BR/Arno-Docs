# Awin Cookies

Componente React que gerencia rastreamento de conversões do Awin, sincronizando parâmetros de origem de tráfego com o orderForm.

## Uso

react/AwinCookies.js

```javascript
import AwinCookies from './components/AwinCookies';

export default AwinCookies;
```

store/interfaces.json

```json
"custom-arno-awin-cookies": {
  "component": "AwinCookies"
}
```

## Exemplos

```json
"header-layout.desktop": {
  "children": [
    "global-css",
    "custom-arno-awin-cookies",
  ]
},
```

## Funcionalidades

### Sincronização de Dados de Sessão

- Busca dados públicos da sessão (`utm_source`, `awc`)
- Recupera `orderFormId` do checkout
- Atualiza customData do orderForm com informações do Awin

### Mapeamento de Parâmetros

- `utm_source=awin` → mapeado como `'aw'`
- Outros valores mapeados como `'other'`
- `awc` (Awin Conversion ID) preservado ou definido como `'other'`

## Dependências

- `react`: Hook `useEffect`

## Endpoints Utilizados

- `GET /api/sessions` - Recupera dados de sessão
- `PUT /api/checkout/pub/orderForm/{orderFormId}/customData/awin` - Atualiza customData

## Tratamento de Erros

Erros nas requisições são logados no console com prefixo `[AWIN]` e não impedem execução.
