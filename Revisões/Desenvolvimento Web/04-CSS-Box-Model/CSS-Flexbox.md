#css #flexbox #layout #unidimensional

## Conceitos Básicos

**Flexbox** é um sistema de layout **unidimensional** para distribuir espaço e alinhar itens em um container.

### Componentes
- **Flex Container** - Elemento pai (display: flex)
- **Flex Item** - Elementos filhos diretos

### Eixos
- **Eixo Principal (Main Axis)** - Direção definida por flex-direction
- **Eixo Transversal (Cross Axis)** - Perpendicular ao eixo principal

## Flex Container

### Criando um Flex Container
```css
.container {
    display: flex;          /* ou inline-flex */
}
```

### Propriedades do Container

#### flex-direction
**Define a direção do eixo principal**
```css
flex-direction: row;            /* Padrão: horizontal, esquerda→direita */
flex-direction: row-reverse;    /* Horizontal, direita→esquerda */
flex-direction: column;         /* Vertical, cima→baixo */
flex-direction: column-reverse; /* Vertical, baixo→cima */
```

#### justify-content
**Alinhamento no eixo principal**
```css
justify-content: flex-start;    /* Início (padrão) */
justify-content: flex-end;      /* Final */
justify-content: center;        /* Centro */
justify-content: space-between; /* Espaço entre itens */
justify-content: space-around;  /* Espaço ao redor dos itens */
justify-content: space-evenly;  /* Espaço igual entre e ao redor */
```

#### align-items
**Alinhamento no eixo transversal**
```css
align-items: stretch;       /* Estica para preencher (padrão) */
align-items: flex-start;    /* Início do eixo transversal */
align-items: flex-end;      /* Final do eixo transversal */
align-items: center;        /* Centro do eixo transversal */
align-items: baseline;      /* Linha base do texto */
```

#### flex-wrap
**Controla quebra de linha**
```css
flex-wrap: nowrap;      /* Não quebra (padrão) */
flex-wrap: wrap;        /* Quebra se necessário */
flex-wrap: wrap-reverse; /* Quebra em ordem reversa */
```

#### gap
**Espaçamento entre itens**
```css
gap: 20px;              /* Espaço igual */
gap: 10px 20px;         /* Linha coluna */
```

## Flex Items

### Propriedades dos Itens

#### flex
**Controla crescimento, encolhimento e tamanho base**
```css
flex: 1;                /* flex: 1 1 0% (cresce igualmente) */
flex: 2;                /* flex: 2 1 0% (cresce 2x mais) */
flex: 0 0 200px;        /* Não cresce/encolhe, 200px fixo */
```

#### align-self
**Sobrescreve align-items para item individual**
```css
align-self: auto;       /* Usa valor do container */
align-self: flex-start; /* Início */
align-self: flex-end;   /* Final */
align-self: center;     /* Centro */
align-self: stretch;    /* Estica */
```

#### order
**Altera ordem visual (não afeta HTML)**
```css
order: 0;               /* Padrão */
order: 1;               /* Vai para depois */
order: -1;              /* Vai para antes */
```

## Exemplos Práticos

### Layout Horizontal Centralizado
```css
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}
```

### Distribuição de Espaço
```css
.container {
    display: flex;
}

.item-1 { flex: 1; }    /* Cresce 1 parte */
.item-2 { flex: 2; }    /* Cresce 2 partes */
.item-3 { flex: 1; }    /* Cresce 1 parte */
```

### Layout de Header
```css
.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo { flex: 0 0 auto; }      /* Tamanho fixo */
.nav { flex: 1; }              /* Cresce */
.actions { flex: 0 0 auto; }   /* Tamanho fixo */
```

## Links e Recursos

### Documentação e Guias
- **MDN:** https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox
- **Guia Completo:** https://origamid.com/projetos/flexbox-guia-completo/

### Jogo para Praticar
- **Flexbox Froggy:** https://flexboxfroggy.com/#pt-br

## Links Relacionados
- [[CSS-Grid]]
- [[CSS-Display-Visibility]]
- [[CSS-Box-Model-Conceito]]