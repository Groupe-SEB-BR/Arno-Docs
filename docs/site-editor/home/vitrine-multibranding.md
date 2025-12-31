# Vitrine Multibranding

## Nome do componente

```text
Vitrine Multibranding
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas homes da loja (Arno, Rochedo e Tefal).

Caminho geral:

- Admin VTEX → CMS → Site Editor

(O componente pode ser utilizado em páginas que suportem blocos customizados de conteúdo.)

## Visão geral

O componente **Vitrine Multibranding** permite criar uma seção com **abas (tabs)** que exibem banners promocionais diferenciados por marca ou categoria. Cada aba pode conter múltiplos banners com imagens, textos e links.

É ideal para destacar múltiplas marcas ou linhas de produto em um único espaço visual.

## Campos do componente

### Deve aparecer

Controla se a seção será exibida no front-end.

- **Ligado** → a seção aparece no site
- **Desligado** → a seção não é renderizada

### Tabs (Abas)

Lista de abas que compõem a vitrine.

Clique em **"+ Adicionar"** para criar uma nova aba.

Cada aba representa uma marca ou categoria específica.

## Campos da Aba

Ao adicionar ou editar uma aba, os seguintes campos ficam disponíveis:

### ID

Identificador único da aba.

Exemplo:

```text
arno
```

### Title

Título exibido na aba.

Exemplo:

```text
Arno
```

### Cor da Sessão

Define a cor de destaque da aba (código hexadecimal).

Exemplo:

```text
#FF1805
```

Essa cor pode ser aplicada em bordas, fundos ou elementos visuais da aba ativa.

### Content (Conteúdo)

Lista de banners exibidos dentro da aba.

Clique em **"+ Adicionar"** para criar um novo banner.

## Campos do Banner

Ao adicionar ou editar um banner dentro de uma aba:

### Título do banner

Texto principal do banner.

Exemplo:

```text
Airfryer
```

### Descrição do banner

Texto secundário exibido abaixo do título.

Exemplo:

```text
Descontos de até 30%
```

### Link do banner

URL de destino ao clicar no banner.

Exemplo:

```text
/airfryer
```

### Texto do link

Texto exibido como chamada de ação (CTA).

Exemplo:

```text
Compre agora
```

### Imagem de fundo do banner

Imagem principal do banner.

Recomendações:

- Usar imagem em alta resolução
- Garantir boa leitura de textos sobre a imagem
- Testar em diferentes dispositivos

### Imagem de acento do banner - Esquerda

Imagem decorativa posicionada à esquerda do banner (opcional).

Pode ser usada para adicionar elementos visuais complementares.

### Imagem de acento do banner - Direita

Imagem decorativa posicionada à direita do banner (opcional).

Funciona como elemento visual de apoio ao conteúdo principal.

## Comportamento do componente

- A seção só aparece se **"Deve aparecer"** estiver ativada
- As abas são exibidas horizontalmente
- Ao clicar em uma aba, o conteúdo correspondente é exibido
- Cada banner dentro da aba é clicável
- O layout se adapta para desktop e mobile
- A cor da aba pode destacar visualmente a marca ativa

## Boas práticas

- Utilize cores consistentes com a identidade de cada marca
- Mantenha um número equilibrado de banners por aba
- Use imagens padronizadas entre os banners
- Evite textos longos nos títulos
- Verifique sempre se os links estão ativos
- Teste a navegação entre abas antes de publicar
- Revise o comportamento em dispositivos móveis

## Observações finais

- O componente é ideal para ambientes multibranding
- Permite organizar conteúdo por marca ou categoria de forma visual
- Toda a gestão é feita diretamente pelo Site Editor
- Não requer configuração técnica adicional
