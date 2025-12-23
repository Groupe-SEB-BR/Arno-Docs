# Black Friday 2025

Componente da página de Black Friday 2025 para Arno, Rochedo e Tefal, integrando banners, vitrines de produtos, barra de benefícios e conteúdo SEO.

## Uso

```javascript
import BlackFriday2025v2 from './components/BlackFriday2025v2';

export default BlackFriday2025v2;
```

interfaces.json

```json
"custom-arno-black-friday-2025-v2": {
  "component": "BlackFriday2025v2"
},
```

## Exemplos

```json
{
  "store.custom#arno-lp-black-friday-25-v2": {
    "children": [
      "custom-arno-meta-tags",
      "custom-arno-data-structure",
      "custom-arno-black-friday-2025-v2"
    ]
  }
}
```

## Estrutura

```text
BlackFriday2025 (Component)
├── div (container principal)
│   └── Banner
│   └── Bar
│   └── Shelf Flash Sales
│   └── Shelf Progressive Discounts
│   └── Seo
```

## Funcionalidades

### Componentes Filhos

- `Banner`: Banner principal acima da dobra
- `Bar`: Barra de benefícios
- `Shelfv2`: Vitrines de produtos com promoções. Para mais detalhes ver [Ofertas Relâmpago](./../shelves/ofertas-relampago.md)
- `Seo`: Conteúdo otimizado para SEO

### Scroll Automático para Promoções

- Detecção de hash URLs (`#ofertas-relampago`, `#descontos-progressivos`)
- Scroll suave com offset de 120px
- MutationObserver para elementos carregados dinamicamente
- Limpeza automática após 5 segundos

## Props

- `aboveTheFold`: Objeto com título, descrição e subtítulo
- `barContent`: Array de objetos com ícone e descrição de benefícios
- `seoContent`: Array com título e descrição meta
- `activePromotions`: Array de duas vitrines com produtos em promoção

## Dependências

- `react`: Hooks `useEffect`
- `vtex.render-runtime`: Hook `useRuntime`
- Componentes customizados: `Bar`, `Shelfv2`, `Banner`, `Seo`, `SpecialSelection`
