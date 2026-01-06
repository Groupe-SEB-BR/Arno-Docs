# Coleção de produtos

## Nome do componente

```text
Coleção
```

## Onde encontrar

Disponível no **Site Editor (VTEX)** nas páginas de coleções.

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Visão geral

O componente **Coleção** permite configurar qual coleção de produtos será usada naquela página.

## Campos do componente

### Versões

É possível criar uma versão nova do conteúdo em vez de sobrescrever o texto atual. Ao clicar em `NOVA VERSÃO`, basta inserir o novo conteúdo e definir os seguintes campos:

- Ativar agora
- Definir uma data de início
- Definir uma data de término

Aplicar para

- esta URL
- este template `(usar essa opção caso for o mesmo texto para todas as categorias)`

É possível gerenciar todas as versões criadas e ativar e desativar o conteúdo dependendo da necessidade de campanhas diferentes, etc.

## Configurações do componente

### Número máximo de itens por página

Define quantos produtos serão exibidos por página na coleção.

**Valor padrão:** 12

### Query

Identificador da coleção que será exibida.

**Exemplo:** 145

### Map

Define o tipo de busca utilizado para a coleção.

**Valor:** `productClusterIds`

### PriceRange

Filtra produtos por faixa de preço.

**Formato:** "valor_minimo TO valor_maximo"  
**Exemplo:** "10 TO 233"

### Order by field

Campo utilizado para ordenação dos produtos na coleção.

**Opções disponíveis:**

- Relevância
- Preço (menor para maior)
- Preço (maior para menor)
- Nome (A-Z)
- Nome (Z-A)
- Data de lançamento

### Ocultar itens indisponíveis

Quando ativado, produtos sem estoque não serão exibidos na coleção.

### Filtro de SKUs

Permite aplicar filtros específicos para SKUs na coleção.

**Valor padrão:** Nenhum

### Comportamento de simulação

Define como o sistema simula preços e disponibilidade.

**Valor padrão:** Padrão

### Parcelamento

Configuração de exibição das opções de parcelamento.

**Valor padrão:** Máximo sem juros

## Observações finais

- O componente permite personalizar completamente a exibição de coleções
- Todas as configurações são aplicadas em tempo real no Site Editor
- É possível combinar múltiplos filtros para segmentações específicas
- O comportamento de simulação afeta como preços e disponibilidade são calculados
- Não requer configuração técnica adicional no código
