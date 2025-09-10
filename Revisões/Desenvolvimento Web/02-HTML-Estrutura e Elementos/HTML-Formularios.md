
```markdown
# HTML - Formulários

#html #formularios #inputs #validacao

## Estrutura Geral
```html
<form method="POST" action="/submit">
    <label for="nome">Nome:</label>
    <input type="text" id="nome" name="nome" required>
    
    <button type="submit">Enviar</button>
</form>
```

## ⚠️ Regras Semânticas

| Situação | Semântica Correta |
|----------|-------------------|
| **Input para envio de dados ao servidor** | Dentro de um `<form>` |
| **Input para controle local** | Pode ficar fora do `<form>` |
| **Label** | Sempre relacionado com input, dentro ou fora de form |
| **Button** | Usar `type="button"` se utilizar fora de form |

## Tipos de `<input>`

### Básicos
```html
<input type="text">        <!-- Texto -->
<input type="password">    <!-- Senha -->
<input type="email">       <!-- Email -->
<input type="number">      <!-- Número -->
<input type="hidden">      <!-- Oculto -->
```

### Seleção
```html
<input type="checkbox">    <!-- Caixa de seleção -->
<input type="radio">       <!-- Botão de rádio -->
<input type="file">        <!-- Arquivo -->
```

### Outros Tipos
```html
<input type="tel">         <!-- Telefone -->
<input type="search">      <!-- Busca -->
<input type="url">         <!-- URL -->
<input type="color">       <!-- Cor -->
<input type="range">       <!-- Slider (min, max, step) -->
<input type="date">        <!-- Data -->
<input type="datetime-local"> <!-- Data e hora -->
```

## Elementos para Listas
```html
<!-- Datalist -->
<input list="navegadores" name="navegador">
<datalist id="navegadores">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
</datalist>

<!-- Select -->
<select name="pais">
    <option value="br">Brasil</option>
    <option value="us">Estados Unidos</option>
    <option value="ca">Canadá</option>
</select>
```

## Para Grande Quantidade de Texto
```html
<textarea name="comentario" rows="4" cols="50">
    Texto inicial...
</textarea>
```

## Elementos Extras

### Agrupamento
```html
<fieldset>
    <legend>Informações Pessoais</legend>
    <input type="text" name="nome">
    <input type="email" name="email">
</fieldset>
```

### Botões
```html
<button type="submit">Enviar</button>
<button type="reset">Limpar</button>
<button type="button">Ação Personalizada</button>
```

### Label
```html
<!-- Forma 1: por atributo -->
<label for="nome">Nome:</label>
<input type="text" id="nome">

<!-- Forma 2: aninhado -->
<label>
    Nome:
    <input type="text" name="nome">
</label>
```

## Validação HTML5
```html
<input type="email" required>
<input type="text" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
<input type="number" min="1" max="100">
<input type="text" maxlength="50">
```

## Links Relacionados
- [[HTML-Tabelas]]
- [[HTML-Elementos-Estruturais]]