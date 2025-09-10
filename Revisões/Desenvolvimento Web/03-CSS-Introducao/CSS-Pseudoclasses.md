#css #pseudoclasses #estados #estrutural

## Conceito
- Permite selecionar elementos através do seu **estado** ou **localização no DOM**
- Sintaxe: `:nome-da-pseudoclasse`

## Pseudoclasses de Estado

### Links
```css
a:link { color: blue; }        /* Link não visitado */
a:visited { color: purple; }   /* Link visitado */
a:hover { color: red; }        /* Mouse sobre o link */
a:active { color: orange; }    /* Link sendo clicado */
```

### Formulários
```css
input:focus { border: 2px solid blue; }     /* Campo em foco */
input:disabled { opacity: 0.5; }            /* Campo desabilitado */
input:checked { background: green; }        /* Checkbox/radio marcado */
```

## Pseudoclasses Estruturais

### Filhos
```css
li:first-child { font-weight: bold; }       /* Primeiro filho */
li:last-child { margin-bottom: 0; }         /* Último filho */
li:nth-child(2) { color: red; }             /* Segundo filho */
li:nth-child(odd) { background: #f0f0f0; }  /* Filhos ímpares */
li:nth-child(even) { background: white; }   /* Filhos pares */
```

### Por Tipo
```css
p:first-of-type { margin-top: 0; }          /* Primeiro <p> */
p:last-of-type { margin-bottom: 0; }        /* Último <p> */
p:nth-of-type(3) { font-style: italic; }    /* Terceiro <p> */
```

### Negação
```css
input:not([type="hidden"]) { display: block; }  /* Todos exceto hidden */
```

## Pseudoclasses Funcionais

### Vazio
```css
p:empty { display: none; }                  /* Parágrafos vazios */
```

### Contém Texto
```css
p:contains("importante") { color: red; }    /* Contém texto específico */
```

## 📌 Dica Importante
**`:nth-child(odd)` e `:nth-child(even)` funcionam como um OU**

## Links Relacionados]]
- [[CSS-Pseudoelementos]]
- [[CSS-Seletores]]
- [[CSS-Especificidade]]

**Documentação:** https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes