# Shelf Lançamentos

## Nome do componente

```text
Shelf Lançamentos
└── Container
  └── Shelf Lançamentos
  └── Banner Lançamentos
└── Container
  └── Shelf Lançamentos
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas homes da loja (Arno, Rochedo e Tefal).

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Visão geral

O componente **Shelf Lançamentos** permite exibir uma vitrine com ou sem um banner customizado.

- Exibição ou não da sessão
- Configuração da vitrine.

## Campos do componente

### Container

Temos dois containers dentro do componente **Shelf Lançamentos**. O primeiro container contém a vitrine com o banner customizado. O segundo container contém apenas a vitrine.

Dentro do Container existe apenas uma opção:

#### Dever aparecer?

- **Ligado** → a vitrine aparece no site
- **Desligado** → a vitrine não é renderizada

### Shelf Lançamentos - Lista de produtos

### ID da categoria

Define a categoria base da listagem.

- Para subcategorias, utilize o caractere `/` para indicar a hierarquia

Exemplo:

```text
1/2/3
```

### Filtros de especificação

Permite adicionar filtros específicos baseados em especificações do produto.

Clique em **“+ Adicionar”** para incluir novos filtros.

Esses filtros refinam os produtos exibidos na lista.

### Coleção

ID da coleção VTEX utilizada como fonte dos produtos.

Exemplo:

```text
281
```

Pode ser usada isoladamente ou em conjunto com categoria e filtros.

### Ordenação da lista

Define o critério de ordenação dos produtos.

Exemplo:

```text
Data de lançamento
```

Outros critérios podem estar disponíveis conforme a configuração da loja.

### Ocultar itens não disponíveis

Quando ativado, produtos indisponíveis (sem estoque) não são exibidos.

- **Ligado** → exibe apenas produtos disponíveis
- **Desligado** → exibe todos os produtos

### Quantidade máxima de itens

Define o número máximo de produtos exibidos na lista.

Exemplo:

```text
10
```

### Filtro de SKUs

Controla quais SKUs serão considerados.

Esse filtro impacta diretamente na disponibilidade exibida.

### Parcelamento

Define a regra de parcelamento exibida nos produtos.

Exemplo:

```text
Máximo sem juros
```

### Nome da lista no Analytics

Nome utilizado para identificação da lista em ferramentas de analytics.

Esse campo facilita:

- Análise de performance
- Rastreamento de cliques
- Relatórios de conversão

### Produtos patrocinados

#### Mostrar produtos patrocinados contextuais

Ativa a exibição de produtos patrocinados dentro da lista.

- **Ligado** → produtos patrocinados podem ser exibidos
- **Desligado** → apenas produtos regulares

#### Quantidade máxima de produtos patrocinados

Define o número máximo de produtos patrocinados exibidos.

Exemplo:

```text
2
```

#### Quantidade de produtos normais antes dos patrocinados

Define quantos produtos regulares devem aparecer antes dos patrocinados.

Esse controle ajuda a equilibrar experiência do usuário e monetização.

#### Repetir produtos patrocinados e regulares

Quando ativado, permite repetição de produtos patrocinados ao longo da lista.

Usar com cautela para não impactar negativamente a experiência do usuário.

### Banner Lançamentos

O banner é exibido acima ou ao lado da vitrine de produtos, dependendo da quantidade de itens.

#### Título

Define o título principal do banner.

Exemplo:

```text
Novos Lançamentos
```

Recomenda-se usar textos curtos e atrativos.

#### Texto Descritivo

Descrição complementar exibida no banner.

Exemplo:

```text
Confira as novidades que acabaram de chegar
```

Este campo aceita textos maiores para detalhar a campanha.

#### Imagem de Acento - Esquerda

Imagem decorativa posicionada à esquerda do banner.

- Utilize imagens leves (PNG ou SVG)
- Recomenda-se dimensões otimizadas para web

#### Imagem de Acento - Direita

Imagem decorativa posicionada à direita do banner.

- Utilize imagens leves (PNG ou SVG)
- Recomenda-se dimensões otimizadas para web

#### Imagem do Banner

Imagem principal do banner de lançamentos.

Formato recomendado:

- **Largura:** conforme padrão da loja
- **Formato:** JPG ou PNG otimizado
- **Peso:** máximo 200KB para melhor performance

#### Link do Banner

URL de destino ao clicar no banner.

Exemplo:

```text
/lancamentos
```

Pode direcionar para:

- Página de categoria
- Landing page específica
- Coleção de produtos

## Comportamento do componente

O componente **Shelf Lançamentos** possui dois modos de exibição controlados pelos containers:

### Modo 1: Vitrine com Banner

Quando o primeiro container está ativo, a shelf é exibida com:

- Banner customizado posicionado conforme layout
- Lista de produtos baseada nos filtros configurados
- Responsividade automática entre desktop e mobile

### Modo 2: Vitrine Simples

Quando o segundo container está ativo:

- Apenas a lista de produtos é exibida
- Sem banner decorativo
- Ocupa toda a largura disponível

### Carregamento de Produtos

O componente busca produtos seguindo esta ordem de prioridade:

1. **Coleção** (se definida)
2. **Categoria** + **Filtros de especificação**
3. Ordenação aplicada ao resultado final

### Interação do Usuário

- Produtos são exibidos em formato de carrossel horizontal
- Setas de navegação aparecem quando há mais itens do que a área visível
- Clique no banner redireciona para o link configurado
- Clique nos produtos leva para a página de detalhe (PDP)

### Atualização de Conteúdo

- Alterações no Site Editor são refletidas imediatamente após salvar
- Produtos indisponíveis são ocultados automaticamente se a opção estiver ativa

## Boas práticas

- Otimize as imagens do banner para garantir carregamento rápido (máximo 200KB)
- Configure corretamente a coleção antes de ativar a exibição no site
- Utilize textos curtos e objetivos no título e descrição do banner
- Teste a responsividade em diferentes dispositivos antes de publicar
- Defina um nome claro no Analytics para facilitar o acompanhamento de métricas
- Equilibre produtos patrocinados e regulares para manter boa experiência do usuário
- Mantenha a quantidade de itens adequada ao tamanho da tela (recomendado: 8 a 12 produtos)

## Observações finais

- O componente depende diretamente da configuração correta da categoria ou coleção
- Produtos sem estoque podem ser ocultados automaticamente através da opção "Ocultar itens não disponíveis"
- O controle é feito 100% via Site Editor, sem necessidade de código ou desenvolvimento
- Alterações são refletidas imediatamente após salvar no Site Editor
- Certifique-se de que os filtros de especificação estão corretos para evitar listagens vazias
- O banner é opcional e pode ser desativado através do container correspondente
