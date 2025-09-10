#css #estilizacao #apresentacao #visual

## Conceito
- **Utilizada para apresentar o HTML**
- **Tudo que diz respeito à questão visual** deve ser feito no CSS
- Arquivos com **extensão `.css`**

## Como Vincular ao HTML?

### 1. CSS Externo (Recomendado)
```html
<link rel="stylesheet" href="estilos.css">
```

### 2. CSS Incorporado
```html
<style>
    body { background-color: blue; }
</style>
```

### 3. CSS Inline
```html
<p style="color: red; font-size: 16px;">Texto</p>
```

## Sintaxe das Folhas de Estilo
```css
seletor {
    propriedade: valor;
    propriedade: valor;
}
```

### Exemplo
```css
h1 {
    color: blue;
    font-size: 24px;
    text-align: center;
}
```

## Aninhamento e Agrupamento

### Agrupamento de Seletores
```css
h1, h2, h3 {
    color: blue;
    font-family: Arial;
}
```

### Aninhamento (Descendentes)
```css
article p {
    line-height: 1.5;
}

nav ul li {
    display: inline-block;
}
```

## Links Relacionados
- [[CSS-Valores-Unidades]]
- [[CSS-Propriedades-Basicas]]
- [[CSS-Seletores]]
- [[HTML-Estrutura-Geral]]