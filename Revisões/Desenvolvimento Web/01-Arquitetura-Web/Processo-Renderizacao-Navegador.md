#navegador #dom #cssom #renderizacao #javascript

## Visão Geral da Renderização

```

Parsing HTML + CSS → DOM + CSSOM → Render Tree → Layout → Painting → Compositing
                                      ↑
                                  JavaScript

```

## Etapas Detalhadas

### 1. Parsing HTML e Construção do DOM (exemplo)
```

html
├── head
│   ├── meta
│   ├── title
│   └── link
└── body
    ├── h1
    └── p

```

### 2. Construção do CSSOM (exemplo)
```

Stylesheet
└── h1
    └── color: blue

```

### 3. Render Tree
- **DOM + CSSOM**
- Contém os elementos **visíveis** na tela e seus estilos computados

### 4. Layout
- O navegador calcula a **posição e tamanho exato** de cada elemento

### 5. Painting
- O navegador pinta os pixels na tela
- Decide cor, sombra, borda, imagens etc.

### 6. Compositing
- O navegador separa partes da tela em **camadas**
- Compõe tudo e exibe na janela do navegador

## JavaScript no Processo

### Comportamento Padrão
Ao encontrar elemento `<script>` sem `async` ou `defer`:
1. **Pausa** a construção da DOM
2. Faz o **download** do script (se externo)
3. **Executa** o script
4. **Retoma** a leitura do HTML

### Atributos Importantes
- **`async`**: Carregados em paralelo, executados assim que terminam de baixar
- **`defer`**: Baixados em paralelo, executados só depois que o DOM estiver pronto

### Impacto nas Modificações
- Modificações no DOM ou CSSOM via JavaScript podem disparar:
  - **Reflow (Layout)** - mais custoso
  - **Repaint (Painting)** - menos custoso

## Links Relacionados
- [[HTML-Estrutura-Geral]]
- [[Arquitetura-Web-Visao-Geral]]
