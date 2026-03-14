# API – Application Programming Interface

## 1) O que é uma API

**API (Application Programming Interface)** é uma **interface programável de uma aplicação**.

Em vez de uma pessoa usar a aplicação pelo navegador, **outro sistema ou cliente** conversa diretamente com a aplicação usando **requisições HTTP**.

Em termos simples:

> **API é como a aplicação “conversa” com outras aplicações.**

---

## 2) Para que uma API serve (na prática)

Uma API geralmente serve para:

- Enviar dados
    
- Receber dados
    
- Executar ações
    
- Integrar sistemas
    

### Exemplos reais do dia a dia

- App de celular buscando dados do backend
    
- Front-end em React consumindo dados
    
- Sistema externo integrando pedidos
    
- Painel administrativo consumindo API
    
- Integração com pagamentos, envio de e-mail, etc.
    

---

## 3) Analogia simples (mundo real)

```
Cliente (App / Front-end)
        ↓
       API
        ↓
    Aplicação / Banco de dados
```

A API é o **garçom**:

- Você pede (requisição)
    
- Ele leva até a cozinha (backend)
    
- Ele traz a resposta (JSON/XML)
    

---

## 4) API NÃO é o banco de dados

Isso é importante em pentest.

```
❌ Cliente → Banco de dados
✅ Cliente → API → Banco de dados
```

A API:

- controla acesso
    
- valida permissões
    
- aplica regras de negócio
    

Se a API falha, **o banco fica exposto indiretamente**.

---

## 5) Tipos de API (os mais comuns na web)

- REST
    
- GraphQL
    
- SOAP
    

Vamos ver **um por um**, com exemplos.

---

# API REST

## 6) O que é REST

**REST (Representational State Transfer)** é o **padrão mais usado hoje**.

Características:

- Usa HTTP
    
- Usa métodos HTTP (GET, POST, PUT, DELETE)
    
- Normalmente usa **JSON**
    
- Cada endpoint representa um recurso
    

---

## 7) Exemplo visual – API REST

