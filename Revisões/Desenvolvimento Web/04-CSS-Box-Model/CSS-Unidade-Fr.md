#css #fr #unidade #flexibilidade

## Conceito

**`fr`** representa uma **fração relativa** do espaço disponível em um container Grid ou Flexbox.

## Como Funciona

### Fórmula de Cálculo
```
Espaço disponível ÷ Total de frações = Valor de 1fr
```

### Exemplo Básico
- **Container:** `width: 600px`
- **3 itens:** `width: 2fr` cada
- **Cálculo:** `600px ÷ (3 × 2) = 100px/fr`
- **Cada item:** `2fr = 200px`

## Exemplos Práticos

### Distribuição Igual
```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;  /* 3 colunas iguais */
    width: 900px;
}
/* Resultado: cada coluna = 300px */
```

### Distribuição Proporcional
```css
.container {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr;  /* Centro 2x maior */
    width: 800px;
}
/* 
Total fr: 1 + 2 + 1 = 4fr
800px ÷ 4 = 200px/fr
Colunas: 200px, 400px, 200px 
*/
```

### Misto: Fixo + Flexível
```css
.container {
    display: grid;
    grid-template-columns: 200px 1fr 100px;
    width: 800px;
}
/* 
Espaço disponível: 800px - 200px - 100px = 500px
Coluna central: 500px (todo espaço restante)
*/
```

### Múltiplas Frações
```css
.container {
    display: grid;
    grid-template-columns: 3fr 1fr 2fr;
    width: 600px;
}
/* 
Total fr: 3 + 1 + 2 = 6fr
600px ÷ 6 = 100px/fr
Colunas: 300px, 100px, 200px 
*/
```

## Flexbox com fr

### Usando flex com números
```css
.container {
    display: flex;
    width: 600px;
}

.item-1 { flex: 1; }  /* 1 parte */
.item-2 { flex: 2; }  /* 2 partes */  
.item-3 { flex: 1; }  /* 1 parte */

/* Resultado: 150px, 300px, 150px */
```

## Vantagens da Unidade fr

1. **Responsiva por natureza** - ajusta automaticamente
2. **Cálculos automáticos** - não precisa calcular porcentagens
3. **Flexibilidade** - combina bem com unidades fixas
4. **Distribuição proporcional** - controle preciso das proporções

## Comparação com Outras Unidades

| Unidade | Comportamento | Uso |
|---------|---------------|-----|
| `px` | Fixa | Tamanhos específicos |
| `%` | Relativa ao pai | Layouts responsivos básicos |
| `fr` | Fração do espaço livre | Distribuição flexível |
| `auto` | Tamanho do conteúdo | Ajuste automático |

## Exemplo Complexo
```css
.layout {
    display: grid;
    grid-template-columns: 
        minmax(200px, 1fr)    /* Sidebar flexível */
        3fr                   /* Conteúdo principal */
        minmax(150px, 1fr);   /* Sidebar direita */
    width: 1200px;
    gap: 20px;
}
```

## Casos de Uso Comuns

### Dashboard com Sidebar
```css
.dashboard {
    display: grid;
    grid-template-columns: 250px 1fr;  /* Sidebar fixa + conteúdo flexível */
}
```

### Cards Responsivos
```css
.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
}
```

### Header com Logo e Menu
```css
.header {
    display: grid;
    grid-template-columns: auto 1fr auto;  /* Logo + espaço + botões */
    gap: 1rem;
    align-items: center;
}
```

## Links Relacionados
- [[Links-Documentacao]]
- [[CSS-Grid]]
- [[CSS-Flexbox]]
- [[CSS-Valores-Unidades]]