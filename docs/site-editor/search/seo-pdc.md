# SEO

## Nome do componente

```text
Ativar/Desativar texto SEO
└── SEO text - Container
  └── Componente ver mais
    └── SEO text - Search
```

## Onde encontrar

Disponível no **Site Editor (VTEX)** nas páginas de departamento, categoria, busca e coleções.

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Visão geral

O componente **SEO** permite criar uma seção composta por **cards promocionais**, normalmente usados para destacar categorias, linhas de produto ou campanhas específicas.

Cada card possui imagem, título, subtítulo e link, funcionando como um atalho visual para páginas estratégicas.

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

### Texto

Texto em markdown com o conteúdo SEO que será aplicado à página.

Exemplo:

```text
### **Ofertas Arno: os maiores descontos do site oficial**

Nesta página você encontra as **melhores ofertas Arno**, com os maiores percentuais de desconto ativos no site oficial. Os produtos listados mudam conforme o estoque e as promoções vigentes, garantindo sempre preços atualizados e oportunidades reais. 

Aqui estão os itens com os melhores descontos. Assim, você pode encontrar rapidamente  **descontos** em várias categorias, sem precisar procurar cupons ou códigos externos..
```

## Comportamento do componente

- A seção só aparece se houver conteúdo preenchido no campo **Texto**
- O texto é renderizado em markdown e exibido na página
- O conteúdo pode ser versionado e agendado
- É possível aplicar o mesmo texto para múltiplas páginas usando a opção de template
- O layout se adapta automaticamente para desktop e mobile

## Boas práticas

- Utilize markdown para estruturar o conteúdo (títulos, listas, negrito, etc.)
- Mantenha o texto focado em SEO e informações relevantes para o usuário
- Use palavras-chave estratégicas relacionadas à página
- Revise o conteúdo antes de ativar versões
- Aproveite o versionamento para campanhas sazonais
- Verifique o comportamento em mobile antes de publicar

## Observações finais

- O componente é ideal para adicionar conteúdo SEO em páginas de busca, categoria e coleções
- Suporta versionamento e agendamento de conteúdo
- Toda a gestão é feita diretamente pelo Site Editor
- Não requer configuração técnica adicional
