# Barra de Benefícios

## Nome do componente

```text
Linha
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas homes da loja (Arno, Rochedo e Tefal).

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Visão geral

O componente **Barra de Benefícios** permite criar uma seção composta por **textos e ícones**, normalmente usados para destacar benefícios que o usuário tem ao comprar na loja.

Cada sessão possui ícone, título e descrição, essa que pode conter links.

## Campos do componente

### Item 1 - icons benefícios

#### Image

Campo para inserir o ícone que será renderizado ao lado do texto. Possui diversas configurações adicionais, como title, nofollow, url, texto alternativo e título da imagem. Também possui campo para configurar o evento do Analytics que será disparado quando clicado. Além disso, é possível escolher a estratégia de carregamento do componente e a prioridade que ele terá na fila.

#### Rich Text

Campo de texto em markdown para configurar título e descrição da sessão. Exemplo:

```text
### Até 6x sem juros

Condições exclusivas de pagamento com parcela mínima de R$ 50
```

Os outros campos `Item 2 - icons benefícios`, `Item 3 - icons benefícios`, `Item 4 - icons benefícios` e `Item 5 - icons benefícios` seguem a mesma lógica.

### Aplicar

Após preencher os campos do card, clique em **APLICAR** para salvar.

## Boas práticas

- Utilize imagens padronizadas entre os cards
- Evite textos longos nos títulos
- Verifique sempre se os links estão ativos
- Revise o comportamento em mobile antes de publicar

## Observações finais

- A gestão do conteúdo é feita diretamente pelo Site Editor
- Caso for necessário excluir um dos itens, será preciso que um desenvolvedor exclua ele no código e faça o deploy.
