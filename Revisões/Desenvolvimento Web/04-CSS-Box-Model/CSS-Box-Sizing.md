#css #box-sizing #dimensionamento

## Propriedade box-sizing

**Define o que considerar no valor final de `width` e `height`**

## content-box (Padrão)

```css
box-sizing: content-box;
```

- **Somente a área de conteúdo** é considerada
- `width` e `height` aplicam-se apenas ao conteúdo
- Padding e border são **adicionados** ao tamanho total

### Exemplo content-box
```css
.elemento {
    box-sizing: content-box;
    width: 200px;
    padding: 20px;
    border: 5px solid black;
}
```

**Largura total:** 200px + 40px (padding) + 10px (border) = **250px**

## border-box (Recomendado)

```css
box-sizing: border-box;
```

- **Inclui padding e border** no cálculo
- `width` e `height` são o tamanho **total** do elemento
- Conteúdo se ajusta automaticamente

### Exemplo border-box
```css
.elemento {
    box-sizing: border-box;
    width: 200px;
    padding: 20px;
    border: 5px solid black;
}
```

**Largura total:** **200px** (padding e border incluídos)  
**Largura do conteúdo:** 200px - 40px (padding) - 10px (border) = **150px**

## Aplicação Global (Boa Prática)

```css
* {
    box-sizing: border-box;
}
```

ou

```css
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

## Vantagens do border-box

1. **Cálculos mais simples** - width definido é width final
2. **Layouts mais previsíveis** - elementos não "estouram" containers
3. **Responsive design mais fácil** - porcentagens funcionam como esperado

## Exemplo Comparativo

```css
/* Dois elementos com width: 50% */
.content-box {
    box-sizing: content-box;
    width: 50%;
    padding: 20px;
    /* Largura real: 50% + 40px → pode quebrar layout */
}

.border-box {
    box-sizing: border-box; 
    width: 50%;
    padding: 20px;
    /* Largura real: exatos 50% → layout preservado */
}
```

## Links Relacionados
- [[CSS-Display-Visibility]]
- [[CSS-Box-Model-Conceito]]
- [[CSS-Propriedades-Basicas]]
