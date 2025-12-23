# Coupon Form Minicart

Este componente fornece uma interface para aplicar e remover cupons de desconto no minicart, com sincronização automática dos preços e feedback visual para o usuário.

![image](../../assets/cupom.png)

## Uso

react/CustomFormMinicart.js

```javascript
import CustomFormMinicart from './components/CustomFormMinicart';

export default CustomFormMinicart;
```

store/interfaces.json

```json
"custom-cupom-minicart": {
  "component": "CustomFormMinicart"
},
```

## Exemplos

```jsx
"toggle-layout#content-cupom-minicart": {
  "title": "Cupom Minicart",
  "children": ["custom-cupom-minicart"],
  "props": {
    "blockClass": "content-cupom-minicart"
  }
},
```

## Funcionalidades

### Aplicação de Cupons

- Campo de entrada para código do cupom
- Botão para aplicar cupom
- Validação e feedback de erro/sucesso
- Loading state durante processamento

### Remoção de Cupons

- Exibe cupom ativo
- Botão para remover cupom aplicado
- Atualização automática do orderForm

### Sincronização de Preços

- Atualiza `sellingPrice` dos itens após aplicar/remover cupom
- Sincroniza `totalizers` e `value` do carrinho
- Mantém consistência dos dados do `orderForm`

### Feedback Visual

- Mensagens de sucesso/erro
- Spinner durante carregamento
- Auto-hide de mensagens após 3 segundos

## Comportamento

### Fluxo de Aplicação

1. Usuário insere código do cupom
2. Clica em "Adicionar"
3. Requisição POST para API de marketingData
4. Atualiza orderForm com novos preços
5. Exibe mensagem de sucesso/erro

### Fluxo de Remoção

1. Usuário clica em "Remover" no cupom ativo
2. Requisição POST com cupom null
3. Atualiza orderForm removendo desconto
4. Exibe mensagem de confirmação

## Dependências

- `react`: Hooks `useEffect`, `useState`
- `vtex.order-manager/OrderForm`: Hook `useOrderForm` para manipulação do carrinho
- `vtex.styleguide`: Componente `Spinner` para loading state
- `./style.css`: Estilos customizados

## Estados Gerenciados

- `couponCode`: Código do cupom inserido
- `loading`: Estado de carregamento
- `couponCodeReturn`: Objeto com status de erro/sucesso e mensagem

## API

### Endpoint Utilizado

```text
POST /api/checkout/pub/orderForm/{orderFormId}/attachments/marketingData
```

### Payload

```json
{
  "coupon": "CODIGO_CUPOM" // ou null para remover
}
```

## Observações

1. Mensagens desaparecem automaticamente após 3 segundos
2. Botões ficam desabilitados durante loading
3. Campo de cupom é limpo após aplicação
4. Validação de cupom vazio antes de aplicar
5. Tratamento de erros com mensagens amigáveis
