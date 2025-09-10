#css #display #visibility #layout

## Display

**Controla como o elemento participa no layout**

### Valores Principais

#### `display: block`
- Elemento em **bloco**
- Ocupa toda largura disponível
- Quebra linha antes e depois
- Respeita width, height, margin, padding

#### `display: inline`
- Elemento em **linha**
- Ocupa apenas o espaço necessário
- Não quebra linha
- **Ignora** width, height, margin-top, margin-bottom

#### `display: inline-block`
- **Híbrido** entre block e inline
- Flui com o texto (como inline)
- Respeita dimensões (como block)

#### `display: none`
- **Remove completamente** do layout
- Elemento não ocupa espaço
- Não é renderizado

### Exemplos
```css
.bloco {
    display: block;
    width: 200px;
    height: 100px;
}

.linha {
    display: inline;
    width: 200px;     /* Ignorado */
    height: 100px;    /* Ignorado */
}

.linha-bloco {
    display: inline-block;
    width: 200px;     /* Aplicado */
    height: 100px;    /* Aplicado */
}

.oculto {
    display: none;    /* Remove do layout */
}
```

## Visibility

**Controla a visibilidade sem afetar o layout**

### Valores

#### `visibility: visible`
- Elemento **visível** (padrão)

#### `visibility: hidden`
- Elemento **invisível**
- **Mantém o espaço** ocupado no layout
- Ainda afeta o fluxo do documento

### Exemplo
```css
.invisivel {
    visibility: hidden;  /* Oculta mas mantém espaço */
}
```

## Display vs Visibility - Comparação

| Propriedade | Ocupa Espaço | Afeta Layout | Renderizado |
|-------------|--------------|--------------|-------------|
| `display: none` | ❌ Não | ❌ Não | ❌ Não |
| `visibility: hidden` | ✅ Sim | ✅ Sim | ❌ Não |
| `visibility: visible` | ✅ Sim | ✅ Sim | ✅ Sim |

## Casos de Uso

### Use `display: none` quando:
- Quiser remover completamente o elemento
- For alternar conteúdo dinamicamente
- Precisar que outros elementos ocupem o espaço

### Use `visibility: hidden` quando:
- Quiser manter o layout intacto
- For criar animações de fade
- Precisar manter referências de posição

## Exemplo Prático
```html
<div class="container">
    <div class="item">Item 1</div>
    <div class="item display-none">Item 2 (display: none)</div>
    <div class="item visibility-hidden">Item 3 (visibility: hidden)</div>
    <div class="item">Item 4</div>
</div>
```

```css
.display-none {
    display: none;        /* Item 4 sobe para perto do Item 1 */
}

.visibility-hidden {
    visibility: hidden;   /* Item 4 mantém posição original */
}
```

## Links Relacionados
- [[CSS-Flexbox]]
- [[CSS-Box-Model-Conceito]]
- [[CSS-Grid]]
- [[CSS-Propriedades-Basicas]]