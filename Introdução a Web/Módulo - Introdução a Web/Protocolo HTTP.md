## Hypertext Transfer Protocol (HTTP)

### Tradução

**HTTP** significa **Protocolo de Transferência de Hipertexto**.

### O que é HTTP

HTTP é um **protocolo usado para comunicação na Web**.  
Neste exato momento, esta conversa acontece sobre **HTTP/HTTPS**, que é um dos protocolos mais utilizados no mundo.

O HTTP funciona sempre como uma comunicação entre:

- **Cliente** (browser, curl, netcat, aplicativo)
    
- **Servidor** (site, API, aplicação web)
    

---

## Comunicação HTTP (visão geral)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20210905091508/ImageOfHTTPRequestResponse-660x374.png)

![Image](https://hackernoon.imgix.net/images/jot3yv6.jpg)

![Image](https://www.researchgate.net/publication/369358390/figure/fig1/AS%3A11431281127810255%401679180216268/HTTP-request-and-response-flow.png)

Fluxo básico:

```
Cliente  →  HTTP Request  →  Servidor
Cliente  ←  HTTP Response ←  Servidor
```

---

## HTTP Request e HTTP Response

### HTTP Request (requisição)

É a mensagem enviada pelo **cliente** ao servidor.

Exemplo de ações:

- Acessar um site
    
- Enviar um formulário
    
- Buscar dados de uma API
    

### HTTP Response (resposta)

É a mensagem enviada pelo **servidor** ao cliente, contendo:

- Código de status
    
- Cabeçalhos
    
- Conteúdo (HTML, JSON, imagem, etc.)
    

---

## Estrutura de uma requisição HTTP (Request)

Uma requisição HTTP é composta por **linhas de texto**.

### Estrutura correta

1. **Request Line** (linha da requisição)
    
2. **Headers** (cabeçalhos – várias linhas)
    
3. **Linha vazia**
    
4. **Body** (corpo da mensagem – opcional)
    

A **linha vazia** serve para **separar os headers do body**.  
Ela **não é o body**. O body vem **depois** da linha vazia.

---

### Exemplo de HTTP Request (GET)

```
GET / HTTP/1.1
Host: www.google.com
User-Agent: Mozilla/5.0
Accept: text/html
Connection: close

```

Explicação:

- Linha 1 → método, caminho e versão do HTTP
    
- Linhas seguintes → headers
    
- Linha vazia → fim dos headers
    
- Não há body em requisições GET comuns
    

---

## Estrutura de uma resposta HTTP (Response)

### Exemplo de HTTP Response

```
HTTP/1.1 200 OK
Date: Tue, 15 Jan 2026 18:30:00 GMT
Server: gws
Content-Type: text/html; charset=UTF-8
Content-Length: 1256

<html>
  <body>
    Conteúdo da página
  </body>
</html>
```

Explicação:

- Linha 1 → status HTTP
    
- Headers → informações da resposta
    
- Linha vazia → separação
    
- Body → conteúdo retornado
    

---

## HTTP Headers

Headers são **metadados** usados na comunicação.

Exemplos comuns:

- `Host`
    
- `User-Agent`
    
- `Content-Type`
    
- `Authorization`
    
- `Cookie`
    
- `Accept`
    

Eles controlam autenticação, tipo de conteúdo, cache, sessão e segurança.

---

## Netcat (nc)

### O que é Netcat

Netcat é uma ferramenta de rede usada para:

- Abrir conexões TCP/UDP
    
- Testar serviços
    
- Fazer requisições manuais
    
- Debug de protocolos (HTTP, SMTP, etc.)
    

Muito usada em **pentest** e **análise de rede**.

---

### Instalação do Netcat

**Debian / Ubuntu**

```
sudo apt update
sudo apt install netcat -y
```

**CentOS / Rocky / AlmaLinux**

```
sudo yum install nc -y
```

ou

```
sudo dnf install nc -y
```

**Arch Linux**

```
sudo pacman -S openbsd-netcat
```

---

## Exemplo prático: HTTP usando Netcat

### Conectando ao Google (porta 80)

```
nc www.google.com 80
```

Depois de conectar, digite manualmente a requisição HTTP:

```
GET / HTTP/1.1
Host: www.google.com
Connection: close

```

Após pressionar Enter duas vezes, o servidor responde com o **HTTP Response** completo.

![Image](https://user-images.githubusercontent.com/4745789/63222769-9c841580-c1c9-11e9-8593-7289b2a40a20.jpg)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240109230411/Screenshot-2024-01-09-230321.png)

![Image](https://www.varonis.com/hubfs/Imported_Blog_Media/netcat-commands-port-scan-2.png?hsLang=en)

Esse exemplo mostra claramente como o HTTP funciona **sem navegador**.

---

## Console do Desenvolvedor (Browser)

Nos navegadores modernos, o **Console do Desenvolvedor** é essencial para análise web.

A aba mais utilizada em segurança e debugging é:

### Network

![Image](https://developer.chrome.com/static/docs/devtools/network/image/the-filters-toolbar.png)

![Image](https://developer.chrome.com/static/docs/devtools/network/reference/image/search-requests.png)

![Image](https://firefox-source-docs.mozilla.org/_images/network_monitor_closeup.png)

Nela é possível ver:

- Todas as requisições HTTP/HTTPS
    
- Headers de request e response
    
- Cookies
    
- Tokens
    
- Parâmetros
    
- Payloads
    
- Status codes
    

É uma das principais ferramentas em **pentest web**.

---

## Portas padrão

- **HTTP** → porta **80**
    
- **HTTPS** → porta **443**
    

HTTPS é HTTP com **camada de criptografia TLS**.

---

## Resumo direto

- HTTP é um protocolo cliente ↔ servidor
    
- Funciona por request e response
    
- Usa headers e, opcionalmente, body
    
- Netcat permite ver o HTTP “cru”
    
- Network do navegador mostra todas as requisições
    
- Porta 80 → HTTP
    
- Porta 443 → HTTPS
