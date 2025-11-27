# Blog PDP

Esse componente é responsável por mostrar um dos posts do Blog Arno que seja relevante ao produto visualizado na página de produto

## Usage

react/BlogPDP.js

```jsx
import BlogPDP from './components/BlogPDP';

export default BlogPDP;
```

store/interfaces.json

```json
  "custom-arno-pdp-blog-session": {
    "component": "BlogPDP"
  },
```

## Props

| Prop         | Type             | Required | Default | Description                                                   |
| ------------ | ---------------- | -------- | ------- | ------------------------------------------------------------- |
| title        | string           | No       |         | Título acima da vitrine                                       |
| brandClass   | string           | Yes      | arno    | Identificação de qual marca se trata (Arno, Tefal ou Rochedo) |
| cards        | Array of objects | No       | []      | Array de objetos com os dados das categorias                  |
| shouldRender | boolean          | No       | false   | Deve renderizar o componente ou não?                          |

### Props de "cards"

Cada objeto no array de `cards` deve ter as seguintes propriedades:

| Property  | Type   | Required | Description                      |
| --------- | ------ | -------- | -------------------------------- |
| image     | string | No       | URL ou caminho da imagem do card |
| title     | string | No       | Título do card                   |
| subTitle  | string | No       | Subtítulo ou descrição do card   |
| linkUrl   | string | No       | URL de destino do botão CTA      |
| linkLabel | string | No       | Texto do botão CTA               |

## Examples

```jsx
  "flex-layout.row#blog-pdp": {
    "children": ["custom-arno-pdp-blog-session"],
    "props": {
      "blockClass": "pdp-blog-session"
    }
  },
```

## Notes

Additional information, gotchas, or important considerations when using this component.
