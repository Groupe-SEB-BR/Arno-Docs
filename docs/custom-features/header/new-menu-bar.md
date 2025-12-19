# Menu Bar

Esse componente é usado para listar os menus de navegação das diferentes marcas do site, em telas maiores que 1024 pixels de largura.

![image](../../assets/new-menu-bar.jpg)

## Uso

react/NewMenuBar.js

```jsx
import NewMenuBar from './components/MenuMultiBranding/NewMenuBar';

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

# Props do Componente NewMenuBar

| Prop              | Tipo      | Obrigatório? | Descrição                      | Valor Padrão |
| ----------------- | --------- | ------------ | ------------------------------ | ------------ |
| **activeArno**    | `boolean` | Não          | Ativa o Black Button Arno      | `true`       |
| **activeCroct**   | `boolean` | Não          | Ativa a integração com a Croct | `false`      |
| **iconArno**      | `string`  | Não          | Ícone do Black Button Arno     | -            |
| **linkArno**      | `string`  | Não          | Link do Black Button Arno      | -            |
| **textArno**      | `string`  | Não          | Texto do Black Button Arno     | -            |
| **activeRochedo** | `boolean` | Não          | Ativa o Black Button Rochedo   | `true`       |
| **iconRochedo**   | `string`  | Não          | Ícone do Black Button Rochedo  | -            |
| **linkRochedo**   | `string`  | Não          | Link do Black Button Rochedo   | -            |
| **textRochedo**   | `string`  | Não          | Texto do Black Button Rochedo  | -            |
| **activeTefal**   | `boolean` | Não          | Ativa o Black Button Tefal     | `true`       |
| **iconTefal**     | `string`  | Não          | Ícone do Black Button Tefal    | -            |
| **linkTefal**     | `string`  | Não          | Link do Black Button Tefal     | -            |
| **textTefal**     | `string`  | Não          | Texto do Black Button Tefal    | -            |

## Observações

1. Todos os props são **opcionais**, pois não há validação de tipos obrigatórios no código
2. Os valores padrão são definidos no schema do componente
3. O componente também recebe implicitamente `activeCroct` que é passado para os subcomponentes `ArnoMenu`, `RochedoMenu` e `TefalMenu`
4. A lógica de exibição é baseada na URL atual, determinando qual menu (Arno, Rochedo ou Tefal) será exibido

## Funcionamento do Componente

O componente `NewMenuBar` analisa a URL atual para decidir qual menu mostrar:

- **Arno Menu**: Mostrado quando a URL contém "arno", é a página inicial (`/`), ou não contém nenhuma das palavras-chave (arno, rochedo, clock, tefal)
- **Rochedo Menu**: Mostrado quando a URL contém "rochedo" ou "clock"
- **Tefal Menu**: Mostrado quando a URL contém "tefal"

O componente usa o estado interno para controlar qual menu está visível com base na URL.
