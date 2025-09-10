#css #seletores #especificidade #pseudoclasses

## Seletores Básicos

### Por Elemento
```css
p { color: blue; }
h1 { font-size: 24px; }
```

### Por Classe
```css
.destaque { background-color: yellow; }
.botao { padding: 10px; }
```

### Por ID
```css
#cabecalho { height: 100px; }
#rodape { background: gray; }
```

### Universal
```css
* { margin: 0; padding: 0; }
```

## Caracteres de Combinação

### Espaço (Descendente)
```css
div p { /* Todos os <p> dentro de <div> */ }
```

### > (Filhos Diretos)
```css
div > p { /* Apenas <p> filhos diretos de <div> */ }
```

### + (Irmão Adjacente)
```css
div + p { /* <p> imediatamente após <div> */ }
```

### ~ (Irmãos)
```css
div ~ p { /* Todos os <p> irmãos após <div> */ }
```

## Exemplo Visual
```html
<div>
    <span>
        <p>P1</p>
        <p>P2</p>
    </span>
    <p>P3</p>
    <aside>
        <p>P4</p>
    </aside>
    <p>P5</p>
    <p>P6</p>
</div>
```

### Resultados dos Seletores
- `div p` → P1, P2, P3, P4, P5, P6
- `div > p` → P3, P5, P6
- `div + p` → Nenhum (não há p após div)
- `div ~ p` → Nenhum (não há p irmão de div)

## Seletor de Atributos
```css
E[x]           /* Atributo existe */
E[x="val"]     /* Valor exato */
E[x^="val"]    /* Começa com */
E[x$="val"]    /* Termina com */
E[x*="val"]    /* Contém em qualquer lugar */
```

### Exemplos
```css
input[type="email"] { border: 2px solid blue; }
a[href^="https"] { color: green; }
img[alt*="importante"] { border: 3px solid red; }
```

## Links Relacionados
- [[CSS-Pseudoclasses]]
- [[CSS-Pseudoelementos]]
- [[CSS-Especificidade]]
- [[CSS-Introducao-Geral]]