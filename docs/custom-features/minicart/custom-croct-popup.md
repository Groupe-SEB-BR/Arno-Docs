# Minicart Checker Popup

Componente que monitora alterações no carrinho e exibe um popup com cupom de desconto após um período configurável. Ideal para capturar a atenção do usuário após adicionar produtos ao carrinho.

## Uso

```javascript
import MinicartChecker from './components/MinicartChecker';

export default MinicartChecker;
```

```json
"custom-arno-minicart-checker": {
  "component": "MinicartChecker"
}
```

## Exemplo

```jsx
"minicart": {
  "blocks": ["minicart-base-content"],
  "children": ["custom-arno-minicart-checker"]
}
```

## Funcionalidades

### Monitoramento de Carrinho

- Detecta adição de novos itens ao carrinho
- Verifica alterações a cada 5 segundos
- Limpa timers anteriores ao detectar novo item

### Responsividade

- Detecção automática de mobile (≤1024px)
- Imagens e cupons específicos por device
- Redimensionamento em tempo real

### Popup com Cupom

- Overlay customizável por device
- Botão de fechamento
- Cópia de cupom para clipboard
- Feedback ao usuário via alert

## Props

| Prop             | Tipo   | Descrição                                |
| ---------------- | ------ | ---------------------------------------- |
| `desktopImage`   | string | URL da imagem exibida em desktop         |
| `mobileImage`    | string | URL da imagem exibida em mobile          |
| `displayMinutes` | number | Tempo (em minutos) antes de exibir popup |
| `desktopCoupon`  | string | Código do cupom para desktop             |
| `mobileCoupon`   | string | Código do cupom para mobile              |

## Dependências

- `react`: Hooks `useEffect`, `useState`
- `prop-types`: Validação de props
- `vtex.order-manager/OrderForm`: Hook `useOrderForm`
- `./style.css`: Estilos customizados

## Estados Gerenciados

- `previousItems`: Snapshot anterior de itens do carrinho
- `showPopup`: Controla visibilidade do popup
- `timerId`: ID do timeout para delay de exibição
- `isMobile`: Flag de detecção de dispositivo

## Comportamento

1. Monitora mudanças no `orderForm` a cada 5 segundos
2. Detecta quando novo item é adicionado ao carrinho
3. Aguarda `displayMinutes` minutos antes de exibir popup
4. Popup é responsivo baseado no tamanho da tela
5. Clique no overlay (fora do popup) fecha o componente
6. Clique na imagem copia o cupom para clipboard
7. Botão "X" fecha o popup manualmente

## Observações

1. Popup só renderiza quando `showPopup` é true
2. Timer é limpo ao adicionar novo item
3. Event listener de resize é removido ao desmontar
4. Cupom é copiado automaticamente ao clicar na imagem
5. Alert confirma sucesso na cópia do cupom
