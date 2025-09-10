#css #pseudoelementos #conteudo-gerado

## Conceito
- **Elementos que não aparecem na árvore DOM**, mas podem ser tratados como elementos regulares
- Sintaxe: `::nome-do-pseudoelemento`

## Pseudoelementos Principais

### ::before e ::after
```css
.destaque::before {
    content: "★ ";
    color: gold;
}

.destaque::after {
    content: " ★";
    color: gold;
}
```

**HTML:**
```html
<p class="destaque">Texto importante</p>
```

**Resultado:** ★ Texto importante ★

### ::first-line
```css
p::first-line {
    font-weight: bold;
    text-transform: uppercase;
}
```

### ::first-letter
```css
p::first-letter {
    font-size: 3em;
    float: left;
    margin-right: 5px;
}
```

### ::selection
```css
::selection {
    background-color: yellow;
    color: black;
}
```

## Exemplos Práticos

### Tooltip com ::after
```css
.tooltip {
    position: relative;
}

.tooltip::after {
    content: attr(data-tooltip);
    position: absolute;
    bottom: 100%;
    left: 50%;
    transform: translateX(-50%);
    background: black;
    color: white;
    padding: 5px 10px;
    border-radius: 4px;
    opacity: 0;
    transition: opacity 0.3s;
}

.tooltip:hover::after {
    opacity: 1;
}
```

### Ícones com ::before
```css
.email::before {
    content: "📧 ";
}

.phone::before {
    content: "📞 ";
}
```

## Regras Importantes
- **Sempre precisam da propriedade `content`**
- **Não funcionam em elementos vazios** (como `<img>`, `<input>`)
- **São inline por padrão**

## Links Relacionados
- [[CSS-Especificidade]]
- [[CSS-Pseudoclasses]]
- [[CSS-Seletores]]

**Documentação:** https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements