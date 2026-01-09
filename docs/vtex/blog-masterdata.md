# Como alimentar o Blog Arno

## Onde encontrar?

O Master Data da VTEX pode ser acessado através do painel administrativo:

**URL direta**: Masterdata > Applications > BLOG: <https://lojaarno.vtexcrm.com.br/>

**Caminho alternativo**: Admin VTEX > Store Settings > Master Data > Applications

## Como editar os posts no Master Data?

### Edição Individual

1. Acesse a entidade **Blog Post** no Master Data
2. Localize o post a ser editado
3. Clique no ícone de edição (lápis) ao lado do registro
4. Realize as alterações necessárias nos campos
5. Clique em **Salvar** para aplicar as mudanças

**Dica**: Sempre revise a URL do post antes de salvar para evitar links quebrados.

## Como editar os posts no Excel?

### Exportação em massa

1. Acesse a entidade **Blog Post**
2. Clique no botão **Export XLS** no canto superior direito
3. Selecione **todos os campos** da entidade que deseja exportar
4. Insira o **email** onde o arquivo será enviado
5. Aguarde o email com o link de download (pode levar alguns minutos)

### Importação após edição

1. Após editar o arquivo, **salve como .xls** (formato Excel 97-2003)

- Importante: Mesmo que o export tenha vindo como .csv, a importação deve ser feita com .xls

2. Retorne à home no Master Data no botão **Application**
3. Clique em **Import XLS**
4. Faça upload do arquivo editado
5. Aguarde a validação e processamento
6. Verifique os logs para confirmar que não houve erros na importação

**⚠️ Atenções importantes:**

- Não altere o campo **ID** dos registros existentes
- Mantenha o formato das URLs (sem espaços ou caracteres especiais)
- Certifique-se de que os valores de relacionamento (como Brand) existem no Master Data
- Faça backup do arquivo original antes de editar
- Teste as alterações em poucos registros antes de importar em massa

## Validações e boas práticas

### Imagens

- Utilize sempre URLs do File Manager da VTEX
- Garanta que as imagens Desktop e Mobile estejam otimizadas
- Formato recomendado: JPG ou PNG
- Tamanho recomendado: máximo 500KB por imagem

## Entidades no Master Data

### Blog Brand

Configurações para as marcas disponíveis no Blog

**Nome da Brand**: arno

**Url da Brand**: arno

### Blog Post

Configurações para os posts disponíveis no Blog

Exemplo: <https://www.arno.com.br/blog/post/como-deixar-o-ambiente-mais-romantico-para-uma-data-especial>

**URL**: 6-receitas-para-acompanhar-os-jogos-da-copa-do-mundo-feminina  
_URL amigável do post, usada para criar o link da página._

**Título do Post**: 6 receitas para acompanhar os jogos da Copa do Mundo Feminina  
_Título principal exibido na página do post._

**Descrição do Post**:

Conteúdo que será o corpo da publicação, pode conter ou não HTML.

```html
<style>
  .content_blog {
    line-height: 1.6;
    margin: 20px;
    color: #333;
  }
  .content_blog h2 {
    font-size: 1.6em !important;
    color: #e30613 !important;
    padding: 10px 0 !important;
  }
  .content_blog h3 {
    font-size: 1.2em !important;
    color: #000000;
  }
  ul,
  ol {
    margin-left: 20px;
    padding-left: 0;
  }
  li {
    margin-bottom: 5px;
  }
  strong {
    font-style: italic;
    color: #e30613;
  }
  ul {
    list-style-type: disc;
  }
  ol {
    list-style-type: decimal;
  }
</style>
<section class="content_blog">
  <p>
    A Copa do Mundo Feminina está chegando na fase decisiva! Os jogos estão
    definidos e as disputas de mata-mata até a grande final, no dia 20 de
    agosto, se iniciam e prometem grandes emoções.
  </p>
  <p>
    Para deixar a sua Copa do Mundo ainda mais saborosa, montamos uma seleção de
    6 receitas perfeitas para preparar e curtir os melhores jogos da modalidade
    (...)
  </p>
</section>
```

**Imagem Desktop**: <https://lojaarno.vtexassets.com/assets/vtex.file-manager-graphql/images/98e66478-ef64-47f8-aec8-eb550fe52d14___c105dedada0da40d691b4e06c2b9eea1.jpg>  
_Imagem de banner exibida em telas maiores (desktops e tablets)._

**Imagem Mobile**: <https://lojaarno.vtexassets.com/assets/vtex.file-manager-graphql/images/98e66478-ef64-47f8-aec8-eb550fe52d14___c105dedada0da40d691b4e06c2b9eea1.jpg>  
_Imagem de banner otimizada para dispositivos móveis._

