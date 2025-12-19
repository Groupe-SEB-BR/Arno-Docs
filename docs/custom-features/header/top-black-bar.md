# Black Bar

Esse componente é usado para informar ao usuário sobre promoções e listar o link do blog de Arno na versão Desktop. Ele é posicionado como o primeiro componente em todas as páginas do site. O conteúdo é editável pelo Site Editor da VTEX.

![image](../../assets/top-black-bar.jpg)

## Uso

react/TopBlackBar.js

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
  "flex-layout.row#topblack-bar": {
    "title": "Top BlackBar",
    "children": ["topblack-bar"],
    "props": {
      "verticalAlign": "center",
      "horizontalAlign": "center",
      "blockClass": ["topblackbar"]
    }
  }
```

## Props do Componente TopBlackBar

| Prop                  | Tipo     | Obrigatório? | Descrição                  | Valor Padrão                                                  |
| --------------------- | -------- | ------------ | -------------------------- | ------------------------------------------------------------- |
| **blogLink**          | `string` | Não          | Link para o blog           | `'/blog'`                                                     |
| **blogText**          | `string` | Não          | Texto do link do blog      | `'Blog Arno.com'`                                             |
| **bonusText**         | `string` | Não          | Texto do link de bônus     | `''` (string vazia)                                           |
| **bonusLink**         | `string` | Não          | Link para resgate de bônus | `''` (string vazia)                                           |
| **officialStoreText** | `string` | Não          | Texto da loja oficial      | `'Loja oficial • Tudo em até 6x sem juros • Desconto no PIX'` |

## Observações

1. Todos os props são **opcionais** e possuem valores padrão definidos em `defaultProps`
2. O componente exibe uma barra preta superior com links configuráveis
3. Os links abrem em nova aba (`target="_blank"`)
4. Há um espaço reservado vazio (`white-text-space`) antes do texto da loja oficial

## Comportamento

- O texto da loja oficial é exibido sempre (usa valor padrão se não fornecido)
- O link de bônus só aparece se `bonusText` e `bonusLink` forem fornecidos
- O link do blog só aparece se `blogText` e `blogLink` forem fornecidos
- Todos os links abrem em nova aba do navegador

## Valores Padrão

Os valores padrão são definidos de duas formas:

1. No schema do componente (para fins de documentação)
2. Em `defaultProps` (valores reais usados pelo React)

**Nota:** Há uma inconsistência nos valores padrão entre o schema e `defaultProps`:

- `bonusText`: No schema tem `'Resgate seu bônus'`, mas em `defaultProps` é `''`
- `bonusLink`: No schema tem `'/resgate-seu-bonus'`, mas em `defaultProps` é `''`
- `blogText`: No schema tem `'Blog Arno.com'`, e em `defaultProps` também

O React usará os valores de `defaultProps` quando os props não forem fornecidos.
