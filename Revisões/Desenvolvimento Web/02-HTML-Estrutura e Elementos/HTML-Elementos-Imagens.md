#html #imagens #responsivo #acessibilidade

## Imagem Básica
```html
<img src="caminho/imagem.jpg" alt="Descrição da imagem" width="300" height="200">
```

## Figura com Legenda
```html
<figure>
    <img src="grafico.png" alt="Gráfico de vendas 2024">
    <figcaption>Figura 1: Crescimento das vendas em 2024</figcaption>
</figure>
```

## Imagens Responsivas
```html
<picture>
    <source media="(max-width: 768px)" srcset="imagem-mobile.jpg">
    <source media="(max-width: 1024px)" srcset="imagem-tablet.jpg">
    <img src="imagem-desktop.jpg" alt="Descrição">
</picture>
```

## Atributos Importantes
- **`src`** - Caminho da imagem (obrigatório)
- **`alt`** - Texto alternativo para acessibilidade (obrigatório)
- **`width`** - Largura em pixels
- **`height`** - Altura em pixels
- **`loading`** - `lazy` para carregamento sob demanda

## Links Relacionados
- [[HTML-Elementos-Estruturais]]
- [[HTML-Elementos-Textuais]]