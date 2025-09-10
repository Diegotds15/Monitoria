#html #tabelas #dados-tabulares

## Estrutura Geral
```html
<table>
    <caption>Título da tabela</caption>
    <thead>
        <tr>
            <th>Cabeçalho 1</th>
            <th>Cabeçalho 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Dado 1</td>
            <td>Dado 2</td>
        </tr>
        <tr>
            <td>Dado 3</td>
            <td>Dado 4</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Total</td>
            <td>Soma</td>
        </tr>
    </tfoot>
</table>
```

## Elementos da Tabela
- **`<table>`** - Container principal
- **`<caption>`** - Título/descrição da tabela
- **`<thead>`** - Cabeçalho da tabela
- **`<tbody>`** - Corpo da tabela (dados)
- **`<tfoot>`** - Rodapé da tabela
- **`<tr>`** - Linha da tabela
- **`<th>`** - Célula de cabeçalho
- **`<td>`** - Célula de dados

## Atributos Úteis
```html
<td colspan="2">Célula que ocupa 2 colunas</td>
<td rowspan="3">Célula que ocupa 3 linhas</td>
```

## ⚠️ Atenção
- **Utilizar somente para dados tabulares**
- **NÃO utilizar tabelas do HTML para construir layouts**

## Links Relacionados
- [[CSS-Introducao-Geral]]
- [[HTML-Listas]]
- [[HTML-Formularios]]