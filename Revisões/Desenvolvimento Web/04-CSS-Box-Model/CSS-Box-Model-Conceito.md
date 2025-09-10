#css #box-model #dimensoes #espacamento

## Conceito
- **Todo elemento no CSS é tratado como uma caixa**
- Determina:
  - Características **dimensionais, visuais e de posicionamento** dos elementos HTML
  - O **relacionamento entre as caixas** e dentro da própria caixa

## Estrutura do Box Model

```
┌─────────────────────────────────────┐
│             MARGIN                  │
│  ┌─────────────────────────────────┐│
│  │           BORDER                ││
│  │  ┌─────────────────────────────┐││
│  │  │         PADDING             │││
│  │  │  ┌─────────────────────────┐│││
│  │  │  │       CONTENT           ││││
│  │  │  │     (width x height)    ││││
│  │  │  └─────────────────────────┘│││
│  │  └─────────────────────────────┘││
│  └─────────────────────────────────┘│
└─────────────────────────────────────┘
```

## Componentes (de dentro para fora)

### 1. Content (Conteúdo)
- Área onde aparece o conteúdo (texto, imagens)
- Definida por `width` e `height`

### 2. Padding (Espaçamento Interno)
- Espaço entre o conteúdo e a borda
- Transparente
- Herda cor de fundo do elemento

### 3. Border (Borda)
- Contorna o padding e o conteúdo
- Pode ter cor, estilo e espessura

### 4. Margin (Espaçamento Externo)
- Espaço entre a borda e outros elementos
- Sempre transparente

## Comportamentos por Tipo de Elemento

### Block-level
- **Margens verticais se sobrepõem** (margin collapse)
- Ocupam toda largura disponível
- Respeitam width e height

### Inline-level
- **Margens verticais não existem**
- **Margens horizontais se somam**
- **Não possuem largura e altura** (width/height ignorados)

### Anonymous
- **Não podem ser acessados via CSS**
- Conteúdo fora de elementos HTML

## Exemplo Prático
```css
.caixa {
    width: 200px;          /* Largura do conteúdo */
    height: 100px;         /* Altura do conteúdo */
    padding: 20px;         /* Espaçamento interno */
    border: 5px solid red; /* Borda */
    margin: 10px;          /* Espaçamento externo */
}
```

**Largura total:** 200px (content) + 40px (padding) + 10px (border) + 20px (margin) = **270px**

## Links Relacionados
- [[CSS-Box-Sizing]]
- [[CSS-Display-Visibility]]
- [[CSS-Propriedades-Basicas]]
