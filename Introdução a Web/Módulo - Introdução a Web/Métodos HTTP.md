# Como o Front-end se comunica com o Back-end (HTTP e Métodos)

## O que você vai ver

- Fluxo de **requisição** e **resposta**
    
- Tecnologias típicas de **front-end** e **back-end**
    
- Métodos HTTP: **GET, POST, PUT, PATCH, DELETE**
    
- Exemplos completos (ex.: formulário de e-mail → **POST**)
    
- Boas práticas: status code, headers, auth, CORS
    
- Referências “acadêmicas” (RFCs e documentação)
    

---

## 1) Visão geral da comunicação

Na Web, o padrão mais comum é:

1. O **front-end** (no navegador ou app) envia uma **requisição HTTP** para uma URL do **back-end**
    
2. O **back-end** processa (valida dados, executa regras, consulta banco/serviços)
    
3. O back-end devolve uma **resposta HTTP** para o front-end
    

O HTTP é um protocolo **stateless** (sem estado): cada requisição deve carregar o contexto necessário para o servidor entender o que fazer (por exemplo, token, cookies, headers, etc.). ([IETF Datatracker](https://datatracker.ietf.org/doc/html/rfc9110?utm_source=chatgpt.com "RFC 9110 - HTTP Semantics - Datatracker - IETF"))

### Diagrama (texto)

```
[Front-end (Browser/App)]
        |
        |  Requisição HTTP (Método + URL + Headers + Body)
        v
[Back-end (Servidor/API)] -----> [Banco de Dados / Serviços externos]
        ^
        |  Resposta HTTP (Status + Headers + Body)
        |
[Front-end (Browser/App)]
```

### Componentes típicos de uma requisição HTTP

- **Método** (GET/POST/PUT/PATCH/DELETE, etc.)
    
- **URL** (ex.: [https://api.exemplo.com/usuarios/123](https://api.exemplo.com/usuarios/123))
    
- **Headers** (ex.: Authorization, Content-Type, Accept, Cookie...)
    
- **Body** (quando faz sentido: JSON, form-data, etc.)
    

### Componentes típicos de uma resposta HTTP

- **Status code** (200, 201, 400, 401, 404, 500…)
    
- **Headers** (Content-Type, Cache-Control, Set-Cookie…)
    
- **Body** (dados retornados, geralmente JSON em APIs)
    

---

## 2) Tecnologias típicas (Front-end vs Back-end)

O front-end roda no **cliente** (navegador/app).  
O back-end roda no **servidor** (API/serviços).  
Quem conecta os dois é o **HTTP/HTTPS**.

### Diagrama (texto)

```
Front-end (cliente)  <---- HTTP/HTTPS ---->  Back-end (servidor)
```

### Front-end (cliente) — exemplos de tecnologias

- Linguagens/base: **HTML, CSS, JavaScript, TypeScript**
    
- Frameworks: **React, Angular, Vue, Svelte**
    
- SSR/SPA: **Next.js, Nuxt, Remix**
    
- UI: **Tailwind, Bootstrap, Material UI**
    
- Estado: **Redux, Zustand, Pinia, NgRx**
    
- Cliente HTTP: **fetch**, **Axios**
    
- Autenticação no cliente: **Cookies**, **JWT** (enviado via HTTP)
    
- Build/tooling: **Vite, Webpack, Babel**
    

### Back-end (servidor) — exemplos de tecnologias

- Estilos de API: **REST**, **GraphQL**, **gRPC (sobre HTTP/HTTPS)**
    
- Node.js: **Express, NestJS**
    
- Python: **FastAPI, Django, Flask**
    
- Java: **Spring Boot**
    
- C#: **ASP.NET Core**
    
- PHP: **Laravel, Symfony**
    
- Bancos: **PostgreSQL, MySQL, MongoDB, Redis**
    
- Infra: **Nginx, Docker, Kubernetes, Cloud**
    

---

## 3) Métodos HTTP (o que cada um faz)

Os métodos definem a “intenção” da operação.  
A mesma URL pode ter comportamento diferente dependendo do método.

Exemplo:

- `GET /usuarios` → listar usuários
    
- `POST /usuarios` → criar usuário
    

### Tabela prática (GET/POST/PUT/PATCH/DELETE)

**GET**

- Ideia: **ler/buscar** dados de um recurso
    
- Ex.: `GET /api/usuarios/123`
    
- Por definição: GET “recupera a informação identificada pela Request-URI” ([W3C](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html?utm_source=chatgpt.com "HTTP/1.1: Method Definitions"))
    
- “Requests using GET should only retrieve data” (documentação prática) ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods?utm_source=chatgpt.com "HTTP request methods - MDN Web Docs"))
    

**POST**

- Ideia: **enviar dados** para o servidor para criar algo ou disparar um processamento
    
- Ex.: `POST /api/newsletter` com `{ "email": "..." }`
    
- Normalmente **não é idempotente** (mandar duas vezes pode criar duas entradas)
    

**PUT**

- Ideia: **criar ou substituir completamente** a representação do recurso
    
- Ex.: `PUT /api/usuarios/123` com o objeto completo do usuário
    
- “PUT … creates a new resource or replaces a representation of the target resource” ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PUT?utm_source=chatgpt.com "PUT request method - HTTP - MDN Web Docs - Mozilla"))
    
