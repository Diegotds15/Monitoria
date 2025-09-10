#css #propriedades #cores #fontes #background

## Propriedades de Texto

### Cor
```css
color: red;
color: #ff0000;
color: rgb(255, 0, 0);
color: rgba(255, 0, 0, 0.5);
```

### Fonte
```css
font-family: Arial, sans-serif;
font-size: 16px;
font-weight: bold;      /* normal, bold, 100-900 */
font-style: italic;     /* normal, italic, oblique */
```

### Alinhamento e Espaçamento
```css
text-align: left;       /* left, right, center, justify */
line-height: 1.5;       /* Altura da linha */
text-decoration: underline;  /* none, underline, line-through */
text-transform: uppercase;   /* uppercase, lowercase, capitalize */
```

## Propriedades de Fundo

### Background Básico
```css
background-color: blue;
background-image: url('imagem.jpg');
background-repeat: no-repeat;    /* repeat, repeat-x, repeat-y */
background-position: center;     /* top, bottom, left, right, center */
background-size: cover;          /* contain, cover, 100px 200px */
```

### Background Shorthand
```css
background: #f0f0f0 url('bg.jpg') no-repeat center/cover;
```

## 📌 Importante
**Por padrão, o background é transparente!**

## Propriedades de Borda

### Borda Completa
```css
border: 2px solid black;
```

### Borda Detalhada
```css
border-width: 1px;
border-style: solid;    /* solid, dashed, dotted, double */
border-color: red;
border-radius: 5px;     /* Cantos arredondados */
```

### Bordas Individuais
```css
border-top: 1px solid black;
border-right: 2px dashed red;
border-bottom: 3px dotted blue;
border-left: 4px double green;
```

## Propriedades de Espaçamento

### Margin (Espaçamento Externo)
```css
margin: 10px;           /* Todos os lados */
margin: 10px 20px;      /* Vertical Horizontal */
margin: 10px 15px 20px 25px;  /* Top Right Bottom Left */
```

### Padding (Espaçamento Interno)
```css
padding: 10px;          /* Todos os lados */
padding: 10px 20px;     /* Vertical Horizontal */
padding-top: 5px;       /* Individual */
```

## Propriedades de Dimensão
```css
width: 300px;
height: 200px;
max-width: 100%;
min-height: 50px;
```

## Propriedades de Display
```css
display: block;         /* Elemento em bloco */
display: inline;        /* Elemento em linha */
display: inline-block;  /* Híbrido */
display: none;          /* Oculta elemento */
```

## Links Relacionados
- [[CSS-Box-Model-Conceito]]
- [[CSS-Valores-Unidades]]