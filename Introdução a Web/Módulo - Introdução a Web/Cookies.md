# Cookies: o que são e para que servem

Um **cookie HTTP** é um pequeno dado que o **servidor manda para o navegador** e o navegador pode **guardar** e **enviar de volta** nas próximas requisições para o mesmo site (conforme regras de Domain/Path/Secure/SameSite). Ele existe porque **HTTP é “stateless”** (uma requisição não “lembra” da outra). ([developer.mozilla.org](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Guides/Cookies?utm_source=chatgpt.com "Cookies HTTP - MDN Web Docs"))

O servidor envia cookie usando o header **`Set-Cookie`**. O navegador devolve cookies usando o header **`Cookie`**. ([developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie?utm_source=chatgpt.com "Set-Cookie header - HTTP - MDN Web Docs"))

---

## 1) Visual: fluxo Set-Cookie → armazenamento → Cookie

```
[1] Servidor → Navegador (Resposta HTTP)
    Set-Cookie: SID=abc123; Path=/; HttpOnly; Secure; SameSite=Lax

[2] Navegador guarda no "Cookie Jar" (armazenamento de cookies)

[3] Navegador → Servidor (Próximas requisições compatíveis)
    Cookie: SID=abc123

[4] Servidor usa SID para reconhecer a sessão/usuário
```

Referência oficial e prática (MDN): ([developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie?utm_source=chatgpt.com "Set-Cookie header - HTTP - MDN Web Docs"))

---

# Tipos de cookie (o que você precisa saber em pentest)

## 2.1 Cookie de sessão (session cookie)

**Não tem `Expires` nem `Max-Age`.** Em geral, o navegador mantém **até “a sessão do navegador acabar”** (muitas vezes ao fechar o browser, mas depende do user agent). ([IETF HTTP Working Group](https://httpwg.org/http-extensions/draft-ietf-httpbis-rfc6265bis.html?utm_source=chatgpt.com "Cookies: HTTP State Management Mechanism"))

Exemplo:

```
Set-Cookie: SID=abc123; Path=/; HttpOnly; Secure
```

Uso típico:

- Identificar sessão logada (session id)
    
- Estado temporário (ex: passo do checkout)
    

Ponto de segurança (pentest):

- Se for cookie de sessão, o foco é **proteção contra roubo** (Secure/HttpOnly) e contra **CSRF** (SameSite/anti-CSRF). ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html?utm_source=chatgpt.com "Session Management - OWASP Cheat Sheet Series"))
    

---

## 2.2 Cookie persistente (persistent cookie)

Tem **`Expires`** e/ou **`Max-Age`**, então fica guardado até expirar.

Exemplo:

```
Set-Cookie: remember_me=1; Max-Age=2592000; Path=/; Secure; SameSite=Lax
```

Detalhe importante:

- Se tiver **Max-Age e Expires**, **Max-Age tem precedência**. ([IETF HTTP Working Group](https://httpwg.org/http-extensions/draft-ietf-httpbis-rfc6265bis.html?utm_source=chatgpt.com "Cookies: HTTP State Management Mechanism"))
    

Uso típico:

- “Lembrar login” (com cuidado)
    
- Preferências (tema, idioma)
    

Ponto de segurança (pentest):

- Persistência aumenta janela de risco se o valor for sensível (token). O ideal é que “remember me” use estratégia segura (ex: token rotativo, expiração curta, revogação). (Diretriz geral de gestão de sessão) ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html?utm_source=chatgpt.com "Session Management - OWASP Cheat Sheet Series"))
    

---

## 2.3 Cookie de terceiros (third-party cookie)

É um cookie cujo **domínio do cookie não é o mesmo** do site que você está visitando (muito comum em tracking/ads e integrações). Em navegadores modernos isso vem sendo restringido e controlado com mais rigor.

Exemplo mental:

- Você está em `siteA.com`
    
