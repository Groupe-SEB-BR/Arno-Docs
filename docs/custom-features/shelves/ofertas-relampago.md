# Flash Sale Shelf Component

Este componente exibe uma prateleira de produtos em promoção relâmpago, utilizando o `react-slick` para a renderização de um slider responsivo.

## Uso

### FlashSales.js

```javascript
import FlashSales from './components/FlashSales';

export default FlashSales;
```

store/interfaces.json

```json
"custom-flash-sales-shelf": {
  "component": "FlashSales"
}
```

## Exemplos

```jsx
"store.home": {
  "blocks": [
    "custom-flash-sales-shelf",
  ]
}
```

### Shelf

O componente `Shelf` gerencia a exibição de prateleiras de ofertas relâmpago, alternando entre dois modos de visualização baseado na configuração de produtos.

#### Shelf Props

- `id` (string): Identificador único da prateleira.
- `darkMode` (boolean): A página está em modo escuro ou não.
- `showSession` (string): Deve mostrar a sessão ou não.
- `activePromotions` (array): Lista de promoções ativas a serem exibidas.
- `oneProductPerTime` (boolean): Define se deve exibir um produto por vez ou múltiplos produtos.
- `showDays` (boolean): Controla a exibição de dias na contagem regressiva.

#### Componentes Filhos

- **OneProductPerTimeShelf**: Renderiza uma prateleira exibindo um produto por vez.
- **MultipleProductsShelf**: Renderiza uma prateleira com múltiplos produtos simultaneamente.

#### Comportamento

- Renderiza ambos os componentes simultaneamente, permitindo que a lógica interna de cada um controle sua visibilidade.
- Repassa todas as props recebidas para os componentes filhos.
- Atua como um container coordenador entre os diferentes modos de exibição.

### Timer

O componente filho `Timer` exibe uma contagem regressiva dinâmica para promoções, calculando o tempo até o início ou fim da oferta com base no fuso horário de São Paulo.

#### Timer Props

- `string` (string, padrão: `''`): Texto exibido quando `currentProduct` é nulo ou indefinido.
- `showDays` (boolean): Se `true`, exibe os dias na contagem regressiva.
- `currentProduct` (object): Objeto do produto contendo datas de início e fim da promoção.
- `oneProductPerTime` (boolean): Aplica estilo específico quando há apenas um produto por vez.

#### Timer Comportamento

- Busca as datas da promoção a partir de múltiplas propriedades do produto (`initialDate`, `startDate`, `endDate`, etc.).
- Se a promoção ainda não começou, exibe contagem regressiva até o início.
- Se a promoção está ativa, exibe contagem regressiva até o fim.
- Utiliza o fuso horário `America/Sao_Paulo` para cálculos precisos.
- Atualiza a contagem a cada segundo usando `setInterval`.
- Exibe tempo em formato `DD:HH:MM:SS` ou `HH:MM:SS` (dependendo de `showDays`).
- Se não houver `currentProduct`, exibe apenas o texto de fallback.
- Quando o tempo expira, exibe zeros (`00:00:00`).

### ShelfProduct

O componente filho `ShelfProduct` renderiza um card individual de produto dentro da prateleira de ofertas relâmpago, gerenciando a seleção de SKU e exibindo informações do produto.

#### ShelfProduct Props

- `product` (object): Objeto contendo todas as informações do produto.
- `productClusterId` (string): ID do cluster do produto para exibição de tags especiais.
- `showTimer` (boolean): Define se o timer deve ser exibido.
- `showDays` (boolean): Controla se os dias devem ser exibidos no timer.

#### ShelfProduct Comportamento

- Gerencia a seleção de SKU através do estado `selectedSku`.
- Calcula o status da data da promoção (passado, presente ou futuro) usando `determineDateStatus`.
- Atualiza o tempo atual a cada segundo para manter o timer sincronizado.
- Renderiza diferentes estados visuais baseado no status da promoção:
  - **now**: Produto ativo com timer e possibilidade de compra.
  - **future**: Produto bloqueado com overlay e mensagem "Em breve".
  - **past**: Produto bloqueado com overlay e mensagem "Acabou".
- Exibe preços formatados incluindo preço de lista, preço final e parcelamento sem juros.
- Mostra tags especiais para produtos dos clusters 265 e 266.
- Integra componentes filhos: `Timer`, `SkuSelector`, `Highlights` e `AddToCart`.
- Desabilita o link do produto quando a promoção está futura ou expirada.
- Utiliza `memo` para otimização de renderização.

## Funcionalidades

- Exibição de produtos em promoção relâmpago.
- Carregamento dinâmico de produtos com base em promoções ativas.
- Renderização responsiva com suporte a dispositivos móveis.
- Controle de estado para gerenciar carregamento e exibição de produtos.
- Contagem regressiva precisa com suporte a múltiplos cenários de promoção.

## Observações

1. O componente aguarda a disponibilidade das promoções ativas.
2. A renderização do slider é adaptativa, dependendo do dispositivo.
3. O componente utiliza um sistema de loading para melhorar a experiência do usuário.
4. Os produtos são enriquecidos com informações de parcelas, se disponíveis.
5. É preciso que exista uma coleção criada dentro da VTEX para que o componente funcione corretamente.
6. Os produtos nessa coleção devem estar ordenados de forma crescente baseado nas datas de início das promoções de cada produto.
