# Blog Home

Este componente renderiza a página inicial do blog com banner, categorias, abas e posts em destaque.

![image](../../assets/blog-home.png)

## Usage

react/Home.tsx

```jsx
import Home from './Pages/Home';

export default Home;
```

store/interfaces.json

```json
"lojaarno-blog-home": {
  "component": "Home"
},
```

## Examples

```jsx
"store.custom#blog-home": {
  "children": ["lojaarno-blog-home"]
},
```

## Route

```json
"store.custom#blog-home": {
  "path": "/blog",
  "isSitemapEntry": true
},
```

## Estrutura

O componente `Home` possui a seguinte estrutura hierárquica:

```text
Home (Component)
└── main
    ├── section (Banner)
    │   ├── img (imagem do banner)
    │   └── div (conteúdo do banner)
    │       ├── h1 (título)
    │       └── h2 (subtítulo)
    ├── section (Título)
    │   └── h3 (Busque por Categoria)
    ├── section (Abas)
    │   └── TabLayout
    │       ├── Tab: Categorias → CategoryCarousel
    │       ├── Tab: Produtos → Carousel
    │       └── Tab: Casa e Cozinha → CategoryCards
    ├── section (Post em Destaque)
    │   └── FeaturedPost
    └── section (Mais Acessados)
        └── Carousel
```

### Props

- **`imageDesktop`**: String com URL da imagem do banner desktop (padrão: `/arquivos/blog-banner.jpg`)
- **`imageMobile`**: String com URL da imagem do banner mobile (padrão: `/arquivos/blog-banner-mobile.jpg`)
- **`title`**: String com título do banner (padrão: `BLOG`)
- **`subtitle`**: String com subtítulo do banner (padrão: `Suas receitas preferidas em um só lugar.`)

### Estados Gerenciados

- **`blogBanner`**: String que armazena a URL da imagem do banner (desktop ou mobile)
- **`featuredPost`**: Objeto contendo o post mais visualizado para destaque

### Funcionalidades

#### Detecção de Dispositivo

Utiliza o hook `useDevice` do VTEX para detectar se o usuário está em mobile:

- Define a imagem do banner baseada no dispositivo
- Atualiza automaticamente ao mudar entre dispositivos

#### Carregamento do Post em Destaque

Busca o post mais visualizado através do serviço `getMostViewedPost`:

**Comportamento:**

- Executa ao montar o componente
- Busca o post com maior número de visualizações
- Atualiza o estado `featuredPost` com os dados retornados
- Passa o post para o componente `FeaturedPost`

#### Sistema de Abas

Define três abas configuradas no array `tabs`:

1. **Categorias**: Exibe `CategoryCarousel`
2. **Produtos**: Exibe `Carousel` ordenado por data de criação (DESC)
3. **Casa e Cozinha**: Exibe `CategoryCards`

### Componentes Renderizados

#### Banner Section

Seção de banner responsiva:

- Imagem adaptável (desktop/mobile)
- Título e subtítulo configuráveis
- Container centralizado para conteúdo

#### Tab Layout Section

Sistema de abas com conteúdo dinâmico:

- Componente `TabLayout` gerencia navegação entre abas
- Cada aba renderiza um componente específico
- Carrosséis e cards de categorias

#### Featured Post Section

Post em destaque:

- Renderiza componente `FeaturedPost`
- Exibe o post mais visualizado
- Carregado dinamicamente via API

#### Most Viewed Carousel

Carrossel de posts mais acessados:

- Componente `Carousel` com ordenação por visualizações
- Ordem descendente (mais visualizados primeiro)
- Título "Mais acessados"

### Schema de Configuração

O componente possui um schema para configuração no Site Editor:

```typescript
{
  title: 'Blog Home',
  type: 'object',
  properties: {
    title: string,           // Título do banner
    subtitle: string,        // Subtítulo do banner
    imageDesktop: string,    // Imagem desktop (com image-uploader)
    imageMobile: string,     // Imagem mobile (com image-uploader)
    featuredPost: number     // ID do post em destaque
  }
}
```

## Observações

1. A imagem do banner é responsiva e muda automaticamente entre desktop e mobile
2. O post em destaque é carregado dinamicamente através da API
3. Sistema de abas permite organizar diferentes tipos de conteúdo
4. Todos os textos e imagens são configuráveis via Site Editor

### Tratamento de Erros

- Em caso de erro ao buscar o post em destaque, o componente continua funcionando
- Estados inicializados com valores seguros

### Performance

- Usa `useEffect` para carregar dados apenas quando necessário
- Imagens são carregadas de forma otimizada
- Componentes filhos são carregados sob demanda nas abas

### Dependências

- `vtex.device-detector`: Detecção de dispositivo
- Componentes internos: `Carousel`, `CategoryCards`, `FeaturedPost`, `CategoryCarousel`, `TabLayout`
- Serviço: `getMostViewedPost` para buscar post mais visualizado
