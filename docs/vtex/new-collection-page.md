# Página de coleção

## Visão geral

As páginas de coleção permitem criar páginas customizadas para exibir grupos específicos de produtos na loja. Essas páginas são ideais para campanhas sazonais, promoções especiais, lançamentos ou qualquer agrupamento estratégico de produtos que não se enquadre na estrutura padrão de categorias.

## Onde encontrar

Disponível no **Admin VTEX**, na seção de gerenciamento de páginas.

Caminho geral:

- Admin VTEX → Storefront → Páginas

## Passo a passo

Para criar uma página de coleção nova dentro da loja, basta seguir os seguintes passos:

### 1. Criar página

Clique no botão **"Criar página"** na interface de gerenciamento de páginas.

![image](../assets/criar-pagina.png)

### 2. Configurar campos da nova página

Preencha os campos conforme descrito abaixo:

#### Título

Título da página para SEO. Este texto aparecerá na aba do navegador e nos resultados de busca.

**Exemplo:** `Ofertas Especiais Arno | Descontos Exclusivos`

#### URL

URL da página nova. Deve seguir o padrão de coleções da loja.

**Formato:** `/colecao/[nome-da-colecao]`

**Exemplos:**

- `/colecao/oferta`
- `/colecao/black-friday`
- `/colecao/lancamentos`
- `/colecao/mais-vendidos`

**Observações:**

- Use apenas letras minúsculas
- Utilize hífens (-) para separar palavras
- Evite caracteres especiais e acentuação

#### Requer autenticação

Define se a página será bloqueada por login.

**Opções:**

- **Não:** A página é pública e acessível a todos os visitantes (recomendado para páginas de coleção)
- **Sim:** Apenas usuários logados podem acessar a página

#### Descrição

Descrição meta para SEO. Este texto aparece nos resultados de busca do Google e outros buscadores.

**Boas práticas:**

- Limite de 150-160 caracteres
- Descreva claramente o conteúdo da página
- Inclua palavras-chave relevantes

**Exemplo:** `Descubra as melhores ofertas Arno com descontos especiais em produtos selecionados. Aproveite preços exclusivos no site oficial.`

#### Palavras-chave

Palavras-chave para SEO (meta keywords). Separe por vírgulas.

**Exemplo:** `ofertas arno, promoção, descontos, produtos arno`

**Observação:** Embora este campo tenha impacto limitado em SEO moderno, ainda é útil para organização interna.

#### Metatag robots

Configurações de indexação para mecanismos de busca.

**Opções comuns:**

- **index, follow:** Permite indexação e rastreamento de links (padrão recomendado)
- **noindex, nofollow:** Impede indexação e rastreamento
- **index, nofollow:** Indexa a página mas não segue os links

**Recomendação:** Use `index, follow` para páginas de coleção públicas.

#### Templates

O template que deve ser usado para páginas de coleção.

![image](../assets/template-colecao.png)

**Observação:** Este template contém toda a estrutura necessária para exibir produtos em formato de vitrine com filtros e ordenação.

#### Condicional

Template condicional não é necessário para criar uma nova página de coleção de produtos.

Deixe este campo vazio ou com a configuração padrão.

### 3. Salvar e publicar

Após preencher todos os campos, clique em **"Salvar"** para criar a página.

## Próximos passos

Após criar a página de coleção, você precisará:

1. **Configurar a coleção no Catalog:** Defina quais produtos aparecerão na página através de regras de coleção no Admin VTEX → Catalog → Coleções

2. **Customizar no Site Editor:** Personalize banners, textos SEO e outros componentes através do Site Editor (Admin VTEX → CMS → Site Editor). Para mais detalhes, visualizar: [Coleção de produtos](./../site-editor/search/collection.md)

3. **Testar a página:** Acesse a URL criada para verificar se tudo está funcionando corretamente

## Boas práticas

- **URLs descritivas:** Escolha URLs que descrevam claramente o conteúdo da coleção
- **SEO otimizado:** Preencha todos os campos de SEO com informações relevantes e únicas
- **Teste em mobile:** Verifique como a página aparece em dispositivos móveis

## Observações finais

- Lembre-se de configurar a coleção de produtos no módulo Catalog para que os produtos apareçam na página
- Alterações nas configurações de SEO podem levar alguns dias para serem refletidas nos buscadores