![Image](https://kajabi-storefronts-production.kajabi-cdn.com/kajabi-storefronts-production/file-uploads/blogs/2147485434/images/7d8522f-3343-70d6-3234-7d8ea88ce2_rest-api-model-http-request-response.webp)

![Image](https://kajabi-storefronts-production.kajabi-cdn.com/kajabi-storefronts-production/file-uploads/blogs/2147485434/images/315487-7af3-d17-c8af-0b4d8af188db_rest-api-model-diagram.png)

![Image](https://media.licdn.com/dms/image/v2/C4D12AQHh6l0xkbhTPg/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1622931040032?e=2147483647&t=KP6s82dMHXyOTcVsNCkKypBjIlQSWYCqI4ucfTrzTJg&v=beta)

```
GET /api/users/10
```

Resposta:

```json
{
  "id": 10,
  "name": "João",
  "email": "joao@email.com"
}
```

---

## 8) REST na prática (exemplo comum)

### Criar usuário

```
POST /api/users
```

### Buscar usuário

```
GET /api/users/10
```

### Atualizar usuário

```
PUT /api/users/10
```

### Excluir usuário

```
DELETE /api/users/10
```

---

## 9) Vulnerabilidades comuns em API REST (conceito)

- Falta de autenticação
    
- Falta de autorização (IDOR)
    
- Exposição excessiva de dados
    
- Validação fraca de input
    
- Rate limit inexistente
    
- Lógica de negócio quebrada
    

### Exemplo conceitual (IDOR)

```
GET /api/users/11
```

Se você só deveria acessar o **seu** usuário e consegue acessar outro, existe falha de autorização.

---

# API GraphQL

## 10) O que é GraphQL

**GraphQL** é um modelo onde:

- Existe **um único endpoint**
    
- O cliente escolhe **exatamente quais dados quer**
    
- Muito usado em aplicações modernas
    

Normalmente:

```
POST /graphql
```

---

## 11) Exemplo visual – GraphQL

![Image](https://www.tutorialspoint.com/graphql/images/graphql_server_integrating_existing_systems.jpg)

![Image](https://www.apollographql.com/docs/_image/graphos/connectors/responses/f2dcc03610de?w=800)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240218204549/GraphQL3-1024.png)

Query:

```graphql
query {
  user(id: 10) {
    name
    email
  }
}
```

Resposta:

```json
{
  "data": {
    "user": {
      "name": "João",
      "email": "joao@email.com"
    }
  }
}
```

---

## 12) Diferença principal do REST

REST:

- Vários endpoints
    
- Dados fixos por endpoint
    

GraphQL:

- Um endpoint
    
- Cliente define os dados
    

---

## 13) Vulnerabilidades comuns em GraphQL

- **Excesso de dados retornados**
    
- Enumeração de schema
    
- Falta de controle de profundidade
    
- Falta de autorização por campo
    
- Queries muito pesadas (DoS lógico)
    

### Exemplo conceitual

Cliente pede mais campos do que deveria:

```graphql
query {
  user(id: 10) {
    name
    email
    passwordHash
    role
  }
}
```

Se a API retornar isso, há **falha grave de autorização**.

---

# API SOAP

## 14) O que é SOAP

**SOAP (Simple Object Access Protocol)** é um modelo mais antigo, ainda usado em:

- Bancos
    
- Sistemas governamentais
    
- ERPs legados
    

Características:

- Usa **XML**
    
- Estrutura rígida
    
- Mais verboso
    
- Usa WSDL (descrição do serviço)
    

---

## 15) Exemplo visual – SOAP

![Image](https://docs.thredd.com/Resources/Images/API_architecture_overview.png)

![Image](https://help.genesys.com/pureconnect/mergedprojects/wh_soap/desktop/img/image001.jpg)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20250513112636358843/SOAP.webp)

Request (simplificado):

```xml
<soap:Envelope>
  <soap:Body>
    <getUser>
      <id>10</id>
    </getUser>
  </soap:Body>
</soap:Envelope>
```

---

## 16) Vulnerabilidades comuns em SOAP

- XML Injection
    
- XXE (XML External Entity)
    
- Exposição do WSDL
    
- Falta de autenticação adequada
    
- Erros verbosos
    

SOAP exige **atenção especial com parsing de XML**.

---

# 17) Exemplo prático crítico (troca de senha via API)

### Fluxo correto

```
POST /api/change-password
→ verifica token
→ valida usuário
→ valida senha atual
→ troca senha
```

### Problema comum (conceito)

- API troca senha apenas com ID do usuário
    
- Sem validar sessão/autorização
    

Isso gera falha lógica grave.

---

# 18) Vulnerabilidades comuns em APIs (geral)

Lista que você deve **sempre ter em mente em pentest web**:

- IDOR (Broken Object Level Authorization)
    
- Broken Authentication
    
- Broken Function Level Authorization
    
- Excessive Data Exposure
    
- Mass Assignment
    
- Falta de rate limit
    
- Falta de logging
    
- Erros detalhados
    
- Falhas de lógica de negócio
    

Essas são a base do **OWASP API Top 10**.

---

## 19) API x Front-end (ponto crítico)

Muita gente confunde:

> “O botão não aparece no front-end”  
> ≠  
> “A API bloqueia a ação”

Em pentest:

- Front-end esconde
    
- API decide
    

Se a API não valida, **a ação pode ser executada mesmo sem botão**.

---

## 20) Resumo final (anotação de curso)

- API = interface programável
    
- Cliente conversa com API via HTTP
    
- REST é o mais comum
    
- GraphQL é flexível e poderoso
    
- SOAP é legado e verboso
    
- APIs são alvos críticos
    
- Vulnerabilidades geralmente são de **autorização e lógica**
    
- Entender API é obrigatório para pentest web
    

---

## Conclusão importante (mentalidade correta)

> **Quem entende API entende a aplicação de verdade.  
> O front-end é só a “cara bonita”. A lógica está na API.**
