# Home Popup

Este componente exibe um modal de newsletter na página inicial, oferecendo desconto na primeira compra para novos cadastros.

![image](../../assets/home-popup.png)

## Uso

react/HomePopUp.tsx

```jsx
import HomePopUp from './components/HomePopUp/HomePopUp';

export default HomePopUp;
```

store/interfaces.json

```json
"home-popup": {
  "component": "HomePopUp"
},
```

## Exemplos

```jsx
"store.home": {
  "children": ["home-popup"]
}
```

## Funcionalidades

### Exibição do Modal

O popup é exibido automaticamente baseado em diferentes condições:

- **Desktop**: Aparece quando o cursor do mouse sai da área visível da página (mouse leave)
- **Mobile**: Aparece automaticamente após 10 segundos
- **Persistência**: Usa `localStorage` para não exibir novamente após ser fechado pelo usuário

### Formulário de Cadastro

O componente gerencia um formulário com os seguintes campos:

- **Nome** (obrigatório)
- **E-mail** (obrigatório, com validação)
- **Telefone** (opcional, formatado automaticamente)
- **Aceite de termos** (obrigatório)
- **Aceite SMS/WhatsApp** (opcional, torna o telefone obrigatório)

### Validações

- **E-mail**: Validação em tempo real usando regex
- **Termos**: Obrigatório para envio do formulário
- **Telefone**: Obrigatório apenas se o checkbox de SMS for marcado
- **SMS**: Exibe erro se o telefone estiver preenchido mas o checkbox não estiver marcado

### Formatação

- **Telefone**: Formatação automática no padrão (XX) XXXXX-XXXX

## Estados Gerenciados

O componente utiliza os seguintes estados:

- `showPopup`: Controla a exibição do modal
- `name`, `email`, `phone`: Valores dos campos do formulário
- `terms`, `smsChecked`: Estados dos checkboxes
- `success`: Indica envio bem-sucedido
- `errorTerms`, `errorNlPhone`, `errorSms`: Controle de erros
- `isValidEmail`: Validação de e-mail
- `windowWidth`: Largura da janela para responsividade

## Fluxo de Sucesso

Após o envio bem-sucedido:

1. Exibe mensagem de sucesso com código de desconto (**BOASVINDAS10**)
2. Limpa todos os campos do formulário
3. Aguarda 10 segundos
4. Redireciona para URL com parâmetros UTM
5. Fecha o modal e salva o estado no `localStorage`

## Integração com API

Envia os dados para o Masterdata da VTEX:

```javascript
POST /api/dataentities/NL/documents
{
  "nome": string,
  "phone": string,
  "email": string,
  "terms": boolean,
  "sms": boolean,
  "origin": "popup"
}
```

## Responsividade

- Imagens diferentes para desktop e mobile
- Desktop: `popup-desktop.png`
- Mobile (≤480px): `popup-mobile.png`

## Redirecionamento

Após cadastro bem-sucedido, redireciona com UTM parameters:

```text
?utm_source=.NSE&utm_medium=email&utm_campaign=1QnK9Q_BR_ARN_NSP_.NSF_.NSSFP_.1NSE_NA_NA_NA_NA_COLL
```

## Observações

1. Utiliza o componente `Modal` do VTEX Styleguide
2. Requer biblioteca `axios` para requisições HTTP
3. O popup não reaparece após ser fechado (gerenciado via `localStorage`)
4. Desconto limitado a R$ 50,00 e não cumulativo com outras promoções
