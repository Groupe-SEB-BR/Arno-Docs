# Flash Sale Shelf Component

Este componente exibe uma prateleira de produtos em promoção relâmpago, utilizando o `react-slick` para a renderização de um slider responsivo.

## Uso

### BlackFridayV2.js

```javascript
import Shelfv2 from './componentes/Shelfv2';

<Shelfv2 id='ofertas-relampago' activePromotions={activePromotions[0] ?? []} />;
```

### Timer

O componente `Timer` exibe uma contagem regressiva até a próxima meia-noite em tempo real para cada produto da vitrine.

#### Props

- `timer` (string, padrão: `'23:59:59'`): Proprietário ignorado; o timer sempre conta até a próxima meia-noite local.
- `string` (string, padrão: `''`): Texto exibido quando `timer` é falso ou nulo.

#### Comportamento

- Atualiza a contagem a cada segundo usando `setInterval`.
- Calcula o tempo restante até a próxima meia-noite local.
- Exibe horas, minutos e segundos em formato `HH:MM:SS`.
- Se não houver tempo restante, exibe zeros (`00:00:00`).

## Funcionalidades

- Exibição de produtos em promoção relâmpago.
- Carregamento dinâmico de produtos com base em promoções ativas.
- Renderização responsiva com suporte a dispositivos móveis.
- Controle de estado para gerenciar carregamento e exibição de produtos.

## Dependências

- `react`: Para gerenciamento de estado e efeitos colaterais.
- `react-slick`: Para a implementação do slider.
- `vtex.device-detector`: Para detectar o tipo de dispositivo.

## Observações

1. O componente aguarda a disponibilidade das promoções ativas.
2. A renderização do slider é adaptativa, dependendo do dispositivo.
3. O componente utiliza um sistema de loading para melhorar a experiência do usuário.
4. Os produtos são enriquecidos com informações de parcelas, se disponíveis.
