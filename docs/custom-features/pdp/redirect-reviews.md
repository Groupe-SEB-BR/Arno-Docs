# Redirect to Reviews

Este componente redireciona cliques no link de avaliações para a aba de reviews e gerencia a exibição de contagem de avaliações.

![image](../../assets/redirect.png)

## Uso

react/RedirectToReviews.js

```javascript
import RedirectToReviews from './components/RedirectToReviews';

export default RedirectToReviews;
```

store/interfaces.json

```json
"custom-arno-scroll-to-reviews": {
  "component": "RedirectToReviews"
},
```

## Exemplos

```json
"link#product-rating-summary": {
  "props": {
    "href": "#tab-2",
    "blockClass": "product-rating-summary-link"
  },
  "children": ["product-rating-summary", "custom-arno-scroll-to-reviews"]
}
```

## Funcionalidades

### Redirecionamento de Cliques

- Intercepta cliques no link de avaliações
- Redireciona para aba de reviews (#tab-2)
- Realiza scroll suave até a aba
- Remove offset de 100px para melhor visualização

### Gerenciamento de Contagem

- Monitora elementos de contagem de avaliações
- Substitui "(0)" por "(-)" quando vazio
- Atualiza texto de classificação média
- Para monitoramento ao encontrar elementos

## Comportamento

### Primeiro Effect - Event Listener

1. Localiza link de avaliações via classe CSS
2. Adiciona listener de clique customizado
3. Redireciona para #tab-2 ao clicar
4. Executa scroll suave
5. Remove listener ao desmontar

### Segundo Effect - Monitoramento

1. Verifica a cada 200ms elementos de contagem
2. Substitui "(0)" por "(-)" se encontrado
3. Atualiza texto de classificação média
4. Para monitoramento ao localizar elementos
5. Limpa interval ao desmontar

## Dependências

- `react`: Hook `useEffect`

## Seletores CSS

- `.vtex-store-link-0-x-link--product-rating-summary-link`: Link de avaliações
- `#tab-2`: Aba de reviews
- `.review__rating--count`: Elemento de contagem
- `.review__rating--average`: Elemento de classificação média
