# Slider Hero

## Nome do componente

```text
Slider Hero
```

![image](../../assets/site-editor/slider-hero.png)

## Visão Geral

O Slider Hero é um componente de carrossel de imagens posicionado no topo da página inicial. Este componente exibe uma sequência de banners promocionais em rotação automática, otimizados tanto para desktop quanto para dispositivos móveis. Cada slide contém uma imagem específica para cada tipo de dispositivo e um link de destino, permitindo direcionar os usuários para páginas de produtos, promoções ou categorias específicas. É um elemento estratégico para destacar campanhas, lançamentos e ofertas principais da loja.

## Onde encontrar

Home Arno, Tefal e Rochedo.

URLs de acesso:

- [lojaarno.myvtex.com/admin/cms/site-editor](https://lojaarno.myvtex.com/admin/cms/site-editor)
- [lojaarno.myvtex.com/admin/cms/site-editor/tefal](https://lojaarno.myvtex.com/admin/cms/site-editor/tefal)
- [lojaarno.myvtex.com/admin/cms/site-editor/rochedo](https://lojaarno.myvtex.com/admin/cms/site-editor/rochedo)

## Campos

![image](../../assets/site-editor/slider-hero-campos.png)
![image](../../assets/site-editor/slider-hero-campos-2.png)

### Ativar Croct

Esse campo foi descontinuado

### Slides

![image](../../assets/site-editor/slider-hero-campos-slides.png)

Campo que recebe todas as imagens que vão ser renderizadas no Slider da home.

#### Banner Desktop

Imagem em alta resolução otimizada para visualização em desktops e tablets em modo paisagem.

Dimensões recomendadas: `1920x540px`

#### Banner Mobile

Imagem otimizada para dispositivos móveis em modo retrato.

Dimensões recomendadas: `506x640px`

#### Link

URL de destino quando o usuário clicar no slide. Deve ser um link relativo à raiz do site.

Exemplo: `/promocoes` ou `/produtos/panelas`

#### Alt

Texto alternativo descritivo da imagem para acessibilidade e SEO.

Exemplo: `Promoção de panelas com até 50% de desconto`

### Data Alvo

Esse campo foi descontinuado

### Ativar Cronômetro

Esse campo foi descontinuado

## Observações

- Recomenda-se usar imagens otimizadas para web para melhor performance
- Todas as imagens devem conter texto alternativo (alt) para acessibilidade
- O slider é responsivo e se adapta automaticamente ao tamanho da tela

## Comportamento

- Transição automática entre slides
- Navegação manual disponível através de setas ou indicadores
- As imagens são otimizadas e carregadas de forma responsiva
- Links abrem na mesma aba por padrão