- Um script/carregamento de `tracker.com` tenta setar cookie de `tracker.com` (isso é third-party no contexto do `siteA.com`)
    

Ponto de segurança (pentest):

- Impacta privacidade, rastreamento e, em alguns cenários, integrações SSO/embedded que dependiam disso. O atributo **SameSite** é central aqui, e mudanças do Chrome fizeram **cookies sem SameSite virarem Lax por padrão**. ([Google for Developers](https://developers.google.com/search/blog/2020/01/get-ready-for-new-samesitenone-secure?utm_source=chatgpt.com "Get Ready for New SameSite=None; Secure Cookie Settings"))
    

---

# Propriedades (atributos) do cookie: explicação detalhada + exemplos

A maioria do que você vai analisar aparece no header `Set-Cookie`. ([developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie?utm_source=chatgpt.com "Set-Cookie header - HTTP - MDN Web Docs"))

## Visual: exemplo completo de Set-Cookie

```
Set-Cookie: SID=abc123;
  Path=/;
  Domain=exemplo.com;
  Expires=Wed, 21 Oct 2026 07:28:00 GMT;
  Secure;
  HttpOnly;
  SameSite=Lax
```

Agora, atributo por atributo:

---

## 1) name

É o **nome** do cookie. Ex: `SID`, `session`, `auth_token`, `remember_me`.

Exemplo:

```
SID=abc123
```

Pentest (o que observar):

- Nome pode indicar função (sessão, auth, preferência).
    
- Um “auth_token” em cookie exige flags fortes (Secure/HttpOnly/SameSite) e boa política de expiração.
    

---

## 2) value

É o **valor** do cookie (o “conteúdo”). Pode ser:

- um **session id** (normal)
    
- um token (JWT ou não)
    
- flags simples (ex: `darkmode=1`)
    

Pentest (o que observar):

- Valor **não deveria conter dados sensíveis legíveis** (ex: senha, CPF, permissões claras).
    
- Se for token de sessão, o risco principal é roubo/reuso (mitigar com flags e gestão de sessão). ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html?utm_source=chatgpt.com "Session Management - OWASP Cheat Sheet Series"))
    

---

## 3) Path

Define **para quais caminhos (URLs) do site** o cookie será enviado.

Exemplo:

```
Path=/
```

Significa: envia para tudo dentro do domínio.

Outro exemplo:

```
Path=/admin
```

Envia só para URLs que começam com `/admin`.

Pentest (o que observar):

- `Path=/` é comum para cookie de sessão geral.
    
- Paths muito amplos podem expor cookie a áreas que não precisam (redução de superfície).
    

---

## 4) Domain

Define **quais hosts** recebem o cookie.

Exemplo:

```
Domain=exemplo.com
```

Isso pode fazer o cookie ser enviado também para subdomínios (dependendo do comportamento do user agent e como foi configurado).

Pentest (o que observar):

- Cookies de sessão com Domain muito amplo podem ficar expostos a riscos com subdomínios (ex: se existir subdomínio menos confiável). Esse é um ponto clássico de arquitetura/segurança para reduzir impacto.
    

---

## 5) Expires (e Max-Age)

Define **quando expira**.

- `Expires=<data>` (data/hora)
    
- `Max-Age=<segundos>` (tempo a partir de agora)
    

