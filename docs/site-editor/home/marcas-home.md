# Marcas Home

## Nome do componente

```text
Marcas Home
└── Título
  └── Marcas Goupe SEB
    └── Layout do Slider
```

## Onde encontrar

Disponível no **Site Editor (VTEX)**, nas homes da loja (Arno, Rochedo e Tefal).

Caminho geral:

- Admin VTEX → CMS → Site Editor

## Visão geral

O componente **Marcas Home** permite criar uma seção composta por um **slide de imagens**, normalmente usados para destacar as marcas disponíveis dentro da loja.

Cada sessão possui imagem e link de redirecionamento.

## Campos do componente

### Info cards dentro da lista

### Imagem como fundo

Define se a imagem será utilizada como **background** do card.

- **Ligado** → imagem ocupa o fundo do card
- **Desligado** → imagem aparece como elemento separado

Impacta diretamente na leitura do texto e no layout.

### Modo de texto

Define o formato do conteúdo textual.

Exemplo:

```text
HTML
```

Quando em HTML, permite uso de tags para estilização e quebra de linha.

### Título

Texto de destaque do card.

- Aparece em maior hierarquia visual
- Normalmente usado para nome da marca ou campanha

### Subtítulo

Texto exibido logo abaixo do título.

Usado para complementar a mensagem principal.

### Corpo do texto

Texto adicional exibido abaixo do subtítulo, dentro do componente.

Ideal para descrições curtas ou mensagens institucionais.

### Call to Action (CTA)

#### Modo do call to action

Define se o card terá um CTA.

Exemplo:

```text
Nenhum
```

Outros modos podem habilitar botão ou link.

#### Texto do call to action

Texto exibido no CTA.

Exemplo:

```text
Saiba mais
```

#### URL do call to action

URL de redirecionamento quando o CTA é clicado.

Pode ser um link interno ou externo.

#### Tipo de redirecionamento do link de call to action

Define como o link será aberto.

Exemplo:

- O link é aberto na mesma aba
- O link é aberto em nova aba

### Imagens

#### Imagem

Imagem principal do card (desktop).

Recomendações:

- Usar imagens otimizadas para web
- Garantir boa legibilidade do texto sobre a imagem
- Manter padrão visual entre os cards

#### Imagem para dispositivos móveis

Imagem específica para mobile.

Recomendada para melhor enquadramento em telas menores.

#### URL de ação da imagem

Define um link para tornar a imagem clicável.

Exemplo:

```text
/rochedo
```

Ao clicar na imagem, o usuário será redirecionado para essa URL.

### Layout e estilo

#### Posição do texto

Define onde o texto aparece dentro do card.

Exemplo:

```text
Centralizado
```

#### Alinhamento de texto

Controla o alinhamento horizontal do texto.

Exemplo:

```text
Centralizado
```

#### Classe de bloco CSS

Permite adicionar uma classe CSS customizada ao componente.

Exemplo:

```text
home-brands
```

Usado para:

- Customizações visuais
- Ajustes específicos por contexto
- Diferenciação entre seções

### Aplicar

Após preencher os campos do card, clique em **APLICAR** para salvar.

## Boas práticas

- Utilize imagens padronizadas entre os cards
- Verifique sempre se os links estão ativos
- Revise o comportamento em mobile antes de publicar

## Observações finais

- A gestão do conteúdo é feita diretamente pelo Site Editor
