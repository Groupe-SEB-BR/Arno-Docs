# Black Button

Componente para exibir um botão preto configurável com suporte a integração Croct para personalização dinâmica.

## Uso

react/BlackButton.tsx

```jsx
import BlackButton from './components/MenuMultiBranding/BlackButton';

export default BlackButton;
```

store/interfaces.json

```json
"arno-black-button": {
  "component": "BlackButton"
},
```

## Exemplos

```jsx
"flex-layout.row#black-btn-container": {
  "props": {
    "blockClass": "black-btn-container"
  },
  "children": ["arno-black-button"]
}
```

## Funcionalidades

### Botão Preto Configurável

O componente exibe um botão preto com:

- **Ícone Dinâmico**: Imagem configurável ou vazia
- **Texto Personalizável**: Texto do botão via props ou Croct
- **Link Configurável**: URL do botão
- **Integração Croct**: Busca conteúdo dinamicamente
- **Rastreamento**: Registra cliques de usuários

## Estrutura de Dados

### Propriedades do Componente

```typescript
{
  active: boolean,           // Ativa/desativa o botão
  activeCroct: boolean,      // Habilita integração Croct
  icon: string,              // URL da imagem do ícone
  link: string,              // URL do botão
  text: string               // Texto do botão
}
```

## Configuração via Schema

```typescript
{
  active: {
    type: 'boolean',
    title: 'Ativar Black Button',
    default: true
  },
  activeCroct: {
    type: 'boolean',
    title: 'Ativar integração com a Croct',
    default: false
  },
  icon: {
    title: 'Ícone do Black Button',
    type: 'string'
  },
  link: {
    title: 'Link do Black Button',
    type: 'string'
  },
  text: {
    title: 'Texto do Black Button',
    type: 'string'
  }
}
```

## Dependências

- `react`: Componente funcional com hooks
- `croct`: Integração para personalização dinâmica

## Observações

1. Quando `activeCroct` é true, o componente busca dados da Croct
2. Em caso de erro na Croct, usa valores padrão (VTEX)
3. Cliques são rastreados apenas para conteúdo Croct
4. Estilos definidos em `./style.css`
