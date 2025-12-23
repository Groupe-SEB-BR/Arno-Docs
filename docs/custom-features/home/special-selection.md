# Special Selection

Este componente exibe uma seleção especial de cards com imagens, títulos e links na página inicial, com suporte a slider no mobile e tracking de cliques via Google Analytics.

![image](../../assets/selecao-especial.png)

## Uso

react/SpecialSelection.js

```jsx
import SpecialSelection from './components/SpecialSelection';

export default SpecialSelection;
```

store/interfaces.json

```json
"custom-arno-special-selection": {
  "component": "SpecialSelection"
},
```

## Exemplos

```jsx
"store.home": {
  "children": ["custom-arno-special-selection"]
}
```

## Funcionalidades

### Cards Personalizáveis

O componente exibe cards com:

- **Imagens**: Imagens representativas de cada card
- **Título e Subtítulo**: Informações do card
- **Links**: Navegação com CTA customizável
- **Layout Responsivo**: Slider no mobile, grid no desktop

### Sistema de Tracking

- **Google Analytics**: Evento disparado ao clicar em cada card
- **Evento Personalizado**: `clicou_selecaoespecial_{index}` baseado na posição
- **ID de Tracking**: `G-WBSPVQFS2L`

### Layout Adaptativo

- **Mobile**: Slider com React Slick (1.25 slides visíveis)
- **Desktop**: Grid com largura dividida igualmente entre cards

## Estrutura de Dados

### Propriedades do Componente

```javascript
{
  shouldRender: boolean,  // Controla exibição do componente
  brandClass: string,     // Classe CSS da marca (default: 'arno')
  title: string,          // Título da seção
  cards: Array<{
    title: string,        // Título do card
    subTitle: string,     // Subtítulo do card
    image: string,        // URL da imagem
    linkUrl: string,      // URL de destino
    linkLabel: string     // Texto do botão (default: 'Comprar')
  }>
}
```

## Comportamento

### Renderização Condicional

O componente não renderiza se:

- `shouldRender` for `false`
- Array `cards` estiver vazio

### Navegação com Tracking

1. Previne comportamento padrão do link
2. Envia evento para `dataLayer`
3. Redireciona para URL do card

### Layout Condicional

- **Mobile**: Cards em formato de imagem opcional, posicionamento baseado na presença de imagem
- **Desktop**: Cards distribuídos uniformemente com largura calculada dinamicamente

## Configuração via Schema

### Propriedades Principais

```typescript
{
  shouldRender: {
    type: 'boolean',
    title: 'Deve aparecer',
    default: false
  },
  brandClass: {
    type: 'string',
    title: 'Classe da Marca',
    default: 'arno'
  },
  title: {
    type: 'string',
    title: 'Título'
  },
  cards: {
    type: 'array',
    items: {
      title: string,        // Título do card
      subTitle: string,     // Subtítulo do card
      image: string,        // Imagem (com image-uploader)
      linkUrl: string,      // URL de destino
      linkLabel: string     // Texto do link
    }
  }
}
```

## Estrutura de Classes CSS

- `.specialSelection`: Container principal
- `.card`: Card individual com imagem
- `.cardCenter`: Card sem imagem (centralizado)
- `.cardImage`: Imagem do card
- `.cardContent`: Container do conteúdo
- `.cardTitle`: Título do card
- `.cardSubTitle`: Subtítulo do card
- `.cardLink`: Link/botão do card

## Configuração do Slider

```javascript
{
  dots: true,              // Indicadores de navegação
  infinite: false,         // Não repete os slides
  speed: 500,             // Velocidade da transição
  slidesToShow: 1.25,     // Mostra 1.25 slides por vez
  slidesToScroll: 1,      // Avança 1 slide por vez
  arrows: false           // Sem setas de navegação
}
```

## Dependências

- `react-slick`: Componente de slider
- `vtex.device-detector`: Detecção de dispositivo mobile
- `classnames`: Manipulação de classes CSS
- CSS Modules: Importação de estilos via `./styles.css`

## Observações

1. Requer configuração via Site Editor para personalização
2. Cards podem ter ou não imagens (layout se adapta)
3. Tracking requer Google Analytics configurado
4. Suporta upload de imagens via Site Editor
5. Label do link é customizável (default: "Comprar")
6. Suporta branding via `brandClass` para estilização específica
