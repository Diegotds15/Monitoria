#http #metodos #codigos-resposta #versoes

## Métodos Comuns do HTTP

| Método | Ícone | Função                                     |
| ------ | ----- | ------------------------------------------ |
| GET    | 📥    | Buscar recurso no servidor                 |
| POST   | 📨    | Enviar dados para o servidor               |
| PUT    | ✏️    | Atualizar recurso por completo no servidor |
| DELETE | 🗑️   | Remover recurso do servidor                |

## Códigos de Resposta

- **1xx** – Informativo
- **2xx** – Sucesso (200)
- **3xx** – Redirecionamento  
- **4xx** – Erro do cliente (404)
- **5xx** – Erro do servidor

## Versões do HTTP

| Aspecto           | HTTP/1.1                           | HTTP/2                                | HTTP/3                  |
| ----------------- | ---------------------------------- | ------------------------------------- | ----------------------- |
| **Ano**           | 1997                               | 2015                                  | 2022 (em adoção)        |
| **Transporte**    | TCP                                | TCP                                   | QUIC (baseado em UDP)   |
| **Multiplexação** | Não (uma conexão = uma requisição) | Sim (múltiplas requisições paralelas) | Sim, com menos latência |
| **Cabeçalhos**    | Texto simples                      | Comprimidos (HPACK)                   | Comprimidos (QPACK)     |
| **Latência**      | Alta (bloqueio)                    | Reduzida                              | Ainda menor             |
| **Conexões**      | Várias conexões TCP                | Uma única conexão TCP                 | Uma única conexão QUIC  |

## Links Relacionados
- [[Servidor-Web]]
- [[URL-Uniform-Resource-Locator]]
- [[Arquitetura-Web-Visao-Geral]]
