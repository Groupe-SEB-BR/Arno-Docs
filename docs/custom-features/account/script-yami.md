# Script Yami

Este componente injeta dinamicamente um botão de "Troca e Devolução" na página de pedidos, permitindo aos usuários acessar o portal de trocas e devoluções da Arno.

## Uso

react/ScriptYami.tsx

```jsx
import ScriptYami from './components/ScriptYami';

export default ScriptYami;
```

store/interfaces.json

```json
"arno-script-yami": {
  "component": "ScriptYami"
},
```

## Exemplos

```jsx
"store.account": {
  "blocks": [
    "arno-script-yami",
  ],
  "parent": {
    "challenge": "challenge.profile"
  }
},
```

## Funcionalidades

### Injeção Condicional de Botão

O componente injeta o botão de devolução apenas quando:

- A URL atual contém `orders`
- Cartões de pedidos estão presentes no DOM
- O botão ainda não foi adicionado

### Detecção de Pedidos

- **Monitoramento de DOM**: Aguarda carregamento dos cartões de pedidos
- **Retry Automático**: Redefine a verificação a cada 2.5 segundos se não encontrar pedidos
- **Limpeza Dinâmica**: Remove botões ao sair da página de pedidos

### Extração de Dados

- Obtém ID do pedido do elemento DOM
- Recupera email do usuário do `localStorage`
- Constrói URL personalizada para o portal de trocas

## Estrutura de Dados

### Estado do Componente

```javascript
{
  haveOrders: boolean; // Flag para controlar se botões já foram adicionados
}
```

### Dados Extraídos

```javascript
{
  orderId: string,      // ID do pedido (sem símbolos)
  userEmail: string,    // Email do usuário
  embedUrl: string      // URL com parâmetro embed para integração
}
```

## Comportamento

### Fluxo de Execução

1. Verifica se está na rota `/orders`
2. Aguarda carregamento dos cartões de pedidos
3. Extrai ID e email para cada pedido
4. Cria link "Troca e Devolução" apontando para portal externo
5. Remove botão nativo de cancelamento do VTEX
6. Monitora mudanças de rota para limpeza

### Renderização

O componente não renderiza nenhum elemento visual (retorna `null`), funcionando apenas com manipulação direta do DOM.

## Dependências

- `react`: Hooks (`useState`, `useEffect`)
- DOM API nativa: Seletores e manipulação de elementos
- `localStorage`: Acesso aos dados do carrinho/pedido

## Observações

1. Acessa `localStorage` para dados do cliente
2. Remove elemento nativo do VTEX My Orders App
3. Redefine estado ao sair de `/orders`
4. URL alvo do portal: `https://arno.troquefacil.com.br/order/{id}/{email}?embed=1`
5. Classe CSS customizada: `btn_devolucion`
