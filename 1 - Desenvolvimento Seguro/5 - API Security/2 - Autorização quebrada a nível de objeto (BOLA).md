# Autorização quebrada a nível de objeto (BOLA)

A **Broken Object Level Authorization (BOLA)** é uma das vulnerabilidades mais comuns em APIs modernas e está listada como **API1 no OWASP API Security Top 10**. Esse tipo de falha ocorre quando uma aplicação não verifica corretamente se um usuário tem permissão para acessar um determinado recurso ou objeto.

Em APIs, objetos geralmente representam entidades específicas do sistema, como usuários, pedidos, documentos, veículos ou registros em banco de dados. Quando a aplicação não valida corretamente o acesso a esses objetos, um atacante pode manipular identificadores para acessar dados de outros usuários.

---

# Visão conceitual da vulnerabilidade

![Image](https://media.licdn.com/dms/image/v2/C4D12AQEKV4K_-rzzGQ/article-cover_image-shrink_720_1280/article-cover_image-shrink_720_1280/0/1596612879982?e=2147483647&t=WMfibC9UZ_AqhB2cicCz7tMO_c2OEGkLoH5-Mo3253Q&v=beta)

![Image](https://miro.medium.com/1%2AeXBOryoQV6arheNrZNiToA.jpeg)

![Image](https://www.authlete.com/img/kb/en/oauth-and-openid-connect/error-handling/fail-api_1.png)

![Image](https://stylish-appliance-1c1cc1c30d.media.strapiapp.com/image_3_6152a1e7f4.jpg)

Essa vulnerabilidade ocorre quando a aplicação utiliza identificadores diretos de objetos e não valida corretamente se o usuário possui permissão para acessá-los.

Por exemplo, uma API pode permitir acessar informações de usuários utilizando um endpoint como:

```
GET /api/users/123
```

Se a aplicação não verificar se o usuário autenticado tem autorização para acessar esse recurso, um atacante pode modificar o identificador.

```
GET /api/users/124
```

Se a API retornar os dados de outro usuário, significa que existe uma falha de autorização.

---

# Como a vulnerabilidade acontece

O problema ocorre quando a aplicação apenas verifica **se o usuário está autenticado**, mas não verifica **se ele possui autorização para acessar aquele objeto específico**.

Muitas APIs recebem parâmetros que identificam recursos específicos.

Esses parâmetros podem incluir:

ID de usuário  
ID de pedido  
ID de arquivo  
ID de veículo  
ID de documento

Se esses identificadores forem manipuláveis e não houver validação adequada no servidor, o atacante pode acessar dados que não deveria.

---

# Exemplo prático de exploração

Imagine uma aplicação que permite visualizar informações de veículos registrados.

Um usuário autenticado realiza a seguinte requisição:

```
GET /api/v2/vehicles/54321
```

A API retorna os dados do veículo pertencente ao usuário.

Um atacante pode modificar o identificador:

```
GET /api/v2/vehicles/54322
```

Se a API retornar os dados de outro usuário, significa que o sistema possui uma falha de autorização a nível de objeto.

Esse tipo de exploração é extremamente comum em aplicações que utilizam APIs REST.

---

# Exemplo usando JSON

Resposta da API para o usuário autenticado:

```json
{
  "vehicle_id": 54321,
  "owner": "userA",
  "model": "Toyota",
  "plate": "ABC1234"
}
```

Após manipular o identificador:

```json
{
  "vehicle_id": 54322,
  "owner": "userB",
  "model": "BMW",
  "plate": "XYZ5678"
}
```

Nesse caso, a aplicação está expondo dados de outro usuário.

---

# Por que essa vulnerabilidade é crítica

A vulnerabilidade BOLA pode permitir que atacantes:

acessam dados de outros usuários  
modifiquem informações sensíveis  
excluam recursos de outros usuários  
visualizem informações confidenciais

Em aplicações que manipulam dados sensíveis, esse tipo de falha pode resultar em vazamento de dados ou comprometimento de contas.

---

# Exemplo em aplicações reais

Esse tipo de vulnerabilidade é comum em sistemas que utilizam APIs para:

aplicações mobile  
plataformas SaaS  
sistemas de e-commerce  
aplicações bancárias  
sistemas de gestão empresarial

Como APIs geralmente utilizam identificadores diretos de recursos, o risco de exploração é elevado quando não existem verificações adequadas de autorização.

---

# Como identificar a vulnerabilidade

Durante testes de segurança, a vulnerabilidade pode ser identificada manipulando parâmetros de identificação de objetos.

O processo geralmente envolve:

interceptar uma requisição usando um proxy como Burp Suite  
identificar parâmetros que representam objetos  
modificar esses identificadores  
verificar se a API retorna dados de outros usuários

Se a API permitir acesso a objetos que não pertencem ao usuário autenticado, a vulnerabilidade está presente.

---

# Mitigação da vulnerabilidade

Para evitar falhas de autorização a nível de objeto, é necessário implementar verificações adequadas no servidor.

A aplicação deve validar se o usuário autenticado possui permissão para acessar aquele recurso específico.

Algumas boas práticas incluem:

validar permissões em todas as requisições  
utilizar controle de acesso baseado em usuário ou função  
não confiar em identificadores enviados pelo cliente  
verificar propriedade do recurso antes de retornar dados

Essas verificações devem ser implementadas no backend da aplicação.

---

# Exemplo de verificação segura

Em vez de apenas buscar o objeto pelo identificador:

```
SELECT * FROM vehicles WHERE vehicle_id = 54321
```

A aplicação deve verificar se o objeto pertence ao usuário autenticado.

```
SELECT * FROM vehicles
WHERE vehicle_id = 54321
AND owner_id = current_user
```

Essa abordagem garante que o usuário só consiga acessar recursos que realmente pertencem a ele.

---

# Conclusão

A vulnerabilidade **Broken Object Level Authorization (BOLA)** ocorre quando uma aplicação falha em verificar corretamente se um usuário tem autorização para acessar um objeto específico.

Esse tipo de falha é extremamente comum em APIs e pode permitir que atacantes acessem ou modifiquem dados de outros usuários.

Para prevenir esse problema, é essencial implementar verificações rigorosas de autorização no backend da aplicação e validar o acesso a cada recurso solicitado.

---

# Usando Burp Suite para identificar BOLA

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-intercepted-request.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-add-to-cart.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-repeater.png)

O Burp Suite funciona como um **proxy entre o navegador e a aplicação**. Isso permite interceptar requisições HTTP enviadas pelo navegador e modificar os parâmetros antes que eles cheguem ao servidor.

Esse processo é fundamental para testar vulnerabilidades como **Broken Object Level Authorization**.

---

# Passo 1 — Configurar o proxy

Quando você abre o Burp Suite, ele cria um proxy local.

Normalmente ele escuta em:

```
127.0.0.1:8080
```

Você precisa configurar seu navegador para usar esse proxy.

No navegador configure:

Proxy HTTP:

```
127.0.0.1
```

Porta:

```
8080
```

Depois disso, todo o tráfego do navegador passará pelo Burp.

---

# Passo 2 — Ativar interceptação

No Burp Suite vá em:

```
Proxy → Intercept
```

E deixe:

```
Intercept is ON
```

Agora toda requisição feita no navegador será interceptada antes de chegar ao servidor.

---

# Passo 3 — Interceptar uma requisição da API

Agora acesse alguma funcionalidade do sistema.

Por exemplo, no **crAPI** quando você consulta um recurso.

Uma requisição pode aparecer assim no Burp:

```http
GET /api/v2/vehicles/54321 HTTP/1.1
Host: localhost:8888
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
```

Essa requisição está pedindo os dados do veículo **54321**.

---

# Passo 4 — Testar manipulação de objeto

Agora você altera o ID.

Exemplo:

```http
GET /api/v2/vehicles/54322 HTTP/1.1
```

Se a API retornar os dados de outro usuário, existe **BOLA**.

---

# Passo 5 — Enviar a requisição modificada

Depois de modificar a requisição no Burp:

Clique em:

```
Forward
```

Ou envie para o **Repeater**.

---

# Passo 6 — Usar o Repeater (melhor prática)

No Burp clique com botão direito na requisição:

```
Send to Repeater
```

Depois vá em:

```
Repeater
```

Agora você pode testar diferentes valores de forma manual.

Exemplo:

```
/api/v2/vehicles/10001
/api/v2/vehicles/10002
/api/v2/vehicles/10003
```

E observar as respostas da API.

---

# Exemplo de resposta vulnerável

Se a resposta retornar dados de outro usuário:

```json
{
 "vehicle_id": 54322,
 "owner": "userB",
 "model": "BMW",
 "plate": "XYZ5678"
}
```

Isso confirma a vulnerabilidade.

---

# Como descobrir endpoints vulneráveis

Durante um pentest você normalmente procura parâmetros como:

```
id=
user_id=
account_id=
vehicle_id=
order_id=
document_id=
```

Esses parâmetros frequentemente representam **objetos do sistema**.

---

# Ferramentas úteis do Burp para BOLA

Dentro do Burp você pode usar:

Proxy  
para interceptar requisições.

Repeater  
para testar manualmente.

Intruder  
para automatizar ataques.

Comparer  
para comparar respostas.

---

# Teste automatizado com Intruder

Você também pode usar o **Intruder** para testar vários IDs.

Exemplo:

```
/api/v2/vehicles/§54321§
```

E enviar uma lista:

```
54300
54301
54302
54303
```

Assim você testa vários objetos rapidamente.

---

# Dica profissional de pentester

Quando estiver testando APIs:

Sempre observe:

headers  
tokens  
IDs  
UUIDs  
parâmetros JSON  
IDs no body

Qualquer identificador pode ser alvo de **BOLA**.