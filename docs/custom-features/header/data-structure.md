# Data Structure

Este componente injeta dados estruturados (JSON-LD) no `<head>` da página de forma condicional, baseado no caminho da URL atual, para melhorar SEO e visibilidade em mecanismos de busca.

## Uso

react/DataStructure.tsx

```jsx
import DataStructure from './components/DataStructure';

export default DataStructure;
```

store/interfaces.json

```json
"custom-arno-data-structure": {
  "component": "DataStructure"
}
```

## Exemplos

```jsx
"store.home": {
  "children": ["custom-arno-data-structure"]
}
```

## Funcionalidades

### Injeção Condicional de JSON-LD

O componente injeta scripts de dados estruturados apenas quando:

- A URL atual corresponde a um `pathname` configurado
- Existe um script JSON-LD válido configurado para aquela rota

### Correspondência de Rotas

- **Normalização de Paths**: Remove barras finais para comparação
- **Correspondência Exata**: Compara o `canonicalPath` atual com os paths configurados
- **Atualização Dinâmica**: Reage a mudanças de rota automaticamente

### Parsing Seguro de JSON

- Aceita strings JSON ou objetos JavaScript
- Tratamento de erros para JSON inválido
- Retorna `null` em caso de parsing falho

## Estrutura de Dados

### Propriedades do Componente

```javascript
{
  items: Array<{
    pathname: string,     // Caminho da URL (ex: "/produtos")
    script: string | object  // JSON-LD como string ou objeto
  }>
}
```

### Exemplo de Item

```json
{
  "pathname": "/produtos",
  "script": "{\"@context\":\"https://schema.org\",\"@type\":\"Product\",\"name\":\"Produto Exemplo\"}"
}
```

## Comportamento

### Renderização Condicional

O componente não renderiza script se:

- Array `items` estiver vazio ou undefined
- Nenhum item corresponder à rota atual
- Script não for um JSON válido

### Fluxo de Execução

1. Obtém o `canonicalPath` da rota atual
2. Busca item com `pathname` correspondente
3. Faz parse do script JSON-LD
4. Injeta no `<head>` via `react-helmet`

## Configuração via Schema

### Propriedades Principais

```javascript
{
  items: {
    type: 'array',
    items: {
      pathname: {
        type: 'string',
        title: 'Path Name*',
        description: 'Caminho da URL onde os dados estruturados serão aplicados'
      },
      script: {
        type: 'string',
        title: 'Objeto JSON-LD*',
        description: 'Insira o objeto JSON-LD que contém os dados estruturados',
        default: '{}'
      }
    }
  }
}
```

## Dependências

- `react-helmet`: Manipulação do `<head>` da página
- `vtex.render-runtime`: Acesso à informações de rota

## Observações

1. Requer configuração via Site Editor
2. Paths são normalizados (barras finais removidas)
3. Suporta múltiplas configurações de rota
4. JSON-LD deve seguir especificações do Schema.org
5. Scripts inválidos são ignorados silenciosamente
6. Útil para diferentes tipos de Schema (Product, BreadcrumbList, Organization, etc.)
