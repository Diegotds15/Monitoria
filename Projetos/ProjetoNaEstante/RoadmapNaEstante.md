# ROADMAP SIMPLIFICADO - Biblioteca Digital

## 📚 Visão Geral do Projeto

Um sistema básico para upload e visualização de livros PDF com foco no aprendizado de desenvolvimento web e modelagem de banco de dados.

**Funcionalidades Core:**
- Upload de livros PDF
- Visualização em lista
- Leitor PDF básico
- Organização por categorias

**Stack Tecnológica:**
- Backend: Python + FastAPI
- Frontend: HTML + CSS + JavaScript
- Banco: MySQL (sem ORM)
- Leitor: PDF.js

---

## 🎯 ETAPA 1: ANÁLISE DE REQUISITOS

### O que o sistema precisa fazer?

#### Requisitos Funcionais
1. **Gerenciar Livros**
   - Usuário pode fazer upload de arquivos PDF
   - Cada livro tem: título, autor, categoria, arquivo PDF
   - Sistema mostra lista de todos os livros
   - Usuário pode abrir livro para leitura

2. **Categorizar Livros**
   - Livros podem ter categorias (Ficção, Técnico, etc.)
   - Usuário pode filtrar livros por categoria

3. **Ler Livros**
   - Visualizar PDF no navegador
   - Navegar entre páginas

#### Requisitos Não-Funcionais
- Interface simples e funcional
- Arquivos até 10MB
- Funciona em navegadores modernos

### Perguntas para Análise
- Que informações são essenciais para um livro?
- Como organizar os livros?
- Onde armazenar os arquivos PDF?
- Como relacionar livros e categorias?

---

## 🧠 ETAPA 2: MODELAGEM DE BANCO DE DADOS

### 2.1 Modelagem Conceitual

**Entidades Identificadas:**
- LIVRO: representa um livro na biblioteca
- CATEGORIA: representa uma categoria/gênero

**Relacionamentos:**
- Um livro PERTENCE a uma categoria
- Uma categoria PODE TER vários livros

```
LIVRO -----(pertence)-----> CATEGORIA
  |                            |
  |                            |
(muitos)                    (uma)
```

### 2.2 Modelagem Lógica

#### Entidade: LIVRO
- **Identificador**: ID único
- **Atributos**: título, autor, arquivo_path, data_upload
- **Relacionamento**: categoria_id (chave estrangeira)

#### Entidade: CATEGORIA  
- **Identificador**: ID único
- **Atributos**: nome, descrição

#### Relacionamento: LIVRO → CATEGORIA
- **Tipo**: N:1 (muitos para um)
- **Cardinalidade**: Um livro tem exatamente uma categoria
- **Implementação**: chave estrangeira categoria_id na tabela livros

### 2.3 Modelagem Física (MySQL)

#### Exercício Prático: Criando as Tabelas

**Passo 1: Criar banco de dados**
```sql
CREATE DATABASE biblioteca_digital;
USE biblioteca_digital;
```

**Passo 2: Tabela categorias (primeiro, pois será referenciada)**
```sql
CREATE TABLE categorias (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL UNIQUE,
    descricao TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**Passo 3: Tabela livros**
```sql
CREATE TABLE livros (
    id INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(255) NOT NULL,
    autor VARCHAR(255) NOT NULL,
    arquivo_path VARCHAR(500) NOT NULL,
    categoria_id INT NOT NULL,
    data_upload TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    
    FOREIGN KEY (categoria_id) REFERENCES categorias(id)
);
```

**Passo 4: Inserir categorias padrão**
```sql
INSERT INTO categorias (nome, descricao) VALUES 
('Ficção', 'Livros de ficção literária'),
('Técnico', 'Livros técnicos e manuais'),
('Biografia', 'Biografias e autobiografias'),
('História', 'Livros de história'),
('Ciência', 'Livros científicos');
```

### 2.4 Exercícios de Modelagem

**Exercício 1**: Adicione uma tabela para armazenar o progresso de leitura
- Que informações são necessárias?
- Como relacionar com livros?

**Exercício 2**: Como você modelaria se um livro pudesse ter múltiplas categorias?
- Que tipo de relacionamento seria?
- Quantas tabelas seriam necessárias?

---

## 🏗️ ETAPA 3: ESTRUTURA DO PROJETO

### Organização dos Arquivos
```
biblioteca-digital/
├── backend/
│   ├── main.py              # Aplicação principal
│   ├── database.py          # Conexão com banco
│   ├── models.py            # Consultas SQL
│   ├── uploads/             # Arquivos enviados
│   └── requirements.txt     # Dependências
├── frontend/
│   ├── index.html           # Página principal
│   ├── upload.html          # Upload de livros
│   ├── reader.html          # Leitor PDF
│   ├── style.css           # Estilos
│   └── script.js           # JavaScript
└── database.sql            # Script de criação do BD
```

---

## 🔧 ETAPA 4: BACKEND PASSO A PASSO

### 4.1 Configuração Inicial

**Passo 1: Instalar dependências**
```bash
pip install fastapi uvicorn pymysql
```

**Passo 2: Conectar com banco de dados**
```python
# database.py
import pymysql

