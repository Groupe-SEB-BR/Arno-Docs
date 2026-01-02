# SEO Home

## Nome do componente

```text
HOME: SEO text - Container > Componente ver mais > SEO text - home
Páginas de categoria/coleções: Ativar/Desativar texto SEO > SEO text - Container > Componente ver mais > SEO text - Search
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas homes da loja (Arno, Rochedo e Tefal).

Caminho geral:

- Admin VTEX → CMS → Site Editor

(O componente pode ser utilizado em páginas que suportem blocos customizados de conteúdo.)

## Visão geral

O componente **Seleção Especial** permite criar uma seção composta por **cards promocionais**, normalmente usados para destacar categorias, linhas de produto ou campanhas específicas.

Cada card possui imagem, título, subtítulo e link, funcionando como um atalho visual para páginas estratégicas.

## Campos do componente

### Deve aparecer

Controla se a seção será exibida no front-end.

- **Ligado** → a seção aparece no site
- **Desligado** → a seção não é renderizada

### Classe da Marca

Define a classe de marca utilizada para personalização visual (CSS).

Exemplo:

```text
arno
```

Essa classe pode ser usada para:

- Aplicar estilos específicos por marca
- Controlar variações visuais

### Título

Título principal exibido no topo da seção.

Exemplo:

```text
Seleção Especial
```

Pode ser ajustado conforme a campanha ou ação promocional.

## Cards

Área onde são cadastrados os cards exibidos dentro da seção.

Clique em **“+ Adicionar”** para criar um novo card.

Os cards aparecem em formato visual com imagem, textos e link clicável.

## Campos do Card

Ao adicionar ou editar um card, os seguintes campos ficam disponíveis:

### Título do Card

Texto principal do card.

Exemplo:

```text
Airfryer
```

Usado para identificar a categoria ou destaque.

### Subtítulo do Card

Texto secundário exibido abaixo do título.

Exemplo:

```text
Descontos de até 30%
```

Ideal para chamadas promocionais ou benefícios.

### Banner Desktop

Imagem principal do card. Opcional.

Recomendações:

- Usar imagem em boa resolução
- Priorizar imagens horizontais
- Garantir boa leitura em diferentes tamanhos de tela

Essa imagem representa visualmente a categoria ou campanha.

### URL do Link

Endereço para onde o usuário será direcionado ao clicar no card.

Exemplo:

```text
/ofertas
```

### Texto do Link

Texto exibido como chamada de ação (CTA).

Exemplo:

```text
Aproveite
```

Deve ser curto, claro e orientado à ação.

### Aplicar

Após preencher os campos do card, clique em **APLICAR** para salvar.

O card passará a aparecer na lista e poderá ser reordenado.

## Comportamento do componente

- A seção só aparece se a opção **“Deve aparecer”** estiver ativada
- Os cards são exibidos na ordem configurada
- Cada card é totalmente clicável
- O link direciona o usuário para a URL configurada
- O layout se adapta automaticamente para desktop e mobile
- O estilo pode variar conforme a **Classe da Marca**

## Boas práticas

- Utilize imagens padronizadas entre os cards
- Evite textos longos nos títulos
- Use subtítulos com benefícios claros
- Verifique sempre se os links estão ativos
- Mantenha coerência visual entre campanhas
- Revise o comportamento em mobile antes de publicar

## Observações finais

- O componente é ideal para destacar categorias, coleções ou campanhas
- Não requer configuração técnica adicional
- Toda a gestão é feita diretamente pelo Site Editor
