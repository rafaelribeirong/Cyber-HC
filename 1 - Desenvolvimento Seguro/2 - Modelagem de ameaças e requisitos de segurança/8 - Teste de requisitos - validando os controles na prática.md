# Teste de requisitos – validando os controles na prática

Depois de definir os **controles e subcontroles de segurança**, o próximo passo é **validar se eles realmente funcionam**.  
Isso é feito executando **testes práticos na aplicação**, comparando o comportamento esperado pelo desenvolvedor com o comportamento observado durante os testes de segurança.

Esses testes devem ocorrer **antes da liberação para produção**, normalmente em um ambiente de **stage (staging)** que simula o ambiente produtivo.

---

# Fluxo de validação do controle

![Image](https://www.mabl.com/hubfs/Screen%20Shot%202017-12-19%20at%204.49.51%20PM.png)

![Image](https://res.cloudinary.com/snyk/image/upload/f_auto%2Cw_2560%2Cq_auto/f_auto/q_auto/v1613516749/wordpress-sync/ssdlc-2.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A2Cng3SGd3MABsZHUOGEtPg.png)

![Image](https://assets.northflank.com/northflank_environments_0447528004.png?auto=avif&quality=100&width=937)

Fluxo recomendado:

Desenvolvimento → Ambiente de Stage → Teste de Segurança → Ajustes → Produção

Objetivo:

Garantir que os **controles de segurança implementados realmente funcionam antes da aplicação ir para produção**.

---

# Exemplo de controle testado

Controle  
Filtro de entrada de dados do usuário

Objetivo do controle

Garantir que **dados enviados pelo usuário sejam validados e sanitizados antes de serem processados pela aplicação**.

Esse controle ajuda a prevenir:

- SQL Injection
    
- Cross-Site Scripting (XSS)
    
- Command Injection
    
- Buffer overflow
    
- Inserção de payload malicioso
    

---

# Cenário de teste

Aplicação rodando em ambiente de **stage**.

Exemplo de funcionalidade:

Formulário que recebe uma **URL enviada pelo usuário**.

Fluxo esperado pelo desenvolvedor:

1. Usuário insere uma URL válida
    
2. Aplicação valida o formato da URL
    
3. Sistema aceita o valor
    
4. Informação é processada ou armazenada
    

Exemplo de entrada válida:

```
https://empresa.com
```

Resultado esperado:

Sistema aceita a URL.

---

# Teste de segurança realizado

Agora executamos testes para verificar **se o controle realmente protege a aplicação**.

Testes de validação de URL.

Entrada testada:

```
javascript:alert(1)
```

Objetivo do teste

Verificar se o sistema bloqueia URLs maliciosas.

Resultado esperado

A aplicação deve:

- rejeitar o valor
    
- apresentar mensagem de erro
    
- não executar o código
    

---

# Outro teste

Entrada enviada:

```
http://empresa.com/<script>alert(1)</script>
```

Objetivo

Verificar se a aplicação sanitiza scripts inseridos na URL.

Resultado esperado

A aplicação deve:

- remover ou bloquear o script
    
- não executar código JavaScript
    

---

# Teste de tamanho máximo

Entrada enviada

URL com mais de 5000 caracteres.

Objetivo

Verificar se existe limite de tamanho para evitar:

- ataques de buffer
    
- consumo excessivo de recursos
    

Resultado esperado

Sistema rejeita o valor ou limita o tamanho permitido.

---

# Teste de caracteres especiais

Entrada enviada

```
http://empresa.com/%00%0A%0D
```

Objetivo

Verificar tratamento de caracteres especiais e codificação.

Resultado esperado

Sistema rejeita ou sanitiza a entrada.

---

# Modelo de registro do teste

|Controle|Subcontrole|Cenário de teste|Entrada enviada|Resultado esperado|Resultado obtido|Status|Evidência|
|---|---|---|---|---|---|---|---|
|Filtro de entrada|Validação de URL|URL válida|[https://empresa.com](https://empresa.com/)|Aceitar valor|Aceitou|OK|Screenshot|
|Filtro de entrada|Sanitização|Script inserido|javascript:alert(1)|Bloquear entrada|Bloqueado|OK|Log|
|Filtro de entrada|Limite de tamanho|URL grande|5000 caracteres|Rejeitar|Rejeitado|OK|Teste|

---

# Evidências que podem ser coletadas

Durante os testes, é importante registrar evidências como:

- capturas de tela
    
- logs da aplicação
    
- registros de erro
    
- relatórios de testes
    
- evidências de sanitização no código
    
- resultados de ferramentas de segurança
    

---

# Benefícios dessa abordagem

Validação real dos controles implementados  
Identificação de falhas antes da produção  
Melhoria da segurança da aplicação  
Base de evidência para auditoria  
Documentação técnica para a equipe