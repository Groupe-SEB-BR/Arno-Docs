# Main Categories

## Nome do componente

```text
Main Categories
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas homes da loja (Arno, Rochedo e Tefal).

Caminho geral:

- Admin VTEX → CMS → Site Editor

(O componente pode ser utilizado em páginas que suportem blocos customizados de conteúdo.)

## Visão geral

O componente **Main Categories** permite exibir as principais categorias da loja em formato de cards, com título, descrição, imagem e link.

Cada card funciona como um atalho visual para páginas de categoria, facilitando a navegação do usuário.

## Campos do componente

### Deve aparecer

Controla se a seção será exibida no front-end.

- **Ligado** → a seção aparece no site
- **Desligado** → a seção não é renderizada

### Categories

Área onde são cadastradas as categorias exibidas na seção.

Clique em **"+ Adicionar"** para criar uma nova categoria.

As categorias aparecem em formato de cards visuais com imagem, textos e link clicável.

## Campos da Categoria

Ao adicionar ou editar uma categoria, os seguintes campos ficam disponíveis:

### Category Title

Título da categoria.

Exemplo:

```text
Airfryer
```

### Category Description

Descrição da categoria, exibida abaixo do título. Não está sendo utilizado atualmente, deve ser removido do código assim que possível.

Exemplo:

```text
Descontos de até 30%
```

### Category Link

URL para onde o usuário será direcionado ao clicar no card.

Exemplo:

```text
/airfryer
```

Campo opcional.

### Category Image

Imagem representativa da categoria.

Recomendações:

- Usar imagem em boa resolução
- Todas as imagens devem ser centralizadas verticalmente e horizontalmente baseado na borda redonda que existe no layout. Todas devem ter o mesmo tamanho.
- Garantir boa leitura em diferentes tamanhos de tela.

## Comportamento do componente

- A seção só aparece se a opção **"Deve aparecer"** estiver ativada
- As categorias são exibidas na ordem configurada
- Cada card é totalmente clicável (quando possui link)
- O layout se adapta automaticamente para desktop e mobile

## Boas práticas

- Utilize imagens padronizadas entre os cards
- Mantenha títulos curtos e objetivos
- Verifique sempre se os links estão ativos
- Revise o comportamento em mobile antes de publicar

## Observações finais

- O componente é ideal para destacar as principais categorias da loja
- Não requer configuração técnica adicional
- Toda a gestão é feita diretamente pelo Site Editor