- PUT é tipicamente **idempotente** ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PUT?utm_source=chatgpt.com "PUT request method - HTTP - MDN Web Docs - Mozilla"))
    

**PATCH**

- Ideia: **atualização parcial** do recurso (só o que mudou)
    
- Ex.: `PATCH /api/usuarios/123` com `{ "email": "novo@..." }`
    
- RFC define PATCH como método para “partial modifications to a resource” ([RFC Editor](https://www.rfc-editor.org/rfc/rfc5789.html?utm_source=chatgpt.com "RFC 5789: PATCH Method for HTTP"))
    
- MDN também descreve PATCH como “modificações parciais” ([MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Reference/Methods/PATCH?utm_source=chatgpt.com "PATCH - HTTP - MDN Web Docs"))
    

**DELETE**

- Ideia: **remover** um recurso
    
- Ex.: `DELETE /api/usuarios/123`
    
- DELETE normalmente é **idempotente** (apagar 1 vez ou 10 vezes gera o mesmo “estado final”: não existe) ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/DELETE?utm_source=chatgpt.com "DELETE request method - HTTP - MDN Web Docs"))
    

### Conceitos importantes (rápido e útil)

- **Safe (seguro):** não deveria causar efeito colateral no servidor (GET/HEAD são os clássicos) ([W3C](https://www.w3.org/Protocols/rfc2616/rfc2616.html?utm_source=chatgpt.com "Hypertext Transfer Protocol -- HTTP/1.1"))
    
- **Idempotente:** repetir a mesma operação várias vezes dá o mesmo efeito que executar uma vez (PUT/DELETE geralmente são) ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods/PUT?utm_source=chatgpt.com "PUT request method - HTTP - MDN Web Docs - Mozilla"))
    

---

## 4) Exemplos práticos (completos)

A seguir você vai ver claramente:

- método
    
- rota (URL)
    
- headers
    
- body
    
- resposta
    

### 4.1) Exemplo POST (formulário de e-mail / newsletter)

**Cenário:**  
Na página tem um campo de e-mail e um botão “Cadastrar”.  
Quando clica, o front-end envia o e-mail para o back-end.

#### Front-end (JavaScript) usando fetch

```js
// Exemplo simples: POST /api/newsletter
async function cadastrarEmail(email) {
  const resp = await fetch("/api/newsletter", {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "Accept": "application/json"
    },
    body: JSON.stringify({ email })
  });

  if (!resp.ok) {
    const erro = await resp.json().catch(() => ({}));
    throw new Error(erro.message || "Falha ao cadastrar e-mail");
  }

  return resp.json();
}
```

#### Requisição HTTP (visão “linha a linha”)

```http
POST /api/newsletter HTTP/1.1
Host: exemplo.com
Content-Type: application/json
Accept: application/json
Content-Length: ...

{"email":"rafael@exemplo.com"}
```

#### Resposta de sucesso (exemplo)

```http
HTTP/1.1 201 Created
Content-Type: application/json

{"ok":true,"message":"E-mail cadastrado"}
```

---

### 4.2) Exemplo GET (buscar dados do servidor)

#### Requisição

