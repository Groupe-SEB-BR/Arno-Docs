# Slider Hero

Este componente exibe um slider de banners na página inicial com suporte a Croct para personalização, tracking de cliques via Google Analytics e cronômetro countdown opcional.

![image](../../assets/slider-hero.png)

## Uso

react/SliderHero.tsx

```jsx
import SliderHero from './components/SliderHero';

export default SliderHero;
```

store/interfaces.json

```json
"arno-slider-hero": {
  "component": "SliderHero"
}
```

## Exemplos

```jsx
"store.home": {
  "children": ["arno-slider-hero"]
}
```

## Funcionalidades

### Slider de Banners

O componente exibe um carrossel de banners com:

- **Imagens Responsivas**: Banners diferentes para desktop e mobile
- **Navegação Automática**: Autoplay com transição suave
- **Dots de Navegação**: Indicadores visuais de posição
- **Pause on Hover**: Pausa ao passar o mouse

### Integração com Croct

- **Personalização Dinâmica**: Banners personalizados por URL
- **Rotas Suportadas**: Home (`/`), Rochedo (`/rochedo`), Tefal (`/tefal`)
- **Tracking**: Eventos de clique e goals personalizados

### Cronômetro Countdown

- **Ativação Opcional**: Controlado via Site Editor
- **Primeiro Slide**: Exibido apenas no primeiro banner
- **Estilos Diferentes**: Classes CSS distintas para mobile e desktop

### Sistema de Tracking

- **Google Analytics**: Evento `clicou_banner_{index}` 
- **Croct Goals**: `carousel-home-click`
- **ID de Tracking**: `G-WBSPVQFS2L`

## Estrutura de Dados

### Propriedades do Componente

```typescript
{
  croctActive: boolean,      // Ativa integração Croct
  enableCountdown: boolean,  // Ativa cronômetro
  targetDate: string,        // Data alvo (ISO 8601)
  slides: Array<{
    imageDesktop: string,    // URL imagem desktop
    imageMobile: string,     // URL imagem mobile
    link: string,            // URL de destino
    alt: string             // Texto alternativo
  }>
}
```

## Comportamento

### Renderização Condicional

1. **Loading**: Exibe componente Loading durante carregamento inicial
2. **Croct Ativo**: Usa banners do Croct se `croctActive` for `true`
3. **Fallback**: Usa slides do schema se Croct não retornar conteúdo

### Detecção de Dispositivo

- Breakpoint: `768px`
- Event listener para redimensionamento
- Limpeza de listeners no unmount

### Navegação com Tracking

Ao clicar em um banner:
1. Envia goal para Croct
2. Atualiza perfil do usuário
3. Dispara evento para Google Analytics

## Configuração de Slider

```javascript
{
  dots: true,
  infinite: true,
  autoplay: true,
  speed: 400,
  autoplaySpeed: 5000,
  slidesToShow: 1,
  slidesToScroll: 1,
  cssEase: 'ease-out',
  pauseOnHover: true
}
```

## Configuração via Schema

### Propriedades Principais

```typescript
{
  croctActive: {
    type: 'boolean',
    title: 'Ativar Croct',
    default: false
  },
  slides: {
    type: 'array',
    items: {
      imageDesktop: string,  // Upload via image-uploader
      imageMobile: string,   // Upload via image-uploader
      link: string,
      alt: string
    }
  },
  targetDate: {
    type: 'string',
    format: 'date-time',
    default: '2024-11-29T00:00:00'
  },
  enableCountdown: {
    type: 'boolean',
    title: 'Ativar Cronômetro',
    default: false
  }
}
```

## Estrutura de Classes CSS

- `#home-banner`: Container principal
- `.customTimerStyle1`: Estilo do countdown mobile
- `.customTimerStyle2`: Estilo do countdown desktop

## Dependências

- `react`: Hooks useState e useEffect
- `react-slick`: Componente de slider
- `slick-carousel`: CSS do carousel
- CSS Modules: Estilos do countdown
- Croct SDK: Personalização de conteúdo

## Observações

1. Requer configuração via Site Editor para personalização
2. Integração Croct opcional, funciona standalone
3. Cronômetro aparece apenas no primeiro slide quando ativado
4. Suporta upload de imagens via Site Editor
5. Tracking automático de cliques e goals
6. Rotas Croct configuradas: home, rochedo, tefal