def get_connection():
    return pymysql.connect(
        host='localhost',
        user='seu_usuario',
        password='sua_senha',
        database='biblioteca_digital',
        charset='utf8mb4'
    )

def test_connection():
    try:
        conn = get_connection()
        print("Conexão estabelecida!")
        conn.close()
        return True
    except Exception as e:
        print(f"Erro na conexão: {e}")
        return False
```

### 4.2 Operações Básicas no Banco

**Passo 3: Criar funções para categorias**
```python
# models.py
from database import get_connection

def get_all_categories():
    conn = get_connection()
    cursor = conn.cursor()
    
    cursor.execute("SELECT id, nome, descricao FROM categorias ORDER BY nome")
    categories = cursor.fetchall()
    
    cursor.close()
    conn.close()
    
    return categories

def get_category_by_id(category_id):
    conn = get_connection()
    cursor = conn.cursor()
    
    cursor.execute("SELECT id, nome, descricao FROM categorias WHERE id = %s", (category_id,))
    category = cursor.fetchone()
    
    cursor.close()
    conn.close()
    
    return category
```

**Passo 4: Criar funções para livros**
```python
def insert_book(titulo, autor, arquivo_path, categoria_id):
    conn = get_connection()
    cursor = conn.cursor()
    
    sql = "INSERT INTO livros (titulo, autor, arquivo_path, categoria_id) VALUES (%s, %s, %s, %s)"
    cursor.execute(sql, (titulo, autor, arquivo_path, categoria_id))
    
    book_id = cursor.lastrowid
    conn.commit()
    
    cursor.close()
    conn.close()
    
    return book_id

def get_all_books():
    conn = get_connection()
    cursor = conn.cursor()
    
    sql = """
    SELECT l.id, l.titulo, l.autor, l.arquivo_path, l.data_upload, 
           c.nome as categoria_nome
    FROM livros l 
    JOIN categorias c ON l.categoria_id = c.id 
    ORDER BY l.data_upload DESC
    """
    
    cursor.execute(sql)
    books = cursor.fetchall()
    
    cursor.close()
    conn.close()
    
    return books
```

### 4.3 API REST Básica

**Passo 5: Criar endpoints**
```python
# main.py
from fastapi import FastAPI, UploadFile, File, Form
from fastapi.staticfiles import StaticFiles
import models
import os

app = FastAPI()

# Servir arquivos estáticos
app.mount("/uploads", StaticFiles(directory="uploads"), name="uploads")

@app.get("/")
def home():
    return {"message": "Biblioteca Digital API"}

@app.get("/categorias")
def listar_categorias():
    return models.get_all_categories()

@app.get("/livros")
def listar_livros():
    return models.get_all_books()

@app.post("/upload")
async def upload_livro(
    titulo: str = Form(...),
    autor: str = Form(...),
    categoria_id: int = Form(...),
    arquivo: UploadFile = File(...)
):
    # Salvar arquivo
    file_path = f"uploads/{arquivo.filename}"
    with open(file_path, "wb") as f:
        content = await arquivo.read()
        f.write(content)
    
    # Inserir no banco
    book_id = models.insert_book(titulo, autor, file_path, categoria_id)
    
    return {"message": "Livro enviado!", "id": book_id}
```

---

## 🎨 ETAPA 5: FRONTEND PASSO A PASSO

### 5.1 HTML Estrutural

**Passo 1: Página principal básica**
```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Biblioteca Digital</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>📚 Biblioteca Digital</h1>
        <nav>
            <a href="index.html">Início</a>
            <a href="upload.html">Adicionar Livro</a>
        </nav>
    </header>
    
    <main>
        <section id="filtros">
            <select id="filtroCategoria">
                <option value="">Todas as categorias</option>
            </select>
        </section>
        
        <section id="livros">
            <!-- Livros serão carregados aqui -->
        </section>
    </main>

    <script src="script.js"></script>
