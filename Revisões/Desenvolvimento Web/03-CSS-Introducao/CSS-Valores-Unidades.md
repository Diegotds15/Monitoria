#css #unidades #valores #medidas

## Tipos de Valores

### Numéricos
- `16px` - Com unidade
- `0` - Sem unidade (quando for zero)
- `1.5` - Decimal

### Texto
- `"Arial"` - Entre aspas
- `Arial` - Sem aspas
- `inherit` - Herda do pai

### Cores
- `red` - Nome
- `#ff0000` - Hexadecimal
- `rgb(255, 0, 0)` - RGB
- `rgba(255, 0, 0, 0.5)` - RGBA

## Tipos de Unidades Numéricas

### Relativas
**Medida é baseada no tamanho de outro elemento**
- `em` - Relativo ao tamanho da fonte do elemento pai
- `rem` - Relativo ao tamanho da fonte do elemento raiz (html)
- `vh` - Viewport height (altura da janela)
- `vw` - Viewport width (largura da janela)
- `%` - Porcentagem relativa ao pai

### Absolutas
**Medida determinada e fixa**
- `px` - CSS pixel (mais comum)
- `pt` - Pontos (72pt = 1 polegada)
- `cm` - Centímetros
- `mm` - Milímetros
- `in` - Polegadas

## 📌 Dica Importante
**Quando for 0 (zero) não precisa especificar a unidade!**
```css
margin: 0;     /* Correto */
margin: 0px;   /* Desnecessário */
```

## Exemplos Práticos
```css
/* Unidades relativas */
font-size: 1.2em;        /* 20% maior que o pai */
width: 50%;               /* Metade da largura do pai */
height: 100vh;            /* Altura total da janela */

/* Unidades absolutas */
border: 1px solid black;  /* Borda de 1 pixel */
padding: 10px;            /* Espaçamento de 10 pixels */
```

## Links Relacionados
- [[CSS-Seletores]]
- [[CSS-Introducao-Geral]]
- [[CSS-Propriedades-Basicas]]