**Imagem do Card**: <https://lojaarno.vtexassets.com/assets/vtex.file-manager-graphql/images/98e66478-ef64-47f8-aec8-eb550fe52d14___c105dedada0da40d691b4e06c2b9eea1.jpg>  
_Imagem thumbnail exibida em listagens e cards de preview._

**Usa vídeo como banner?**: No  
_Define se o banner será um vídeo (Yes) ou imagem (No)._

**Link do vídeo**: <https://www.youtube.com/watch?v=Yycz_vKFTgs>  
_URL do vídeo do YouTube caso seja utilizado como banner._

**Resumo do Post**: ---  
_Texto curto para descrição em listagens e compartilhamentos._

**Brand**: arno  
_Marca associada ao post, deve corresponder ao cadastro em Blog Brand._

**Categoria do Post**: receitas práticas e deliciosas  
_Categoria principal do post para organização e navegação._

**Categorias do Post**: refeicoes, lanches, airfryer, copa do mundo, batedeira, air fryer  
_Tags secundárias separadas por vírgula para classificação e filtros._

**Tags do Post**: todos, refeicoes, lanches, airfryer, copa do mundo, batedeira, air fryer  
_Palavras-chave para busca e relacionamento entre posts._

**Filtros do Post**: ---  
_Filtros customizados para segmentação adicional._

**ID da Coleção de Produtos**: 277  
_ID da coleção VTEX que agrupa produtos relacionados ao post._

**Receita - Tempo de Preparo**: ---  
_Tempo estimado para preparar as receitas (ex: 30 minutos)._

**Receita - Complexidade**: ---  
_Nível de dificuldade (Fácil, Médio, Difícil)._

**Receita - Ingredientes**: ---  
_Lista estruturada de ingredientes necessários._

**Receita - Instruções**: ---  
_Passo a passo detalhado do modo de preparo._

**Visualizações**: 40  
_Contador de acessos ao post._

**Titulo do MetaDado**: 6 receitas práticas para curtir a copa do mundo feminina em casa  
_Meta title para SEO, exibido em resultados de busca._

**Descrição do MetaDado**: Descubra 6 receitas deliciosas para acompanhar os jogos da copa do mundo feminina. Torça pelo futebol feminino com petiscos fáceis e cheios de sabor!  
_Meta description para SEO, resumo exibido nos resultados de busca._

### Blog Category

Configurações para as categorias disponíveis no Blog.

Exemplo: <https://www.arno.com.br/blog/categoria/casa-e-cozinha>

**Nome da Categoria**: tecnologia na sua cozinha  
_Nome identificador da categoria no sistema._

**URL da Categoria**: tecnologia-na-cozinha  
_URL amigável para acessar a página da categoria._

**Descrição da Categoria**: A tecnologia na cozinha está revolucionando a forma como preparamos nossas refeições, trazendo mais praticidade, eficiência e inovação ao dia a dia. Se você está em busca de dicas sobre como aproveitar ao máximo a tecnologia moderna na cozinha, este artigo é para você! Vamos compartilhar ideias que incluem eletroportáteis multifuncionais, como mixers, processadores e liquidificadores da Arno, que tornam o preparo de receitas mais rápido e fácil. Além disso, falaremos sobre recursos que facilitam a limpeza e ajudam a manter tudo organizado com menos esforço. Seja para cozinhar pratos elaborados ou simplificar tarefas diárias, a tecnologia é uma aliada indispensável. Continue lendo e descubra como modernizar sua cozinha com soluções inteligentes que unem funcionalidade e design, tornando cada momento mais prático e prazeroso!  
_Texto descritivo completo da categoria, exibido na página de listagem._

**Imagem Desktop**: <https://lojaarno.vtexassets.com/assets/vtex.file-manager-graphql/images/2ae5ed3c-1d30-4578-9bff-96eb0299884f___4002620796bd28d2403c586699f03924.jpg>  
_Imagem de banner da categoria para telas maiores (desktops e tablets)._

**Imagem Mobile**: <https://lojaarno.vtexassets.com/assets/vtex.file-manager-graphql/images/2ae5ed3c-1d30-4578-9bff-96eb0299884f___4002620796bd28d2403c586699f03924.jpg>
_Imagem de banner da categoria otimizada para dispositivos móveis._

**Filtros da Categoria**: ---  
_Filtros customizados aplicáveis à categoria._

**Título do Metadado**: Dicas de tecnologia na cozinha: ideias modernas para o dia a dia  
_Meta title para SEO da categoria, exibido em resultados de busca._

**Descrição do Metadado**: Descubra como a tecnologia moderna pode transformar sua cozinha. Dicas práticas para otimizar tarefas, facilitar a limpeza e inovar no preparo!
_Meta description para SEO da categoria, resumo exibido nos resultados de busca._

**Ordenação da Categoria na Home**: ---  
_Define a posição de exibição da categoria na página inicial._

## Blog Subcategories

Descontinuado