</body>
</html>
```

### 5.2 CSS Simples e Funcional

**Passo 2: Estilos básicos**
```css
/* style.css */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    color: #333;
}

header {
    background-color: #2c3e50;
    color: white;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

nav a {
    color: white;
    text-decoration: none;
    margin-left: 1rem;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    transition: background-color 0.3s;
}

nav a:hover {
    background-color: rgba(255, 255, 255, 0.1);
}

main {
    max-width: 1200px;
    margin: 2rem auto;
    padding: 0 1rem;
}

.livro-card {
    background: white;
    border-radius: 8px;
    padding: 1rem;
    margin-bottom: 1rem;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    cursor: pointer;
    transition: transform 0.2s;
}

.livro-card:hover {
    transform: translateY(-2px);
}
```

### 5.3 JavaScript Progressivo

**Passo 3: Conectar com API**
```javascript
// script.js

// Configuração da API
const API_URL = 'http://localhost:8000';

// Função para fazer requisições
async function apiRequest(endpoint, options = {}) {
    try {
        const response = await fetch(`${API_URL}${endpoint}`, options);
        return await response.json();
    } catch (error) {
        console.error('Erro na API:', error);
        throw error;
    }
}

// Carregar categorias
async function carregarCategorias() {
    const categorias = await apiRequest('/categorias');
    const select = document.getElementById('filtroCategoria');
    
    categorias.forEach(categoria => {
        const option = document.createElement('option');
        option.value = categoria[0]; // id
        option.textContent = categoria[1]; // nome
        select.appendChild(option);
    });
}

// Carregar livros
async function carregarLivros() {
    const livros = await apiRequest('/livros');
    const container = document.getElementById('livros');
    
    container.innerHTML = '';
    
    livros.forEach(livro => {
        const div = document.createElement('div');
        div.className = 'livro-card';
        div.innerHTML = `
            <h3>${livro[1]}</h3>
            <p><strong>Autor:</strong> ${livro[2]}</p>
            <p><strong>Categoria:</strong> ${livro[5]}</p>
            <p><small>Adicionado em: ${new Date(livro[4]).toLocaleDateString()}</small></p>
        `;
        div.onclick = () => abrirLivro(livro[0]);
        container.appendChild(div);
    });
}

// Abrir livro para leitura
function abrirLivro(id) {
    window.location.href = `reader.html?id=${id}`;
}

// Inicializar página
document.addEventListener('DOMContentLoaded', () => {
    carregarCategorias();
    carregarLivros();
});
```

---

## 📤 ETAPA 6: IMPLEMENTANDO UPLOAD

### 6.1 Página de Upload

**Passo 1: Criar formulário**
```html
<!-- upload.html -->
<main>
    <h2>Adicionar Novo Livro</h2>
    
    <form id="uploadForm">
        <div>
            <label for="titulo">Título:</label>
            <input type="text" id="titulo" required>
        </div>
        
        <div>
            <label for="autor">Autor:</label>
            <input type="text" id="autor" required>
        </div>
        
        <div>
            <label for="categoria">Categoria:</label>
            <select id="categoria" required>
                <option value="">Selecione...</option>
            </select>
        </div>
        
        <div>
            <label for="arquivo">Arquivo PDF:</label>
            <input type="file" id="arquivo" accept=".pdf" required>
        </div>
        
        <button type="submit">Enviar Livro</button>
    </form>
    
    <div id="progresso" style="display: none;">
        <p>Enviando...</p>
        <div class="barra-progresso">
            <div id="barra"></div>
        </div>
    </div>
</main>
```

**Passo 2: JavaScript do upload**
```javascript
// Adicionar ao script.js

async function enviarLivro(event) {
    event.preventDefault();
    
    const formData = new FormData();
    formData.append('titulo', document.getElementById('titulo').value);
    formData.append('autor', document.getElementById('autor').value);
    formData.append('categoria_id', document.getElementById('categoria').value);
    formData.append('arquivo', document.getElementById('arquivo').files[0]);
    
    try {
        document.getElementById('progresso').style.display = 'block';
        
        const response = await fetch(`${API_URL}/upload`, {
            method: 'POST',
            body: formData
        });
        
        const result = await response.json();
        alert('Livro enviado com sucesso!');
        window.location.href = 'index.html';
        
    } catch (error) {
        alert('Erro ao enviar livro: ' + error.message);
    }
}

// No DOMContentLoaded da página upload
document.getElementById('uploadForm').addEventListener('submit', enviarLivro);
```

---

## 📖 ETAPA 7: LEITOR PDF

### 7.1 Implementação Básica

**Passo 1: Estrutura do leitor**
```html
<!-- reader.html -->
<main>
    <div id="controles">
        <button onclick="history.back()">← Voltar</button>
        <button onclick="paginaAnterior()">Anterior</button>
        <span id="pagina-info">Página 1 de 1</span>
        <button onclick="proximaPagina()">Próxima</button>
    </div>
    
    <div id="pdf-container">
        <canvas id="pdf-canvas"></canvas>
    </div>
</main>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
```

**Passo 2: JavaScript do leitor**
```javascript
// reader.js (arquivo separado)
let pdfDoc = null;
let paginaAtual = 1;
let totalPaginas = 0;

async function carregarPDF() {
    const urlParams = new URLSearchParams(window.location.search);
    const livroId = urlParams.get('id');
    
    // Buscar informações do livro
    const livro = await apiRequest(`/livro/${livroId}`);
    const pdfUrl = `${API_URL}/${livro.arquivo_path}`;
    
    // Carregar PDF
    pdfDoc = await pdfjsLib.getDocument(pdfUrl).promise;
    totalPaginas = pdfDoc.numPages;
    
    mostrarPagina(1);
}

async function mostrarPagina(num) {
    const page = await pdfDoc.getPage(num);
    const viewport = page.getViewport({scale: 1.5});
    
    const canvas = document.getElementById('pdf-canvas');
    const context = canvas.getContext('2d');
    
    canvas.height = viewport.height;
    canvas.width = viewport.width;
    
    await page.render({
        canvasContext: context,
        viewport: viewport
    }).promise;
    
    paginaAtual = num;
    document.getElementById('pagina-info').textContent = `Página ${num} de ${totalPaginas}`;
}

function proximaPagina() {
    if (paginaAtual < totalPaginas) {
        mostrarPagina(paginaAtual + 1);
    }
}

function paginaAnterior() {
    if (paginaAtual > 1) {
        mostrarPagina(paginaAtual - 1);
    }
}

// Inicializar
document.addEventListener('DOMContentLoaded', carregarPDF);
```

---

## 🎓 EXERCÍCIOS PRÁTICOS

### Exercício 1: Melhorar a Busca
Implemente busca por título e autor:
```sql
SELECT * FROM livros 
WHERE titulo LIKE '%termo%' OR autor LIKE '%termo%'
```

### Exercício 2: Contadores
Adicione na página inicial:
- Total de livros
- Livros por categoria
```sql
SELECT c.nome, COUNT(l.id) as total 
FROM categorias c 
LEFT JOIN livros l ON c.id = l.categoria_id 
GROUP BY c.id
```

### Exercício 3: Validações
Implemente no backend:
- Verificar se arquivo é PDF
- Limitar tamanho do arquivo
- Validar campos obrigatórios

### Exercício 4: Melhorias na Interface
- Adicionar ícones
- Melhorar layout responsivo
- Adicionar loading states

---

## 📝 PRÓXIMOS PASSOS

### Funcionalidades Avançadas (Opcional)
1. **Sistema de Favoritos**
   - Nova tabela: favoritos (user_id, book_id)
   - Botão de favoritar na interface

2. **Progresso de Leitura**
   - Tabela: progresso_leitura (livro_id, pagina_atual, total_paginas)
   - Barra de progresso visual

3. **Busca Avançada**
   - Filtros combinados
   - Ordenação por data, título, autor

### Melhorias Técnicas
- Tratamento de erros mais robusto
- Validação no frontend
- Upload com drag & drop
- Preview da capa do livro
- Zoom no leitor PDF

---

## 🔍 CONCEITOS APRENDIDOS

### Banco de Dados
- Análise de requisitos
- Modelagem conceitual, lógica e física
- Relacionamentos (1:N)
- Chaves primárias e estrangeiras
- Consultas SQL com JOIN

### Backend
- API REST com FastAPI
- Conexão com banco sem ORM
- Upload de arquivos
- Servir arquivos estáticos

### Frontend
- HTML semântico
- CSS responsivo básico
- JavaScript assíncrono
- Integração com APIs
- Manipulação do DOM

### Integração
- Comunicação frontend-backend
- Tratamento de erros
- Fluxo de dados completo

Este roadmap simplificado permite focar no aprendizado dos conceitos fundamentais enquanto constrói um projeto funcional!