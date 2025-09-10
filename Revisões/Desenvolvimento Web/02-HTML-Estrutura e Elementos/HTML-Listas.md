#html #listas #organizacao #conteudo

## Lista Não Ordenada (ul)
```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

## Lista Ordenada (ol)
```html
<ol>
    <li>Primeiro item</li>
    <li>Segundo item</li>
    <li>Terceiro item</li>
</ol>
```

## Lista de Definições (dl)
```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
    
    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
    
    <dt>JavaScript</dt>
    <dd>Linguagem de programação para web</dd>
</dl>
```

## 📌 Guia de Uso

| Situação | Melhor Escolha |
|----------|----------------|
| **Glossário ou lista de definições** | `<dl>` |
| **FAQ interativo** | `<details>` |
| **Mostrar/esconder conteúdo extra opcional** | `<details>` |
| **Lista simples de termos e descrições** | `<dl>` |

### Exemplo FAQ Interativo
```html
<details>
    <summary>O que é HTML?</summary>
    <p>HTML é uma linguagem de marcação usada para estruturar conteúdo web.</p>
</details>
```

## Dicas
- Use `<dl>`, `<dt>` e `<dd>` quando quiser **definir termos**
- Use `<details>` e `<summary>` quando precisar que informações adicionais **fiquem ocultas** até que o usuário solicite

## Links Relacionados]]
- [[HTML-Tabelas]]
- [[HTML-Elementos-Estruturais]]