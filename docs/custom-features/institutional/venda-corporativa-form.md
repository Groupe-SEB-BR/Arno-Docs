# Venda Corporativa Form

Componente de formulário para coleta de dados de clientes corporativos, permitindo o envio de informações de contato e CNPJ para solicitação de conta corporativa.

## Uso

react/VendaCorporativaForm.js

```javascript
import VendaCorporativaForm from './components/VendaCorporativaForm/index';

export default VendaCorporativaForm;
```

store/interfaces.json

```json
"arno-form-venda-corporativa": {
  "component": "VendaCorporativaForm"
},
```

## Exemplos

```jsx
"flex-layout.col#form-vendas-corporativas-info": {
  "children": [
    "rich-text#form-vendas-corporativas",
    "arno-form-venda-corporativa"
  ],
  "props": {
    "width": "64%",
    "blockClass": "form-vendas-corporativas-info"
  }
},
```

## Funcionalidades

### Campos do Formulário

- Nome completo (obrigatório)
- E-mail (obrigatório)
- Telefone (obrigatório)
- CNPJ (obrigatório)
- Checkbox de consentimento para comunicação

### Validação

- Validação de campos obrigatórios
- Validação específica de checkbox
- Feedback visual de erro no checkbox
- Prevenção de envio sem aceitar termos

### Envio de Dados

- POST para `/api/dataentities/VC/documents`
- Envio de dados estruturados
- Mensagem de sucesso após envio
- Limpeza de formulário após sucesso

## Comportamento

### Fluxo de Envio

1. Usuário preenche todos os campos
2. Marca checkbox de consentimento
3. Clica em "Enviar"
4. Validação do checkbox é verificada
5. Dados são enviados via POST
6. Mensagem de sucesso é exibida por 5 segundos
7. Formulário é resetado

### Fluxo de Erro

1. Usuário tenta enviar sem marcar checkbox
2. Classe de erro é aplicada ao checkbox
3. Envio é cancelado
4. Erro é limpo ao marcar checkbox novamente

## Dependências

- `react`: Hooks `useEffect`, `useState`
- `axios`: Requisições HTTP
- `./styles.css`: Estilos customizados

## Estados Gerenciados

- `name`: Nome completo do usuário
- `email`: E-mail do usuário
- `telefone`: Telefone de contato
- `cnpj`: CNPJ da empresa
- `accept`: Estado do checkbox de consentimento
- `success`: Indicador de sucesso no envio
- `errorAccept`: Indicador de erro na validação do checkbox

## API

### Endpoint Utilizado

```text
POST /api/dataentities/VC/documents
```

### Payload

```json
{
  "nome": "string",
  "email": "string",
  "telefone": "string",
  "cnpj": "string",
  "accept": "boolean"
}
```

## Observações

1. Todos os campos são obrigatórios
2. Checkbox é validado separadamente antes do envio
3. Mensagem de sucesso desaparece automaticamente após 5 segundos
4. Formulário é resetado após sucesso
5. Classe `error` é aplicada ao checkbox em caso de erro
6. Campo telefone e CNPJ aceitam apenas números
