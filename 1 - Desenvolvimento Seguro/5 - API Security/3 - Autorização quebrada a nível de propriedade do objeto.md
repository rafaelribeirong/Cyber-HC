# Broken Object Property Level Authorization (BOPLA)

A vulnerabilidade **Broken Object Property Level Authorization (BOPLA)** ocorre quando uma aplicação permite que um usuário autenticado acesse um objeto válido, porém **não controla corretamente o acesso às propriedades internas desse objeto**.

Diferente da BOLA, onde o problema é acessar o objeto de outro usuário, na BOPLA o problema é:

- acessar campos sensíveis
    
- visualizar atributos internos
    
- modificar propriedades críticas
    

Mesmo estando autenticado e acessando o próprio recurso.

Essa falha está frequentemente associada a:

- Excessive Data Exposure
    
- Mass Assignment
    
- Falta de autorização granular
    
- APIs que retornam objetos completos
    

---

# Visão conceitual da vulnerabilidade

![Image](https://www.researchgate.net/publication/342575529/figure/fig5/AS%3A908293190991879%401593565380171/API-Response-in-JSON-Format.png)

![Image](https://miro.medium.com/0%2AyHg5ZnmXapIDZAuU.png)

![Image](https://miro.medium.com/1%2ARlnN9--20yGfqkl8N1mQfg.png)

![Image](https://i.sstatic.net/81buI.png)

A API retorna o objeto completo e não valida quais propriedades o usuário pode visualizar ou alterar.

---

# Exemplo prático de cenário vulnerável

Uma aplicação possui o endpoint:

```
GET /api/v1/account
```

Resposta:

```json
{
 "user_id": 105,
 "name": "Rafael",
 "email": "rafael@email.com",
 "plan": "basic",
 "is_admin": false,
 "credit_balance": 700,
 "internal_flag": "priority_user"
}
```

O usuário deveria visualizar apenas:

- nome
    
- email
    
- plano
    

Porém a API expõe:

- saldo interno
    
- flags administrativas
    
- dados operacionais
    

Isso caracteriza **exposição indevida de propriedades do objeto**.

---

# Relação com Excessive Data Exposure

Em muitos sistemas o backend retorna o objeto completo e o frontend apenas oculta campos.

O atacante usa proxy e consegue visualizar:

- tokens
    
- permissões
    
- valores financeiros
    
- indicadores administrativos
    

Isso transforma a exposição em **vetor real de ataque**.

---

# Exploração usando Burp Suite

## Interceptação da requisição

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-intercepted-request.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-repeater.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AeaWL-9Wu0rY4r8Gvy8pTFA.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/burps-layout-hidden-tab-icon.png)

Configurar o navegador:

```
Proxy HTTP
127.0.0.1
Porta 8080
```

Ativar:

```
Proxy → Intercept → ON
```

Acessar funcionalidade da aplicação para capturar a requisição.

---

## Análise da resposta no Burp

Enviar a requisição para o Repeater.

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-repeater.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-product-page-request.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-repeater-invalid-productid.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-send-to-repeater.png)

Agora observar:

- campos ocultos
    
- atributos administrativos
    
- propriedades financeiras
    
- identificadores internos
    

Isso já confirma **BOPLA passiva**.

---

# Exploração ativa da vulnerabilidade

A etapa seguinte é testar alteração de propriedades.

Exemplo:

```
PUT /api/v1/account
Content-Type: application/json
```

Payload:

```json
{
 "plan": "enterprise",
 "is_admin": true,
 "credit_balance": 999999
}
```

Se a API aceitar a alteração:

- ocorre escalada de privilégio
    
- ocorre manipulação de dados sensíveis
    
- ocorre comprometimento do modelo de autorização
    

Esse cenário representa **BOPLA combinada com Mass Assignment**.

---

# Testes profissionais recomendados no Burp

Durante o pentest devem ser realizados testes como:

Alteração de propriedades booleanas:

```
"is_admin": true
"is_verified": true
```

Alteração de permissões:

```
"role": "superuser"
```

Manipulação financeira:

```
"balance": 1000000
```

Inserção de propriedades não existentes:

```
"account_type": "internal"
```

Se a API aceitar qualquer desses valores sem validação, a falha está confirmada.

---

# Como identificar rapidamente BOPLA em um teste real

Indicadores comuns:

- API retorna objetos muito grandes em JSON
    
- Diferença entre dados exibidos no frontend e dados retornados
    
- Uso de frameworks ORM com serialização automática
    
- Endpoints PUT ou PATCH sem validação granular
    
- Campos administrativos expostos
    

---

# Impacto de segurança

Dependendo do sistema a vulnerabilidade pode permitir:

- elevação de privilégio
    
- fraude financeira
    
- acesso a dados confidenciais
    
- comprometimento completo de contas
    
- manipulação de registros internos
    

Em ambientes corporativos ou financeiros o impacto pode ser crítico.

---

# Mitigação recomendada

Boas práticas técnicas incluem:

- implementar autorização a nível de propriedade
    
- criar DTO seguro para resposta da API
    
- validar campos permitidos na escrita
    
- aplicar whitelist de atributos
    
- não confiar em dados enviados pelo cliente
    
- ocultar propriedades sensíveis no backend
    

Exemplo conceitual seguro:

```
allowed_update_fields = ["phone", "address"]
```

Qualquer outro campo deve ser ignorado ou rejeitado.

