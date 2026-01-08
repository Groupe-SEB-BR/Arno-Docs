# Black Friday 2025

Componente da página de Black Friday 2025 para Arno, Rochedo e Tefal, integrando banners, vitrines de produtos, barra de benefícios e conteúdo SEO.

## Uso

```javascript
import BlackFridayLP from './components/BlackFridayLP';

export default BlackFridayLP;
```

interfaces.json

```json
"custom-arno-black-friday-lp": {
  "component": "BlackFridayLP"
},
```

## Exemplos

```json
{
  "store.custom#arno-lp-black-friday-25": {
    "children": [
      "custom-arno-meta-tags",
      "custom-arno-data-structure",
      "custom-arno-black-friday-lp"
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
│   └── FlashSales (Ofertas Relâmpago)
│   └── FlashSales (Descontos Progressivos)
│   └── Seo
```

## Funcionalidades

### Componentes Filhos

- `Banner`: Banner principal acima da dobra
- `Bar`: Barra de benefícios
- `FlashSales`: Vitrines de produtos com promoções (ofertas relâmpago e descontos progressivos). Para mais detalhes ver [Flash Sales](./../shelves/flash-sales.md)
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
- `activePromotions`: Configuração da vitrine de ofertas relâmpago (ID da coleção, título, descrição, imagem e items com datas)
- `commonShelf`: Configuração da vitrine de descontos progressivos (ID da coleção, título, descrição, imagem, texto e link do CTA)

## Dependências

- `react`: Hooks `useEffect`
- `vtex.render-runtime`: Hook `useRuntime`
- Componentes customizados: `Bar`, `Banner`, `Seo`, `FlashSales`
