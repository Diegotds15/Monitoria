# Roadmap - Linguagem de Programação Web I

## 🧠 Mapa Mental do Curso

```
Linguagem de Programação Web I
├── 📐 Fundamentos da Web
│   ├── Arquitetura Web (Cliente-Servidor)
│   ├── HTTP/HTTPS e URLs
│   └── Processo de Renderização do Navegador
├── 🏗️ HTML Estrutural
│   ├── Elementos e Atributos
│   ├── Elementos Textuais e Imagens
│   ├── Estruturas Semânticas
│   ├── Listas e Tabelas
│   └── Formulários
├── 🎨 CSS Estilização
│   ├── Seletores e Especificidade
│   ├── Propriedades Básicas
│   └── Box Model
└── 📦 Layouts Avançados
    ├── Display e Visibility
    ├── Flexbox (1D)
    └── Grid (2D)
```

---

## 🗺️ Sequência de Estudo

### 📚 Módulo 1: Fundamentos da Arquitetura Web
**Objetivo:** Compreender como a web funciona

### 📚 Módulo 2: HTML - Estrutura e Semântica
**Objetivo:** Dominar a marcação e estruturação de conteúdo

### 📚 Módulo 3: CSS - Apresentação e Estilo
**Objetivo:** Estilizar e apresentar o conteúdo HTML

### 📚 Módulo 4: Layouts Modernos
**Objetivo:** Criar layouts responsivos e complexos

---

## 📐 Módulo 1: Fundamentos da Arquitetura Web

### 🌐 Web vs Internet
- **Internet:** Rede global de computadores conectados
- **Web:** Sistema de documentos interligados que funciona sobre a internet

### 🔗 URL (Uniform Resource Locator)
```
http://www.exemplo.com.br:80/pasta1/carregar.html?user=123&p1=AAA#secao2
└──┘   └─────────────────┘└─┘└─────────────────────┘└─────────────┘└──────┘
scheme      host         port        path           query string  anchor
```

**Componentes:**
- **Scheme:** Protocolo (http, https)
- **Host:** Domínio do servidor
- **Port:** Porta de rede (80 para HTTP, 443 para HTTPS)
- **Path:** Caminho do recurso
- **Query String:** Parâmetros adicionais
- **Anchor:** Referência específica na página

### 📡 HTTP - HyperText Transfer Protocol

**Métodos Principais:**
- `GET` 📥 - Buscar recurso
- `POST` 📨 - Enviar dados
- `PUT` ✏️ - Atualizar recurso
- `DELETE` 🗑️ - Remover recurso

**Códigos de Resposta:**
- `1xx` - Informativo
- `2xx` - Sucesso (200 OK)
- `3xx` - Redirecionamento
- `4xx` - Erro do cliente (404 Not Found)
- `5xx` - Erro do servidor

**Evolução HTTP:**
- **HTTP/1.1 (1997):** Uma requisição por conexão
- **HTTP/2 (2015):** Multiplexação, cabeçalhos comprimidos
- **HTTP/3 (2022):** QUIC sobre UDP, menor latência

### 🖥️ Processo de Renderização do Navegador

**Etapas:**
1. **Parsing HTML** → DOM (Document Object Model)
2. **Parsing CSS** → CSSOM (CSS Object Model)
3. **Render Tree** → DOM + CSSOM
4. **Layout** → Cálculo de posições e tamanhos
5. **Painting** → Pintura dos pixels
6. **Compositing** → Composição final das camadas

**JavaScript no Processo:**
- Scripts sem `async`/`defer`: Pausam a construção do DOM
- Scripts com `async`: Carregados em paralelo, executados imediatamente
- Scripts com `defer`: Carregados em paralelo, executados após DOM pronto

---

## 🏗️ Módulo 2: HTML - Estrutura e Semântica

### 🧱 Elementos HTML

**Block-level vs Inline-level:**

| Característica | Block-level | Inline-level |
|---------------|-------------|--------------|
| Espaço | Toda largura disponível | Apenas espaço do conteúdo |
| Quebra de linha | Sim | Não |
| Aninhamento | Block e inline | Apenas inline |
| Exemplos | `div`, `p`, `h1-h6`, `section` | `span`, `a`, `b`, `em`, `img` |

### 📝 Elementos Textuais

