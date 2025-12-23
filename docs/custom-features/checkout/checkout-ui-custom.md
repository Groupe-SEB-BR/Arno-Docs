# Documentação de Funções - Script Checkout VTEX

## 1. Funções de Detecção de Página

Funções que verificam em qual etapa do checkout o usuário está.

### `isCartPage()`

**Descrição:** Verifica se o usuário está na página do carrinho


**Retorno:** `boolean` - true se estiver na página do carrinho


**Uso:** Detecta pela presença de "cart" no hash da URL

### `isEmailPage()`

**Descrição:** Verifica se o usuário está na página de email

**Retorno:** `boolean` - true se estiver na página de email

**Uso:** Detecta pela presença de "email" no hash da URL

### `isProfilePage()`

**Descrição:** Verifica se o usuário está na página de perfil

**Retorno:** `boolean` - true se estiver na página de perfil

**Uso:** Detecta pela presença de "profile" no hash da URL

### `isShippingPage()`

**Descrição:** Verifica se o usuário está na página de entrega

**Retorno:** `boolean` - true se estiver na página de shipping

**Uso:** Detecta pela presença de "shipping" no hash da URL

### `isPaymentPage()`

**Descrição:** Verifica se o usuário está na página de pagamento

**Retorno:** `boolean` - true se estiver na página de payment

**Uso:** Detecta pela presença de "payment" no hash da URL

### `isOrderPlacedPage()`

**Descrição:** Verifica se o usuário está na página de pedido confirmado

**Retorno:** `boolean` - true se estiver na página orderPlaced

**Uso:** Detecta pelo pathname da URL

## 2. Funções de Configuração de Página

Funções que aplicam classes CSS e modificam comportamentos específicos por página.

### `setCartPage(total)`

**Descrição:** Configura a página do carrinho

**Parâmetros:** `total` - número de itens no carrinho
**Ações:**

- Adiciona classe `x-cart-page` ao body
- Esconde links do carrinho se estiver vazio
- Remove classe se houver itens

### `setEmailPage()`

**Descrição:** Configura a página de email

**Ações:** Adiciona/remove classe `x-email-page` do body

### `setProfilePage()`

**Descrição:** Configura a página de perfil

**Ações:**

- Adiciona/remove classe `x-profile-page` do body
- Modifica texto de newsletter

### `setShippingPage()`

**Descrição:** Configura a página de entrega

**Ações:** Adiciona/remove classe `x-shipping-page` do body

### `setPaymentPage()`

**Descrição:** Configura a página de pagamento

**Ações:**

- Adiciona/remove classe `x-payment-page` do body
- Simula clique no método de pagamento cartão de crédito

### `setOrderPlacedPage()`

**Descrição:** Configura a página de pedido confirmado

**Ações:** Adiciona/remove classe `x-orderPlaced-page` do body

## 3. Funções de Integração AWIN

Gerencia dados de afiliados (AWIN) no checkout.

### `updateOrderFormCustomData(orderFormId, sessionData)`

**Descrição:** Atualiza dados customizados do orderForm com informações AWIN

**Parâmetros:**

- `orderFormId`: ID do orderForm
- `sessionData`: Objeto com dados da sessão (utm_source, awc)
  **Retorno:** `Promise` com dados atualizados do orderForm
  

### `getSession()`

**Descrição:** Busca dados da sessão do usuário

**Retorno:** `Promise` com dados da sessão


### `syncAwinData()`

**Descrição:** Sincroniza dados AWIN da sessão para o orderForm

**Fluxo:**

1. Obtém orderForm e dados da sessão
2. Extrai awc e utm_source
3. Atualiza customData do orderForm

## 4. Funções de Gerenciamento de Cupons

### `removeCouponIfCollaborator(email)`

**Descrição:** Remove cupom se o usuário for colaborador

**Parâmetros:** `email` - email do usuário
**Fluxo:**

1. Busca usuário na entidade CL
2. Verifica se é colaborador
3. Remove cupom se necessário

### `trackCouponApplied()`

**Descrição:** Rastreia aplicação de cupons via Google Analytics

**Uso:** Detecta mudanças no cupom aplicado e envia evento ao GA

## 5. Funções de Navegação do Checkout

### `checkoutSteps.init()`

**Descrição:** Inicializa indicação visual dos passos do checkout

**Fluxo:**

- Identifica etapa atual pela URL
- Aplica classes CSS `is--active` e `is--complete` nos elementos

### `checkoutSteps.setStepActive(_step, _$checkoutSteps)`

**Descrição:** Marca passo ativo no checkout

**Parâmetros:**

- `_step`: Nome do passo atual
- `_$checkoutSteps`: Elementos jQuery dos passos

## 6. Funções de Atualização do Carrinho

### `updateCart()`

**Descrição:** Monitora atualizações do orderForm

**Uso:** Vincula evento `orderFormUpdated.vtex` e chama `bindStepChange()`

### `bindStepChange()`

**Descrição:** Atualiza estado do carrinho baseado nos itens

**Ações:** Filtra cupons e chama `setCartPage()`

