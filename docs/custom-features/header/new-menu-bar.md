# New Menu Bar

Componente para exibir uma barra de menu superior com suporte multi-brand (Arno, Rochedo, Tefal) com detecção automática de URL.

## Uso

react/NewMenuBar.tsx

```jsx
import NewMenuBar from "./components/MenuMultiBranding/NewMenuBar";

export default NewMenuBar;
```

store/interfaces.json

```json
"newmenu": {
  "component": "NewMenuBar",
  "render": "lazy"
},
```

## Exemplos

```jsx
"flex-layout.row#newmenu-bar": {
  "children": ["newmenu"],
  "props": {
    "verticalAlign": "center",
    "blockClass": ["newmenubar"]
  }
},
```

## Funcionalidades

### Menu Multi-Brand

O componente exibe diferentes menus baseado na URL:

- **Arno**: Menu padrão para URLs contendo "arno", homepage ou URLs não reconhecidas
- **Rochedo/Clock**: Menu específico para URLs contendo "rochedo" ou "clock"
- **Tefal**: Menu específico para URLs contendo "tefal"
- **Detecção Automática**: Identifica a marca pela URL atual
- **Integração Croct**: Suporte opcional para personalização via Croct

## Estrutura de Dados

### Propriedades do Componente

```typescript
{
  activeArno: boolean,          // Ativa menu Arno
  activeCroct: boolean,         // Ativa integração Croct
  iconArno: string,             // Ícone do botão Arno
  linkArno: string,             // URL do botão Arno
  textArno: string,             // Texto do botão Arno
  activeRochedo: boolean,       // Ativa menu Rochedo
  iconRochedo: string,          // Ícone do botão Rochedo
  linkRochedo: string,          // URL do botão Rochedo
  textRochedo: string,          // Texto do botão Rochedo
  activeTefal: boolean,         // Ativa menu Tefal
  iconTefal: string,            // Ícone do botão Tefal
  linkTefal: string,            // URL do botão Tefal
  textTefal: string             // Texto do botão Tefal
}
```

## Configuração via Schema

```typescript
{
  activeCroct: {
    type: 'boolean',
    title: 'Ativar integração com a Croct',
    default: false
  },
  activeArno: {
    type: 'boolean',
    title: 'Ativar Black Button Arno',
    default: true
  },
  iconArno: {
    title: 'Ícone do Black Button Arno',
    type: 'string'
  },
  linkArno: {
    title: 'Link do Black Button Arno',
    type: 'string'
  },
  textArno: {
    title: 'Texto do Black Button Arno',
    type: 'string'
  },
  activeRochedo: {
    type: 'boolean',
    title: 'Ativar Black Button Rochedo',
    default: true
  },
  iconRochedo: {
    title: 'Ícone do Black Button Rochedo',
    type: 'string'
  },
  linkRochedo: {
    title: 'Link do Black Button Rochedo',
    type: 'string'
  },
  textRochedo: {
    title: 'Texto do Black Button Rochedo',
    type: 'string'
  },
  activeTefal: {
    type: 'boolean',
    title: 'Ativar Black Button Tefal',
    default: true
  },
  iconTefal: {
    title: 'Ícone do Black Button Tefal',
    type: 'string'
  },
  linkTefal: {
    title: 'Link do Black Button Tefal',
    type: 'string'
  },
  textTefal: {
    title: 'Texto do Black Button Tefal',
    type: 'string'
  }
}
```

## Dependências

- `react`: Hooks (useState, useEffect)
- `ArnoMenu`, `RochedoMenu`, `TefalMenu`: Componentes de menu específicos
- `./style.css`: Estilos do componente

## Observações

1. Detecção de URL ocorre no mount do componente
2. Suporta regex para identificação de padrões de URL
3. Todos os textos, ícones e links são configuráveis via Site Editor
4. Integração Croct é opcional via propriedade `activeCroct`
5. Menu Arno é exibido como padrão para URLs não reconhecidas
