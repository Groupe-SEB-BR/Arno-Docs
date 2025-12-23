# Pixel APP para rastreio de eventos na VTEX

## Visão Geral

Este módulo lida com vários eventos relacionados às interações do usuário na plataforma de e-commerce VTEX. Ele escuta mensagens específicas e aciona ações correspondentes, como rastreamento de visualizações de página, impressões de produtos e interações do usuário com conteúdo promocional.

## Repositório

[![GitHub](https://img.shields.io/badge/GitHub-Repo-blue?style=flat&logo=github)](https://github.com/enext-dev/arno-tagcommander)

## Funções

### handleEvents

Manipula eventos recebidos e executa ações correspondentes com base no tipo de evento.

#### Tipos de Eventos Tratados

- **vtex:pageView**: Rastreia visualizações de página e configura scripts e variáveis necessárias.
- **vtex:pageInfo**: Atualiza variáveis de rastreamento com base nas informações da página.
- **vtex:userData**: Busca dados do usuário e atualiza variáveis de rastreamento conforme necessário.
- **vtex:orderPlaced**: Rastreia eventos de colocação de pedidos e envia dados relevantes para análise.
- **vtex:productView**: Rastreia eventos de visualização de produtos e atualiza variáveis de rastreamento.
- **vtex:productClick**: Rastreia eventos de clique em produtos e envia dados para análise.
- **vtex:promoView**: Rastreia visualizações promocionais.
- **vtex:promotionClick**: Rastreia cliques em promoções.
- **vtex:productImpression**: Rastreia impressões de produtos.
- **vtex:addToCart**: Rastreia itens adicionados ao carrinho.
- **vtex:removeFromCart**: Rastreia itens removidos do carrinho.

## TagCommander

TagCommander é uma plataforma de gerenciamento de tags que permite a coleta e o rastreamento de dados de eventos em lojas online.

### Propriedades do TagCommander

O TagCommander utiliza várias propriedades no objeto `window` para gerenciar dados e funcionalidades de rastreamento. Abaixo estão as principais propriedades e suas descrições:

- **tc_vars**: Um objeto que contém variáveis específicas do TagCommander, utilizadas para configuração e personalização de rastreamento.
- **tc_functions**: Um objeto que armazena funções que podem ser chamadas para executar ações específicas relacionadas ao TagCommander.
- **tc_scripts**: Um objeto que contém scripts que são carregados dinamicamente para rastreamento de eventos.
- **tc_settings_vars**: Um objeto que armazena variáveis de configuração do TagCommander, permitindo ajustes nas definições de rastreamento.
- **tC**: Um objeto que fornece acesso à API do TagCommander, permitindo interações programáticas com a plataforma.

### Outras propriedades

- **dataLayer**: Um array que armazena dados de eventos e variáveis que podem ser utilizados para rastreamento e análise.
- **jsonldList**: Um array que contém dados estruturados em formato JSON-LD, utilizados para SEO e rastreamento.
- **gtag_report_conversion**: Uma função que reporta conversões para o Google Analytics.
- **gtag**: A função principal do Google Analytics para enviar dados de rastreamento.
- **fbq**: A função do Facebook para rastreamento de eventos e conversões.
- **ttq**: A função do TikTok para rastreamento de eventos.
- **_dAutomationGtmAddTimer**: Uma função interna para adicionar temporizadores no Google Tag Manager.
- **_dAutomationGtmCloseTimer**: Uma função interna para fechar temporizadores no Google Tag Manager.

### Exemplos

```typescript
newsletterButton?.addEventListener('click', () => {
  window.tC.event.newsletterSubscription(this, {
    position: 'Home',
  })
  console.log('clicked button -> ', newsletterButton)
})
```

## Funções Utilitárias

- **normalizeReferenceId**: Normaliza IDs de referência de produtos removendo prefixos específicos.
- **removeStartAndEndSlash**: Limpa strings de categoria removendo barras iniciais e finais.
- **getSeller**: Recupera o vendedor padrão de uma lista de vendedores.
- **formatPrice**: Formata valores de preço para duas casas decimais.

## Dependências

- `canUseDOM`: Uma utilidade do `vtex.render-runtime` para verificar se o DOM está disponível.

## Uso

Para usar este módulo, certifique-se de que ele esteja incluído no contexto apropriado onde os eventos do VTEX são despachados. O ouvinte de eventos é adicionado ao objeto window para capturar mensagens enviadas pela plataforma VTEX.

## Notas

- Certifique-se de que o `site_id` esteja configurado nas configurações do administrador para evitar erros.
- O módulo inclui vários scripts de rastreamento que são carregados dinamicamente com base no tipo de evento.
