# Ofertas Relâmpago

## Nome do componente

```text
Ofertas Relâmpago
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas páginas que utilizam a vitrine de ofertas relâmpago.

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Visão geral

O componente **Ofertas Relâmpago** permite exibir uma vitrine especial de produtos com tempo limitado, controlando:

- Exibição ou não da sessão
- Redirecionamento por âncora
- Timer com ou sem dias
- Exibição de apenas um produto por vez
- Coleção de produtos vinculada
- Banner visual da vitrine
- Datas individuais de início e fim por produto

## Campos do componente

### Mostrar sessão de ofertas relâmpago?

Ativa ou desativa completamente a exibição da sessão no front-end.

- **Ligado** → a vitrine aparece no site
- **Desligado** → a vitrine não é renderizada

### ID da Sessão para redirecionamento

Define o identificador (âncora) usado para redirecionar o usuário diretamente para a seção de ofertas.

Exemplo:

```text
flash-sales
```

Isso permite links como:

```text
/seu-path#flash-sales
```

### Mostrar dias no timer?

Controla se o contador exibirá também **dias**, além de horas, minutos e segundos.

- Ligado → mostra dias no contador
- Desligado → mostra apenas horas, minutos e segundos

### Mostrar apenas um produto de vez?

Quando ativado, apenas **um produto por vez** será exibido na vitrine, mesmo que a coleção possua vários itens válidos.

### ID da Coleção de Produtos

Informe o **ID da coleção VTEX** que contém os produtos participantes da oferta relâmpago.

Exemplo:

```text
393
```

A vitrine irá buscar automaticamente os produtos dessa coleção.

### Título da Coleção de Produtos

Título exibido acima da vitrine.

Exemplo:

```text
CORRA! OFERTAS RELÂMPAGO
```

Esse texto é totalmente editável e pode ser usado para chamadas promocionais.

### Descrição da Vitrine

Texto complementar exibido abaixo do título. Só é renderizada se existir um banner configurado para a Vitrine.

Exemplo:

```text
Aproveite as ofertas relâmpago por tempo limitado.
```

### Banner da Vitrine

Imagem usada como identidade visual da sessão de ofertas relâmpago.

Recomendações:

- Usar imagem leve e otimizada para web
- Preferir fundo transparente ou cor sólida
- Usar textos legíveis
- Manter proporção consistente entre campanhas

Esse banner aparece junto ao título da vitrine.

## Datas Inicial e Final de cada Produto

Essa seção permite configurar **individualmente o período de validade da oferta para cada produto**.

### Adicionar item

Clique em **“+ Adicionar”** para criar uma nova configuração.

Cada item possui os seguintes campos:

### ID do Produto

ID numérico do produto na VTEX.

Exemplo:

```text
605
```

### Data inicial da promoção

Define a data e hora em que a oferta começa a valer.

Formato:

```text
DD/MM/AAAA HH:mm
```

Exemplo:

```text
29/12/2025 00:00
```

### Data final da promoção

Define a data e hora em que a oferta deixa de valer.

Formato:

```text
DD/MM/AAAA HH:mm
```

Exemplo:

```text
29/12/2025 23:59
```

### Aplicar

Após preencher os dados do produto, clique em **APLICAR** para salvar a configuração.

O item passará a aparecer na lista de produtos configurados.

## Comportamento do componente

- Apenas produtos dentro do período configurado são exibidos
- O timer respeita a data final definida por produto
- Produtos fora do período não aparecem na vitrine
- Caso vários produtos estejam ativos:
    - podem aparecer todos, ou
    - apenas um por vez (dependendo da configuração)
- O contador é atualizado automaticamente
- O banner e os textos são exibidos acima da vitrine, se forem múltiplos produtos, e ao lado, caso for apenas um

## Boas práticas

- Sempre valide as datas antes de publicar
- Use coleções exclusivas para ofertas relâmpago
- Utilize banners leves para melhor performance

## Observações finais

- O componente depende diretamente da configuração correta da coleção
- Datas inválidas impedem a exibição do produto
- O controle é feito 100% via Site Editor, sem necessidade de código