### `showProductCount()`

**Descrição:** Exibe contador dinâmico de itens no carrinho

**Funcionalidade:**

- Adiciona elemento HTML com contador
- Atualiza em tempo real com eventos do orderForm

## 7. Funções de Tracking e Analytics

### `initGtag()`

**Descrição:** Inicializa Google Tag Manager

**Ações:**

- Injeta scripts do GTM
- Configura dataLayer e tags

### `gtag_report_conversion(url)`

**Descrição:** Reporta conversão para Google Ads

**Parâmetros:** `url` - URL de destino (não utilizado)
**Uso:** Envia evento de conversão com transaction_id

### `loadScript()`

**Descrição:** Carrega scripts do TagCommander

**Fluxo:**

1. Chama `initTcVar()`
2. Carrega scripts sequencialmente

### `initTcVar()`

**Descrição:** Inicializa variáveis do TagCommander

**Ações:** Cria objeto `window.tc_vars`

## 8. Funções de Manipulação de Dados

### `updateOrderFormWithUserId(orderFormId, userId)`

**Descrição:** Atualiza orderForm com ID do usuário

**Parâmetros:**

- `orderFormId`: ID do orderForm
- `userId`: ID do usuário
  **Uso:** Armazena ucrID no customData

### `ucrID()`

**Descrição:** Obtém e atualiza ID do usuário no orderForm

**Fluxo:**

1. Busca usuário autenticado
2. Busca ID na entidade UL
3. Atualiza orderForm

### `currencyFormatter(value)`

**Descrição:** Formata valores monetários

**Parâmetros:** `value` - Valor em centavos
**Retorno:** `string` - Valor formatado em BRL


## 9. Funções de Variáveis do TagCommander

### `addedCartProductsVariables()`

**Descrição:** Preenche variáveis com produtos do carrinho

**Uso:** Mapeia itens do orderForm para formato do tc_vars

### `initVariables()`

**Descrição:** Inicializa variáveis base do TagCommander

**Uso:** Define site_id, env, lang, country

### `pageViewTag()`

**Descrição:** Define tipo de página baseado na URL

**Uso:** Mapeia hash da URL para page_type do tc_vars

### `checkDevice()`

**Descrição:** Detecta dispositivo do usuário

**Uso:** Define user_device como 'mobile' ou 'desktop'

### `pageVariables()`

**Descrição:** Atualiza variáveis da página no tc_vars

**Uso:** Preenche dados do carrinho (ID, subtotal, total)

## 10. Funções de Data Layer e Eventos

### `dataLayerTracking()`

**Descrição:** Configura tracking de eventos do checkout

**Eventos tratados:**

- Finalizar compra
- Continuar comprando
- Selecionar frete
- Selecionar método de pagamento
- Confirmar pedido

### `updateDataLayer()`

**Descrição:** Atualiza dataLayer com mudanças no carrinho

**Funcionalidades:**

- Rastreia adição/remoção de itens
- Atualiza cupons e descontos
- Compara estados anteriores e atuais do carrinho

### `updateOrderFormItemsStorage()`

**Descrição:** Salva estado inicial do carrinho no localStorage

**Uso:** Base para comparação em `updateDataLayer()`

## 11. Funções de Segurança e Performance

### `addSecurity()`

**Descrição:** Adiciona política de segurança de conteúdo

**Ações:** Injeta meta tag upgrade-insecure-requests

### `dynamicallyLoadScript(url)`

**Descrição:** Carrega script dinamicamente

**Parâmetros:** `url` - URL do script
**Uso:** Injeta script com async e defer

## 12. Funções de Resumo Personalizado

### `renderCheckoutResumo()`

**Descrição:** Renderiza resumo personalizado do checkout com PIX

**Funcionalidades:**

- Calcula parcelamentos
- Aplica desconto PIX
- Substitui tabela nativa do checkout
- Atualiza em tempo real

### `calculateInstallments(orderForm)`

**Função interna:** Calcula opções de parcelamento

### `getPixDiscountPercent()`

**Função interna:** Busca percentual de desconto PIX do Master Data

### `renderResumo(orderForm)`

**Função interna:** Renderiza HTML do resumo

## 13. Funções Auxiliares

### `showFrete()`

**Descrição:** Simula clique no botão de cálculo de frete

**Uso:** Automatiza cálculo de frete

## 14. Inicialização Principal

As funções são executadas em:

1. `$(document).ready()`: Renderiza resumo
2. `$(window).load()`: Inicializa todos os sistemas
3. `$(window).on('hashchange')`: Atualiza tracking em mudanças de página

## Fluxo de Execução Principal:

1. **Inicialização:** Scripts de analytics, variáveis, segurança
2. **Tracking:** Configura eventos e dataLayer
3. **Integrações:** AWIN, TagCommander, Google Analytics
4. **UI/UX:** Resumo personalizado, steps do checkout, contador de itens
5. **Dados:** Sincronização de IDs, cupons, customData
6. **Monitoramento:** Eventos em tempo real, atualizações do orderForm
