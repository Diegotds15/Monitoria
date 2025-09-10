#html #elementos #atributos #estrutura

## Estrutura Básica

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Título da Página</title>
</head>
<body>
    <h1>Conteúdo</h1>
</body>
</html>
```


## Elementos

### Anatomia
```html
<tagname atributo="valor">Conteúdo</tagname>
```

### Elementos Vazios
```html
<br>
<img src="imagem.jpg" alt="Descrição">
<input type="text">
```

## Block-level vs Inline-level

| Característica         | Block-Level                                           | Inline-Level                            |
| ---------------------- | ----------------------------------------------------- | --------------------------------------- |
| **Espaço Ocupado**     | Toda a largura disponível                             | Apenas o espaço do conteúdo             |
| **Quebra de linha**    | Sim                                                   | Não                                     |
| **Aninhamento**        | Elementos block-level, inline-level e texto           | Apenas elementos inline-level e texto   |
| **Exemplos**           | `<div>`, `<p>`, `<h1>–<h6>`, `<section>`, `<article>` | `<span>`, `<a>`, `<b>`, `<em>`, `<img>` |
| **Display CSS padrão** | `display: block`                                      | `display: inline`                       |

[Vídeo de fácil compreensão sobre Block-level vs Inline-Level](https://www.youtube.com/watch?v=M4n-WSkehmI)

## Atributos

### Globais (todos os elementos)
- `id` - Identificador único
- `class` - Classe para estilização
- `style` - Estilos inline
- `title` - Tooltip

### Específicos
- Dependem do elemento
- Ex: `src` para `<img>`, `href` para `<a>`
## Referências para estudo de HTML

[HcodeBrasil - Canal do Youtube - PT-BR](https://www.youtube.com/@HcodeBrasil)
[W3Schools - Canal do Youtube - Dublagem automática para PT-BR](https://www.youtube.com/@w3schools)
[W3Schools - Melhor site de consulta para HTML e qualquer linguagem de programação](https://www.w3schools.com/html/default.asp) 
## Links Relacionados
- [[HTML-Elementos-Textuais]]
- [[HTML-Elementos-Estruturais]]
- [[HTML-Elementos-Imagens]]
- [[HTML-Formularios]]
- [[HTML-Listas]]
- [[HTML-Tabelas]]