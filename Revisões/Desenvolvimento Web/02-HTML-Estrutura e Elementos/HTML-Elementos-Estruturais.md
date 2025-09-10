#html #semantica #estrutura #layout

## Layout Principal
```html
<header>Cabeçalho da página/seção</header>
<nav>Navegação</nav>
<main>Conteúdo principal (único por página)</main>
<section>Seção de conteúdo</section>
<article>Conteúdo independente</article>
<aside>Conteúdo lateral/complementar</aside>
<footer>Rodapé</footer>
```

## Estrutura Típica
```html
<!DOCTYPE html>
<html>
<head>...</head>
<body>
    <header>
        <nav>Menu principal</nav>
    </header>
    <main>
        <section>
            <article>
	            <header>
		            <h1>Título</h1>
	            </header>
	            
	            <p>
		            Parágrafo
	            </p>
            </article>
            
            <article>Artigo 2</article>
        </section>
        <aside>Barra Lateral</aside>
    </main>
    <footer>Rodapé</footer>
</body>
</html>
```

## Conteúdo Expansível
```html
<details>
    <summary>Clique para expandir</summary>
    <p>Conteúdo que fica oculto até ser solicitado</p>
</details>
```

## Incorporação Externa
```html
<iframe src="https://exemplo.com" width="600" height="400"></iframe>
```

## 📌 Dicas Importantes
- **Prefira elementos semânticos** (`header`, `main`, `section`, etc.) a `div` sempre que possível
- **O `main`** deve conter o conteúdo central, e **só pode existir um por página**
- **O `aside`** é perfeito para conteúdo lateral ou complementar
- **`iframe`** permite integrar conteúdos externos, mas deve ser usado com cuidado por questões de **segurança e performance**

## Links Relacionados
- [[HTML-Listas]]
- [[HTML-Estrutura-Geral]]