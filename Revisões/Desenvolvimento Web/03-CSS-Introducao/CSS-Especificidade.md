#css #especificidade #cascata #prioridade

## Problema da Cascata
**Cenário:** Um CSS externo diz que elementos `h1` são vermelhos e um CSS incorporado diz que elementos `h1` são verdes. Qual o navegador deve seguir?

## A Cascata (ordem de prioridade)

### 1. Folha de estilo do navegador (menor prioridade)
### 2. Folha de estilo do usuário
### 3. Folha de estilo do desenvolvedor
   - Externa ou incorporada
### 4. Inline styles
### 5. Declarações `!important` do desenvolvedor
### 6. Declarações `!important` do usuário
### 7. Cálculo da Especificidade (maior prioridade)

## Cálculo da Especificidade

### Sistema (a, b, c, d)
- **a [0,1]** - Inline styles
- **b** - IDs
- **c** - Classes, pseudoclasses e atributos
- **d** - Elementos e pseudoelementos

### Exemplo de Cálculo
```css
/* Exemplo 1 */ p { background-color: red; }
/* (0,0,0,1) = 1 */

/* Exemplo 2 */ div p { background-color: blue; }
/* (0,0,0,2) = 2 */

/* Exemplo 3 */ body div p { background-color: green; }
/* (0,0,0,3) = 3 */

/* Exemplo 4 */ div > p { background-color: yellow; }
/* (0,0,0,2) = 2 */
```

**Qual o navegador escolhe aplicar?**
- **Resposta:** Exemplo 3 (`body div p`) - maior especificidade (3)

### Mais Exemplos
```css
* { }                    /* (0,0,0,0) = 0 */
li { }                   /* (0,0,0,1) = 1 */
ul li { }                /* (0,0,0,2) = 2 */
ul ol+li { }             /* (0,0,0,3) = 3 */
h1 + *[rel=up] { }       /* (0,0,1,1) = 11 */
ul ol li.red { }         /* (0,0,1,3) = 13 */
li.red.level { }         /* (0,0,2,1) = 21 */
style="" { }             /* (1,0,0,0) = 1000 */
#x34y { }                /* (0,1,0,0) = 100 */
```

## Regras de Desempate
1. **Maior especificidade vence**
2. **Em caso de empate:** a última regra declarada vence
3. **`!important` sobrescreve especificidade** (mas não é recomendado)

## Boas Práticas
- **Evite `!important`** - dificulta manutenção
- **Use especificidade crescente** - comece com seletores simples
- **Prefira classes a IDs** para estilização
- **Organize CSS por especificidade**

## Links Relacionados
- [[CSS-Propriedades-Basicas]]
- [[CSS-Seletores]]
- [[CSS-Pseudoclasses]]
- [[CSS-Introducao-Geral]]