#css #grid #layout #bidimensional

## Conceitos Básicos

**CSS Grid** é um sistema de layout **bidimensional** que trabalha com linhas e colunas simultaneamente.

### Componentes
- **Grid Container** - Elemento pai (display: grid)
- **Grid Item** - Elementos filhos diretos

## Grid Container

### Criando um Grid Container
```css
.container {
    display: grid;          /* ou inline-grid */
}
```

### Definindo a Grade

#### grid-template-columns
**Define as colunas da grade**
```css
grid-template-columns: 100px 200px 100px;      /* 3 colunas fixas */
grid-template-columns: 1fr 2fr 1fr;            /* 3 colunas proporcionais */
grid-template-columns: repeat(3, 1fr);         /* 3 colunas iguais */
grid-template-columns: 200px 1fr;              /* Fixa + flexível */
```

#### grid-template-rows
**Define as linhas da grade**
```css
grid-template-rows: auto 1fr auto;             /* Header, main, footer */
grid-template-rows: repeat(3, 200px);          /* 3 linhas de 200px */
grid-template-rows: minmax(100px, auto);       /* Mín 100px, máx conteúdo */
```

### Espaçamento

#### gap
**Espaçamento entre células**
```css
gap: 20px;              /* Mesmo espaço para linhas e colunas */
gap: 20px 10px;         /* Linha coluna */
row-gap: 20px;          /* Apenas entre linhas */
column-gap: 10px;       /* Apenas entre colunas */
```

### Alinhamento

#### justify-items e align-items
**Alinhamento dos itens dentro das células**
```css
justify-items: start;   /* Início horizontal */
justify-items: center;  /* Centro horizontal */
justify-items: end;     /* Final horizontal */

align-items: start;     /* Início vertical */
align-items: center;    /* Centro vertical */
align-items: end;       /* Final vertical */
```

#### justify-content e align-content
**Alinhamento da grade inteira no container**
```css
justify-content: center;    /* Grade centralizada horizontalmente */
align-content: center;      /* Grade centralizada verticalmente */
```

## Grid Items

### Posicionamento

#### grid-column e grid-row
**Posiciona item em linhas/colunas específicas**
```css
.item {
    grid-column: 1 / 3;     /* Da coluna 1 até a 3 (ocupa 2 colunas) */
    grid-row: 2 / 4;        /* Da linha 2 até a 4 (ocupa 2 linhas) */
}

/* Sintaxe alternativa */
.item {
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 2;
    grid-row-end: 4;
}
```

#### grid-area
**Shorthand para posicionamento**
```css
grid-area: 1 / 2 / 3 / 4;  /* row-start / col-start / row-end / col-end */
```

### Alinhamento Individual

#### justify-self e align-self
```css
justify-self: start;    /* Início horizontal na célula */
align-self: center;     /* Centro vertical na célula */
```

## Unidade fr (Fração)

**Representa uma fração do espaço disponível**

### Exemplo de Cálculo
- Container: `width: 600px`
- Colunas: `grid-template-columns: 2fr 2fr 2fr` (3 itens com 2fr cada)
- Cálculo: `600px / (3 × 2) = 100px/fr`
- Cada coluna: `2fr = 200px`

### Exemplos com fr
```css
/* Distribuição igual */
grid-template-columns: 1fr 1fr 1fr;    /* 3 colunas iguais */

/* Distribuição proporcional */
grid-template-columns: 1fr 2fr 1fr;    /* Centro 2x maior */

/* Misto */
grid-template-columns: 200px 1fr 100px; /* Fixa + flexível + fixa */
```

## Exemplos Práticos

### Layout Básico
```css
.container {
    display: grid;
    grid-template-columns: 1fr 3fr 1fr;
    grid-template-rows: auto 1fr auto;
    gap: 20px;
    height: 100vh;
}

.header { grid-column: 1 / -1; }    /* Ocupa todas as colunas */
.sidebar { grid-column: 1; }        /* Primeira coluna */
.main { grid-column: 2; }           /* Segunda coluna */
.aside { grid-column: 3; }          /* Terceira coluna */
.footer { grid-column: 1 / -1; }    /* Ocupa todas as colunas */
```

### Grid de Cards
```css
.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
}
```

### Layout Holy Grail
```css
.holy-grail {
    display: grid;
    grid-template-areas:
        "header header header"
        "nav main aside"
        "footer footer footer";
    grid-template-columns: 200px 1fr 200px;
    grid-template-rows: auto 1fr auto;
    min-height: 100vh;
}

.header { grid-area: header; }
.nav { grid-area: nav; }
.main { grid-area: main; }
.aside { grid-area: aside; }
.footer { grid-area: footer; }
```

## Propriedades Avançadas

### auto-fit vs auto-fill
```css
/* auto-fit: colunas se expandem para preencher espaço */
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));

/* auto-fill: mantém colunas vazias */
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
```

### minmax()
```css
/* Mínimo 100px, máximo 1 fração */
grid-template-columns: minmax(100px, 1fr) 2fr;
```

### Linhas Nomeadas
```css
grid-template-columns: [start] 250px [content-start] 1fr [content-end] 250px [end];
```

## Links e Recursos

### Documentação e Guias
- **MDN:** https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout
- **Guia Completo:** https://www.origamid.com/projetos/css-grid-layout-guia-completo/

### Jogo para Praticar
- **Grid Garden:** https://cssgridgarden.com/#pt-br

## Links Relacionados
- [[CSS-Unidade-Fr]]
- [[CSS-Flexbox]]
- [[CSS-Display-Visibility]]