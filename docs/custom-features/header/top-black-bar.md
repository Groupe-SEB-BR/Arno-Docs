# Top Black Bar

Componente para exibir a barra preta superior com links configuráveis na página inicial.

## Uso

react/TopBlackBar.tsx

```jsx
import TopBlackBar from './components/MenuMultiBranding/TopBlackBar';

export default TopBlackBar;
```

store/interfaces.json

```json
"topblack-bar": {
  "component": "TopBlackBar",
  "render": "lazy"
},
```

## Exemplos

```jsx
"flex-layout.row#header-mobile": {
  "children": [
    "topblack-bar",
    "multibranding-menu",
    "flex-layout.row#searchbar-mob"
  ],
  "props": {
    "blockClass": "main-header-mobile",
    "preserveLayoutOnMobile": true,
    "horizontalAlign": "center",
    "verticalAlign": "middle",
    "fullWidth": true
  }
},
```

## Funcionalidades

### Barra Superior Configurável

O componente exibe uma barra preta com:

- **Texto da Loja Oficial**: Mensagem personalizável sobre a loja
- **Links Dinâmicos**: Blog e Bônus com URLs configuráveis
- **Responsivo**: Adapta-se a diferentes tamanhos de tela
- **Abertura em Nova Aba**: Links abrem em `target="_blank"`

## Estrutura de Dados

### Propriedades do Componente

```typescript
{
  blogLink: string,           // URL do blog
  blogText: string,           // Texto do link do blog
  bonusText: string,          // Texto do link de bônus
  bonusLink: string,          // URL de resgate de bônus
  officialStoreText: string   // Texto da loja oficial
}
```

## Configuração via Schema

### Propriedades Principais

```typescript
{
  blogLink: {
    title: 'Link do Blog',
    type: 'string',
    default: '/blog'
  },
  blogText: {
    title: 'Texto do Blog',
    type: 'string',
    default: 'Blog Arno.com'
  },
  bonusText: {
    title: 'Texto do Bônus',
    type: 'string',
    default: 'Resgate seu bônus'
  },
  bonusLink: {
    title: 'Link do Bônus',
    type: 'string',
    default: '/resgate-seu-bonus'
  },
  officialStoreText: {
    title: 'Texto da Loja Oficial',
    type: 'string',
    default: 'Loja oficial • Tudo em até 6x sem juros • Desconto no PIX'
  }
}
```

## Estrutura de Classes CSS

- `.black-bar`: Container principal da barra
- `.black-bar-content`: Conteúdo interno
- `.white-text`: Texto branco
- `.white-text-space`: Espaçador
- `.links`: Container dos links
- `.white-link`: Estilo dos links

## Dependências

- `react`: Componente funcional
- `prop-types`: Validação de props

## Observações

1. Todos os textos e links são configuráveis via Site Editor
2. Links abrem em nova aba automaticamente
3. Suporta valores vazios para textos opcionais
4. Estilos definidos em `./style.css`