**Estruturais:**
- `h1` a `h6` - Cabeçalhos hierárquicos
- `p` - Parágrafos
- `div` - Container genérico (block)
- `span` - Container genérico (inline)

**Semânticos:**
- `strong` - Texto importante (negrito)
- `em` - Texto enfatizado (itálico)
- `mark` - Texto destacado
- `small` - Texto pequeno
- `del` - Texto deletado
- `ins` - Texto inserido

### 🖼️ Elementos de Imagem
- `img` - Imagem (com `src`, `alt`, `width`, `height`)
- `figure` + `figcaption` - Imagem com legenda
- `picture` + `source` - Imagens responsivas

### 🏛️ Elementos Estruturais Semânticos

**Layout Principal:**
- `header` - Cabeçalho da página/seção
- `main` - Conteúdo principal (único por página)
- `nav` - Navegação
- `section` - Seção de conteúdo
- `article` - Conteúdo independente
- `aside` - Conteúdo lateral/complementar
- `footer` - Rodapé

**Outros:**
- `details` + `summary` - Conteúdo expansível
- `iframe` - Incorporar conteúdo externo

### 📋 Listas

**Tipos:**
- `ul` + `li` - Lista não ordenada
- `ol` + `li` - Lista ordenada
- `dl` + `dt` + `dd` - Lista de definições

### 📊 Tabelas

**Estrutura:**
```html
<table>
  <caption>Título da tabela</caption>
  <thead>
    <tr><th>Cabeçalho</th></tr>
  </thead>
  <tbody>
    <tr><td>Dados</td></tr>
  </tbody>
  <tfoot>
    <tr><td>Rodapé</td></tr>
  </tfoot>
</table>
```

**⚠️ Importante:** Use tabelas apenas para dados tabulares, nunca para layout!

### 📝 Formulários

**Estrutura Básica:**
```html
<form method="POST" action="/submit">
  <label for="nome">Nome:</label>
  <input type="text" id="nome" name="nome" required>
  <button type="submit">Enviar</button>
</form>
```

**Tipos de Input:**
- `text`, `password`, `email`, `tel`, `url`
- `number`, `range`, `date`, `datetime-local`
- `color`, `file`, `hidden`
- `checkbox`, `radio`
- `search`

**Outros Elementos:**
- `textarea` - Texto longo
- `select` + `option` - Lista suspensa
- `fieldset` + `legend` - Agrupamento
- `button` - Botões personalizados

**Regras Semânticas:**
- Input para envio: Dentro de `form`
- Input para controle local: Pode ficar fora
- `label`: Sempre relacionado com input
- `button`: Use `type="button"` se fora do form

---

## 🎨 Módulo 3: CSS - Apresentação e Estilo

### 🔗 Vinculação com HTML

**Métodos:**
1. **Externa:** `<link rel="stylesheet" href="styles.css">`
2. **Incorporada:** `<style>...</style>`
3. **Inline:** `<div style="...">`

### 📏 Unidades

**Relativas:**
- `em` - Relativo ao elemento pai
- `rem` - Relativo ao elemento raiz
- `vh`, `vw` - Viewport height/width
- `%` - Porcentagem

**Absolutas:**
- `px` - Pixels CSS
- `pt`, `cm`, `mm`, `in` - Unidades físicas

### 🎯 Seletores

**Básicos:**
- `elemento` - Por tag
- `.classe` - Por classe
- `#id` - Por ID
- `*` - Universal

**Combinadores:**
- `A B` - Descendente (espaço)
- `A > B` - Filho direto
- `A + B` - Irmão adjacente
- `A ~ B` - Irmãos gerais

**Atributos:**
- `[attr]` - Atributo existe
- `[attr="val"]` - Valor exato
- `[attr^="val"]` - Começa com
- `[attr$="val"]` - Termina com
- `[attr*="val"]` - Contém

### 🎭 Pseudoclasses

**Estados:**
- `:hover` - Mouse sobre o elemento
- `:focus` - Elemento em foco
- `:active` - Elemento ativo
- `:visited` - Link visitado

**Estruturais:**
- `:first-child`, `:last-child`
- `:nth-child(n)`, `:nth-of-type(n)`
- `:not(seletor)`

### 👻 Pseudoelementos

