# Awin Conversion

Componente React que integra rastreamento de conversões do Awin, gerenciando pixels de tracking e identificação de origem de tráfego.

## Uso

react/AwinConversion.js

```javascript
import AwinConversion from './components/AwinConversion';

export default AwinConversion;
```

store/interfaces.json

```json
"custom-arno-awin-conversion": {
  "component": "AwinConversion"
},
```

## Exemplos

```json
"store.orderplaced": {
  "blocks": [
    "__fold__",
    "order-placed",
    "custom-arno-awin-conversion",
  ]
},
```

## Funcionalidades

### Definição de Origem de Tráfego

- Detecta origem via `awaid` ou `utm_source=awin`
- Identifica tráfego de buscadores (Google, Bing, Yahoo, DuckDuckGo, Yandex)
- Classifica como direto ou externo
- Armazena origem em cookie por 30 dias

### Rastreamento de Conversões

- Monitora eventos `orderPlaced` no dataLayer
- Dispara múltiplos pixels Awin (sread.js, sread.php, alt.php)
- Rastreia grupo de comissão por marca e categoria
- Envia cupom de desconto e identificadores de sessão

### Mapeamento de Produtos

Suporta grupos de comissão específicos para:

- **Nescafé Dolce Gusto**
- **Arno** (20+ categorias de produtos)
- **Rochedo** (panelas e utensílios)
- **Tefal** (frigideiras e panelas)

## Dependências

- `react`: Hook `useEffect`

## Variáveis de Configuração

- `merchantId`: '108626' (ID Awin)
- `currency`: 'BRL'
- `cookieDomain`: '.arno.com.br'
- `cookieLengthDays`: 30