```http
GET /api/usuarios/123 HTTP/1.1
Host: exemplo.com
Accept: application/json
```

#### Resposta

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"id":123,"nome":"Rafael","email":"rafael@exemplo.com"}
```

---

### 4.3) Exemplo PUT vs PATCH (diferença na prática)

**Mesmo recurso:** `/api/usuarios/123`

- **PUT**: você manda a versão completa (substitui/define estado desejado) ([RFC Editor](https://www.rfc-editor.org/rfc/rfc9110.html?utm_source=chatgpt.com "RFC 9110: HTTP Semantics"))
    
- **PATCH**: você manda só o que mudou (parcial) ([RFC Editor](https://www.rfc-editor.org/rfc/rfc5789.html?utm_source=chatgpt.com "RFC 5789: PATCH Method for HTTP"))
    

#### PUT (substituição completa)

```http
PUT /api/usuarios/123 HTTP/1.1
Content-Type: application/json

{"id":123,"nome":"Rafael Ribeiro","email":"rafael@exemplo.com","telefone":"11999999999"}
```

#### PATCH (mudança parcial)

```http
PATCH /api/usuarios/123 HTTP/1.1
Content-Type: application/json

{"email":"novoemail@exemplo.com"}
```

---

### 4.4) Exemplo DELETE (remover um recurso)

#### Requisição

```http
DELETE /api/usuarios/123 HTTP/1.1
Host: exemplo.com
```

#### Resposta comum

```http
HTTP/1.1 204 No Content
```

---

## 5) Boas práticas que você precisa conhecer

### 5.1) Status codes mais comuns em APIs

- **200 OK**: deu certo e retornou dados
    
- **201 Created**: criou algo
    
- **204 No Content**: sucesso sem body (muito comum em DELETE)
    
- **400 Bad Request**: dados inválidos
    
- **401 Unauthorized**: não autenticado (sem login/token válido)
    
- **403 Forbidden**: autenticado, mas sem permissão
    
- **404 Not Found**: rota/recurso não encontrado
    
- **409 Conflict**: conflito (ex.: e-mail já existe)
    
- **500 Internal Server Error**: erro do servidor
    

### 5.2) Headers essenciais (o que você mais vai ver)

- **Content-Type**: formato do body enviado (ex.: `application/json`)
    
- **Accept**: formato que o cliente quer receber
    
- **Authorization**: credencial (ex.: `Bearer <token>`)
    
- **Cookie / Set-Cookie**: sessão/autenticação via cookie
    
- **Cache-Control**: regras de cache
    

### 5.3) Autenticação e autorização (visão rápida)

Depois do login, o cliente normalmente envia credenciais em todas as requisições:

- via **cookies** (sessão)
    
- via **token** (ex.: JWT) no header `Authorization`
    

O servidor valida e decide se o usuário pode acessar aquele recurso.

### 5.4) CORS (quando dá erro no navegador)

Se o seu front-end está em `https://site.com` e chama uma API em outro domínio (por exemplo `https://api.site.com` ou outro), o navegador aplica **CORS**.

Se o servidor não permitir a origem/métodos/headers necessários, o browser bloqueia a chamada.

---

## 6) Referências (fontes recomendadas)

- RFC 2616 (HTTP/1.1) — **Method Definitions** e conceitos de métodos “safe” e “idempotent” ([W3C](https://www.w3.org/Protocols/rfc2616/rfc2616.html?utm_source=chatgpt.com "Hypertext Transfer Protocol -- HTTP/1.1"))
    
- RFC 5789 — **PATCH Method for HTTP** (PATCH = modificações parciais) ([RFC Editor](https://www.rfc-editor.org/rfc/rfc5789.html?utm_source=chatgpt.com "RFC 5789: PATCH Method for HTTP"))
    
- RFC 9110 — **HTTP Semantics** (semântica moderna de métodos; relação de PUT/POST com o corpo) ([RFC Editor](https://www.rfc-editor.org/rfc/rfc9110.html?utm_source=chatgpt.com "RFC 9110: HTTP Semantics"))
    
- MDN Web Docs — referência prática de métodos HTTP (GET/POST/PUT/DELETE/PATCH) ([MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods?utm_source=chatgpt.com "HTTP request methods - MDN Web Docs"))
    