Se ambos existirem, **Max-Age vence**. ([IETF HTTP Working Group](https://httpwg.org/http-extensions/draft-ietf-httpbis-rfc6265bis.html?utm_source=chatgpt.com "Cookies: HTTP State Management Mechanism"))

Pentest (o que observar):

- Cookie de sessão geralmente **sem Expires/Max-Age**.
    
- “Remember me” com expiração muito longa aumenta risco (janela de ataque/uso indevido).
    

---

## 6) HttpOnly

Quando presente, o cookie **não pode ser lido por JavaScript** (por exemplo via `document.cookie`). Isso ajuda a reduzir roubo de cookie em caso de **XSS**. ([owasp.org](https://owasp.org/www-community/HttpOnly?utm_source=chatgpt.com "HttpOnly"))

Exemplo:

```
Set-Cookie: SID=abc; HttpOnly
```

Pentest (o que observar):

- Cookies de sessão/autenticação **devem** ter HttpOnly (boa prática).
    
- Se não tiver HttpOnly e existir XSS, o impacto costuma ser maior (roubo de sessão).
    

---

## 7) Secure

Quando presente, o navegador só envia o cookie **em conexões HTTPS** (com ressalvas como localhost). ([developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies?utm_source=chatgpt.com "Using HTTP cookies - MDN Web Docs - Mozilla"))

Exemplo:

```
Set-Cookie: SID=abc; Secure
```

Pentest (o que observar):

- Cookies de sessão/autenticação devem ser `Secure`.
    
- Se o site ainda aceita HTTP, faltando Secure pode facilitar vazamento em tráfego inseguro.
    

---

## 8) SameSite

Controla se o cookie será enviado em requisições **cross-site** (quando a requisição é disparada a partir de outro site). É um mecanismo importante para mitigar **CSRF**. ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html?utm_source=chatgpt.com "Cross-Site Request Forgery Prevention Cheat Sheet"))

Valores:

- `SameSite=Strict`
    
- `SameSite=Lax`
    
- `SameSite=None` (precisa de `Secure` nos browsers modernos) ([Google for Developers](https://developers.google.com/search/blog/2020/01/get-ready-for-new-samesitenone-secure?utm_source=chatgpt.com "Get Ready for New SameSite=None; Secure Cookie Settings"))
    

### Regras práticas (bem resumidas)

- **Strict**: mais restritivo (melhor contra CSRF, pode quebrar fluxos).
    
- **Lax**: meio termo (frequente por padrão).
    
- **None**: permite uso cross-site; **exige Secure** em navegadores modernos. ([Google for Developers](https://developers.google.com/search/blog/2020/01/get-ready-for-new-samesitenone-secure?utm_source=chatgpt.com "Get Ready for New SameSite=None; Secure Cookie Settings"))
    

Pentest (o que observar):

- Se o app depende de cookies para ações sensíveis, SameSite ajuda, mas normalmente **não substitui** proteção anti-CSRF (token/validações), dependendo do caso. ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html?utm_source=chatgpt.com "Cross-Site Request Forgery Prevention Cheat Sheet"))
    

---

# Exemplos práticos (bem didáticos)

## Exemplo A: cookie de sessão (login)

Resposta do servidor:

```
Set-Cookie: SID=abc123; Path=/; HttpOnly; Secure; SameSite=Lax
```

Requisições seguintes:

```
Cookie: SID=abc123
```

O que isso significa:

- O servidor “amarra” a sessão no `SID`.
    
- O navegador envia `SID` automaticamente.
    
- `HttpOnly` reduz exposição a JS (XSS).
    
- `Secure` força HTTPS.
    
- `SameSite=Lax` reduz envio em contextos cross-site.
    

Referências: ([developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/Set-Cookie?utm_source=chatgpt.com "Set-Cookie header - HTTP - MDN Web Docs"))

---

## Exemplo B: cookie persistente (preferência)

```
Set-Cookie: theme=dark; Max-Age=31536000; Path=/; SameSite=Lax
```

O que isso significa:

- Guarda uma preferência simples por 1 ano.
    
- Não é cookie de autenticação, então risco é menor.
    

---

## Exemplo C: third-party (conceito)

Você está em `loja.com` e carrega um recurso de `analytics.com`.  
Se `analytics.com` define cookie dele mesmo no contexto do `loja.com`, isso é cookie de terceiros (e pode ser bloqueado/restringido dependendo do browser e SameSite). ([Google for Developers](https://developers.google.com/search/blog/2020/01/get-ready-for-new-samesitenone-secure?utm_source=chatgpt.com "Get Ready for New SameSite=None; Secure Cookie Settings"))

---

# Por que cookies são críticos para vulnerabilidades (entender para achar e evitar)

Sem ensinar “como invadir”, aqui está o raciocínio de segurança que você precisa ter:

## 1) Sequestro de sessão (session hijacking)

Se o atacante consegue obter o cookie de sessão (por XSS, tráfego inseguro, máquina comprometida, vazamento), ele pode se passar pelo usuário.  
Mitigações clássicas:

- `HttpOnly`, `Secure`, boa expiração, rotação e invalidação de sessão ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html?utm_source=chatgpt.com "Session Management - OWASP Cheat Sheet Series"))
    

## 2) CSRF (ações feitas sem intenção do usuário)

Se o navegador envia cookies automaticamente, um site malicioso pode tentar induzir requisições. `SameSite` ajuda a reduzir isso, e OWASP trata isso diretamente. ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html?utm_source=chatgpt.com "Cross-Site Request Forgery Prevention Cheat Sheet"))

## 3) XSS e cookies

- Sem `HttpOnly`, JS pode ler cookie e exfiltrar.
    
- Com `HttpOnly`, ainda pode haver impacto de XSS, mas normalmente reduz o roubo direto do cookie. ([owasp.org](https://owasp.org/www-community/HttpOnly?utm_source=chatgpt.com "HttpOnly"))
    

---

# Checklist de análise (para suas anotações de pentest web)

Quando você estiver analisando cookies em um alvo autorizado/lab:

1. Cookies de sessão/auth têm **Secure**? ([developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/Cookies?utm_source=chatgpt.com "Using HTTP cookies - MDN Web Docs - Mozilla"))
    
2. Cookies de sessão/auth têm **HttpOnly**? ([owasp.org](https://owasp.org/www-community/HttpOnly?utm_source=chatgpt.com "HttpOnly"))
    
3. Existe **SameSite**? Qual valor? (Strict/Lax/None) ([cheatsheetseries.owasp.org](https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html?utm_source=chatgpt.com "Cross-Site Request Forgery Prevention Cheat Sheet"))
    
4. O cookie tem **Domain** muito amplo? (exposição a subdomínios) ([IETF HTTP Working Group](https://httpwg.org/http-extensions/draft-ietf-httpbis-rfc6265bis.html?utm_source=chatgpt.com "Cookies: HTTP State Management Mechanism"))
    
5. O cookie tem **Path** adequado? (mínimo necessário) ([IETF HTTP Working Group](https://httpwg.org/http-extensions/draft-ietf-httpbis-rfc6265bis.html?utm_source=chatgpt.com "Cookies: HTTP State Management Mechanism"))
    
6. É sessão ou persistente? (Expires/Max-Age) e expiração faz sentido? ([IETF HTTP Working Group](https://httpwg.org/http-extensions/draft-ietf-httpbis-rfc6265bis.html?utm_source=chatgpt.com "Cookies: HTTP State Management Mechanism"))
    
7. Em mudanças recentes de navegador, cookies sem SameSite podem virar Lax por padrão (impacto funcional e de segurança). ([Google for Developers](https://developers.google.com/search/blog/2020/01/get-ready-for-new-samesitenone-secure?utm_source=chatgpt.com "Get Ready for New SameSite=None; Secure Cookie Settings"))
    

---

Se você quiser, eu adiciono uma seção final “como documentar isso em relatório” com um modelo pronto tipo:

- Cookie observado
    
- Flags presentes/ausentes
    
- Risco
    
- Evidência (cópia do Set-Cookie)
    
- Recomendação (Secure/HttpOnly/SameSite/expiração)
    

E também posso integrar essa parte de cookies dentro do seu documento maior (HTTP + status codes + Nginx/Apache + load balancer + browser rendering).