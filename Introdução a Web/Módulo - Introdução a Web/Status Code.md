### O que é “status code”?

**Status code** é um **número na resposta HTTP**.  
Ele diz o resultado da sua requisição. ([MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status?utm_source=chatgpt.com "Códigos de status de respostas HTTP - MDN Web Docs"))

Ele aparece na primeira linha, por exemplo:

```http
HTTP/1.1 200 OK
```

---

## “Imagem” (explicação visual)

```
CLIENTE (front-end)                        SERVIDOR (back-end)
      |  Requisição HTTP                         |
      |----------------------------------------->|
      |                                          |
      |  Resposta HTTP: 200 / 404 / 500 ...      |
      |<-----------------------------------------|
           ^ aqui fica o status code
```

---

## Classes (faixas) de status code

- **200–299**: sucesso. ([MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status?utm_source=chatgpt.com "Códigos de status de respostas HTTP - MDN Web Docs"))
    
- **300–399**: redirecionamento. ([MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status?utm_source=chatgpt.com "Códigos de status de respostas HTTP - MDN Web Docs"))
    
- **400–499**: erro do cliente (requisição errada, sem login, sem permissão). ([W3C](https://www.w3.org/Protocols/HTTP/HTRESP.html?utm_source=chatgpt.com "Status codes in HTTP"))
    
- **500–599**: erro do servidor (falha interna). ([W3C](https://www.w3.org/Protocols/HTTP/HTRESP.html?utm_source=chatgpt.com "Status codes in HTTP"))
    

Exemplos visuais (bem direto):

**200 OK**

```http
HTTP/1.1 200 OK
```

**301 Redirect**

```http
HTTP/1.1 301 Moved Permanently
Location: /novo
```

**404 Not Found**

```http
HTTP/1.1 404 Not Found
```

**500 Internal Server Error**

```http
HTTP/1.1 500 Internal Server Error
```

---

## Pra que serve isso?

Serve para você saber:

- Se deu certo.
    
- Se precisa redirecionar.
    
- Se o erro foi seu (4xx).
    
- Se o erro foi do servidor (5xx). ([MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status?utm_source=chatgpt.com "Códigos de status de respostas HTTP - MDN Web Docs"))
    

---

## Usando isso em descoberta de diretórios / fuzzing (somente com autorização)

Em **content discovery**, a ferramenta tenta vários caminhos e analisa respostas. ([portswigger.net](https://portswigger.net/burp/documentation/desktop/tools/engagement-tools/content-discovery?utm_source=chatgpt.com "Content discovery"))

O que costuma chamar atenção:

- **200**: existe.
    
- **301/302**: existe e redireciona.
    
- **403**: existe, mas bloqueado.
    
- **404**: não existe.
    

Mas tem armadilhas:

- Site que retorna **200 para tudo** (404 “falso”).
    
- Resposta “igual” para muitas URLs.
    

Por isso a ferramenta filtra por:

- **status code**
    
- **tamanho**
    
- **palavras**
    
- **linhas** ([GitHub](https://github.com/ffuf/ffuf?utm_source=chatgpt.com "ffuf/ffuf: Fast web fuzzer written in Go"))
    

---

## Estudos para ler depois

- MDN: códigos de status HTTP (PT e EN). ([MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Status?utm_source=chatgpt.com "Códigos de status de respostas HTTP - MDN Web Docs"))
    
- IANA: lista oficial de códigos. ([iana.org](https://www.iana.org/assignments/http-status-codes?utm_source=chatgpt.com "Hypertext Transfer Protocol (HTTP) Status Code Registry"))
    
- RFC 9110: semântica do HTTP (oficial). ([IETF Datatracker](https://datatracker.ietf.org/doc/html/rfc9110?utm_source=chatgpt.com "RFC 9110 - HTTP Semantics - Datatracker - IETF"))
    
- OWASP WSTG: fuzzing (base de metodologia). ([owasp.org](https://owasp.org/www-project-web-security-testing-guide/latest/6-Appendix/C-Fuzzing?utm_source=chatgpt.com "WSTG: Appendix C - Fuzzing"))
    
- PortSwigger/Burp: content discovery. ([portswigger.net](https://portswigger.net/burp/documentation/desktop/tools/engagement-tools/content-discovery?utm_source=chatgpt.com "Content discovery"))
    

Se você quiser, eu monto um “resumo de bolso” com:

- os 15 códigos mais usados (200, 201, 204, 301, 302, 304, 400, 401, 403, 404, 405, 409, 415, 429, 500, 503)
    
- quando usar cada um
    
- e um mini exercício de leitura de respostas HTTP.