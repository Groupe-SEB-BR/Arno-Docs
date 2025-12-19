# Home Tabs

Este componente exibe uma vitrine multibranding com abas interativas na página inicial, alternando automaticamente entre diferentes marcas com animação de progresso.

![image](../../assets/home-tabs.png)

## Uso

react/HomeTabs.tsx

```jsx
import HomeTabs from './components/HomeTabs';

export default HomeTabs;
```

store/interfaces.json

```json
"custom-arno-home-tabs": {
  "component": "HomeTabs"
},
```

## Exemplos

```jsx
"store.home": {
  "children": ["home-tabs"]
}
```

## Funcionalidades

### Sistema de Abas com Rotação Automática

O componente alterna automaticamente entre as abas a cada 5 segundos, com barra de progresso visual:

- **Rotação Automática**: Transição suave entre abas com duração de 5000ms
- **Barra de Progresso**: Indicador visual animado que mostra o tempo até a próxima aba
- **Cor Personalizada**: Cada aba pode ter sua própria cor de destaque
- **Navegação Manual**: Clique nas abas para alternar imediatamente

### Controles de Interação

- **Mouse Hover**: Pausa a rotação automática ao passar o mouse sobre o conteúdo
- **Touch Events**: Pausa a rotação em dispositivos móveis ao tocar no conteúdo
- **Retomada Automática**: Volta a rotacionar ao remover o mouse/toque

### Banners de Conteúdo

Cada aba pode conter múltiplos banners com:

- **Imagem de Fundo**: Imagem principal do banner
- **Título e Descrição**: Textos informativos
- **Acentos Visuais**: Imagens decorativas (esquerda e direita)
- **Link de Ação**: Botão customizável para redirecionamento

## Estados Gerenciados

O componente utiliza os seguintes estados:

- `activeTab`: Índice da aba ativa atual
- `isPaused`: Controla se a rotação automática está pausada
- `progress`: Percentual de progresso da barra (0-100)
- `tabItemRef`: Referência ao container do conteúdo
- `startTimeRef`: Timestamp de início da animação
- `animationFrameRef`: ID do frame de animação

## Responsividade

### Desktop

- Exibe todos os banners lado a lado em grid
- Controle de hover para pausar rotação

### Mobile

- Utiliza carrossel `react-slick` para navegação entre banners
- Um banner por vez com dots de navegação
- Touch events para pausar rotação

## Configuração via Schema

### Propriedades Principais

```typescript
{
  shouldRender: boolean,  // Controla exibição do componente
  tabs: Array<{
    id: string,           // Identificador único da aba
    title: string,        // Título exibido na aba
    color: string,        // Cor da barra de progresso (hex)
    content: Array<{
      title: string,                // Título do banner
      description: string,          // Descrição do banner
      href: string,                 // URL de destino
      label: string,                // Texto do botão
      image: string,                // URL da imagem de fundo
      imageAccentLeft: string,      // URL acento esquerdo
      imageAccentRight: string      // URL acento direito
    }>
  }>
}
```

## Animação de Progresso

Utiliza `requestAnimationFrame` para animação suave:

1. Calcula tempo decorrido desde o início
2. Atualiza progresso proporcionalmente
3. Ao atingir 100%, avança para próxima aba
4. Reseta progresso e reinicia ciclo

## Dependências

- `react-slick`: Carrossel mobile
- `vtex.device-detector`: Detecção de dispositivo
- `classnames`: Gerenciamento de classes CSS

## Estrutura de Classes CSS

- `.HomeTabs`: Container principal
- `.HomeTabsHeader`: Container das abas
- `.HomeTab`: Botão de aba individual
- `.HomeTabsBar`: Container da barra de progresso
- `.HomeTabsBarFill`: Barra de progresso animada
- `.TabItems`: Container do conteúdo
- `.BannerItem`: Item de banner individual

## Observações

1. Requer configuração via Site Editor para personalização
2. Suporta de 2 a 3 abas simultaneamente
3. Classes CSS dinâmicas baseadas no número de abas
4. Limpeza automática de animations frames ao desmontar componente
5. Progress bar com cor dinâmica baseada na aba ativa
