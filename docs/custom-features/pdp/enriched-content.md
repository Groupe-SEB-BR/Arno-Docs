# Enriched Content

Este componente permite a exibição de conteúdo enriquecido personalizado na página de produto, extraindo HTML e scripts de uma propriedade específica do produto.

![image](../../assets/conteudo-enriquecido.png)

## Uso

react/EnrichedContent.js

```javascript
import EnrichedContent from './components/PDP/EnrichedContent';

export default EnrichedContent;
```

store/interfaces.json

```json
"arno-enriched-content": {
  "component": "EnrichedContent",
  "composition": "children"
},
```

## Exemplos

```json
"flex-layout.col#pdp-description": {
  "children": [
    "arno-enriched-content"
  ],
  "props": {
    "blockClass": "pdp-description"
  }
},
"arno-enriched-content": {
  "children": ["rich-text#pdp-description", "product-description"]
},
```

## Funcionalidades

### Extração de Conteúdo

- Busca propriedade "Conteudo Enriquecido" do produto
- Extrai HTML e scripts separadamente
- Renderiza HTML com `dangerouslySetInnerHTML`
- Injeta scripts dinamicamente no documento

### Renderização Condicional

- Verifica disponibilidade do DOM
- Exibe conteúdo enriquecido se disponível
- Fallback para `children` quando não há conteúdo enriquecido
- Controle de renderização para evitar hidratação SSR

### Gerenciamento de Scripts

- Cria elementos `<script>` dinamicamente
- Adiciona scripts ao body do documento
- Remove scripts ao desmontar componente
- Suporte para múltiplos scripts

## Comportamento

### Fluxo de Carregamento

1. Verifica se há propriedade "Conteudo Enriquecido" no produto
2. Extrai HTML removendo tags `<script>`
3. Extrai conteúdo dos scripts separadamente
4. Define estados para renderização
5. Aguarda disponibilidade do DOM
6. Renderiza conteúdo apropriado

### Fluxo de Scripts

1. Scripts são extraídos via regex
2. Elementos `<script>` são criados dinamicamente
3. Scripts são adicionados ao body
4. Cleanup remove scripts ao desmontar

## Dependências

- `react`: Hooks `useEffect`, `useState`
- `vtex.product-context`: Hook `useProduct` para acesso aos dados do produto
- `vtex.render-runtime`: Função `canUseDOM` para verificação de ambiente

## Estados Gerenciados

- `description`: Conteúdo HTML sem scripts
- `scripts`: Array de scripts extraídos
- `enriched`: Flag indicando se há conteúdo enriquecido
- `render`: Flag de controle de renderização

## Propriedade do Produto

### Nome da Propriedade

```text
Conteudo Enriquecido
```

## Funções Auxiliares

### extractHTML

Remove todas as tags `<script>` do conteúdo para renderização segura do HTML.

```javascript
function extractHTML(content) {
  return content.replace(/<script.*?>.*?<\/script>/g, '');
}
```

### extractScripts

Extrai o conteúdo interno de todas as tags `<script>` usando regex.

```javascript
function extractScripts(content) {
  const scriptRegex = /<script.*?>([\s\S]*?)<\/script>/g;
  let scripts = [];
  let match;
  while ((match = scriptRegex.exec(content)) !== null) {
    scripts.push(match[1]);
  }
  return scripts;
}
```

## Observações

1. Scripts são injetados diretamente no DOM
2. Renderização é controlada para evitar problemas de SSR
3. Fallback automático para `children` quando não há conteúdo enriquecido
4. Scripts são removidos ao desmontar componente
5. Usa `dangerouslySetInnerHTML` - validar conteúdo antes de usar
6. Suporta múltiplos scripts no mesmo conteúdo
7. HTML e scripts são processados separadamente
8. Componente aguarda disponibilidade do DOM antes de renderizar