- `::before` - Antes do conteúdo
- `::after` - Depois do conteúdo
- `::first-line` - Primeira linha
- `::first-letter` - Primeira letra

### ⚖️ Especificidade e Cascata

**Ordem de Prioridade:**
1. Folha de estilo do navegador
2. Folha de estilo do usuário
3. Folha de estilo do desenvolvedor
4. Inline styles
5. Declarações `!important`

**Cálculo de Especificidade (a,b,c,d):**
- **a:** Inline styles
- **b:** IDs
- **c:** Classes, pseudoclasses, atributos
- **d:** Elementos, pseudoelementos

### 🎨 Propriedades Essenciais

**Texto:**
- `color`, `font-family`, `font-size`
- `font-weight`, `text-align`, `line-height`

**Fundo:**
- `background-color` (transparente por padrão)
- `background-image`, `background-size`
- `background-position`, `background-repeat`

**Bordas:**
- `border`, `border-radius`
- `border-width`, `border-style`, `border-color`

---

## 📦 Módulo 4: Box Model e Layouts Modernos

### 📦 Box Model

**Componentes (de dentro para fora):**
1. **Content** - Conteúdo
2. **Padding** - Espaçamento interno
3. **Border** - Borda
4. **Margin** - Espaçamento externo

### 📐 box-sizing

**Valores:**
- `content-box` (padrão) - Width/height apenas do conteúdo
- `border-box` - Width/height inclui padding e border

### 👁️ Display vs Visibility

**Display:**
- `block` - Elemento em bloco
- `inline` - Elemento em linha
- `inline-block` - Híbrido
- `none` - Remove do layout

**Visibility:**
- `visible` - Visível
- `hidden` - Oculto (mantém espaço)

### 🌊 Flexbox (Layout Unidimensional)

**Container (flex container):**
```css
.container {
  display: flex;
  flex-direction: row | column;
  justify-content: flex-start | center | space-between;
  align-items: stretch | center | flex-start;
}
```

**Itens (flex items):**
```css
.item {
  flex: 1; /* grow shrink basis */
  align-self: auto | center | flex-start;
}
```

**Eixos:**
- **Principal:** Direção definida por `flex-direction`
- **Transversal:** Perpendicular ao principal

### 🔲 Grid (Layout Bidimensional)

**Container (grid container):**
```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-template-rows: auto 1fr auto;
  gap: 20px;
}
```

**Itens (grid items):**
```css
.item {
  grid-column: 1 / 3;
  grid-row: 2 / 4;
}
```

### 📊 Unidade fr (Fração)

**Exemplo:**
- Container: `width: 600px`
- 3 itens: `width: 2fr` cada
- Cálculo: `600px / (3 × 2) = 100px/fr`
- Cada item: `2fr = 200px`

---

## 🎮 Recursos para Prática

### 🐸 Jogos Interativos
- **Flexbox Froggy:** https://flexboxfroggy.com/#pt-br
- **Grid Garden:** https://cssgridgarden.com/#pt-br

### 📚 Documentação de Referência
- **Flexbox:** https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox
- **Grid:** https://developer.mozilla.org/pt-BR/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout
- **Pseudoclasses:** https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes
- **Pseudoelementos:** https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements

---

## 📝 Resumo de Boas Práticas

### ✅ HTML
- Use elementos semânticos sempre que possível
- Apenas um `main` por página
- `aside` para conteúdo complementar
- Tabelas apenas para dados tabulares
- `iframe` com cuidado (segurança/performance)

### ✅ CSS
- Prefira unidades relativas
- Use `box-sizing: border-box`
- Organize seletores por especificidade
- Evite `!important` desnecessário
- Background transparente por padrão

### ✅ Layout
- Flexbox para layouts 1D (linha ou coluna)
- Grid para layouts 2D (linha e coluna)
- Use `fr` para distribuição proporcional
- Considere responsividade desde o início

---

## 🎯 Próximos Passos

1. **Pratique cada módulo sequencialmente**
2. **Faça projetos pequenos combinando os conceitos**
3. **Use os jogos interativos para fixar Flexbox e Grid**
4. **Consulte a documentação oficial regularmente**
5. **Experimente com diferentes combinações de propriedades**

**Lembre-se:** A prática consistente é fundamental para dominar estes conceitos!