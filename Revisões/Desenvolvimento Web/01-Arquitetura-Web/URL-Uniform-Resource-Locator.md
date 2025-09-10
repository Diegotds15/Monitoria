#url #web #componentes

## Estrutura da URL

```
http://www.exemplo.com.br:80/pasta1/carregar.html?user=123&p1=AAA#secao2
```

| Parte                   | Nome Técnico     | Função                                  |
| ----------------------- | ---------------- | --------------------------------------- |
| `http`                  | Scheme           | Define o protocolo de comunicação       |
| `://`                   | Scheme Separator | Indica o fim do esquema                 |
| `www.exemplo.com.br`    | Host             | Nome do servidor (domínio ou IP)        |
| `:80`                   | Port             | Porta de rede (HTTP=80, HTTPS=443)      |
| `/pasta1/carregar.html` | Path             | Caminho até o recurso específico        |
| `?user=123&p1=AAA`      | Query String     | Parâmetros adicionais                   |
| `#secao2`               | Anchor           | Referência a ponto específico da página |

## ⚠️ Importante
- `www` é um subdomínio
- `www.exemplo.com.br` é **diferente** de `exemplo.com.br`

## Links Relacionados
- [[HTTP-HyperText-Transfer-Protocol]]
- [[Arquitetura-Web-Visao-Geral]]
