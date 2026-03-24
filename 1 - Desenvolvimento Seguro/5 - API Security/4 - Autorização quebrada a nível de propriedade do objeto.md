### Broken Object Property Level Authorization (BOPLA)

A **Autorização quebrada a nível de propriedade do objeto** é uma vulnerabilidade comum em APIs modernas e aplicações web que ocorre quando o sistema permite que um usuário autenticado acesse corretamente um recurso, porém **não controla o acesso às propriedades internas desse recurso**.

Na prática, o usuário possui permissão para acessar o objeto, mas consegue visualizar ou modificar **atributos sensíveis que deveriam estar protegidos**. Esse tipo de falha está diretamente relacionado a problemas de design de autorização granular e frequentemente aparece em ambientes que utilizam arquiteturas orientadas a APIs, microsserviços e serialização automática de dados.

Essa vulnerabilidade é muito abordada em laboratórios práticos e materiais técnicos utilizados em trilhas de aprendizado ofensivo, como os estudos de segurança de APIs explorados em treinamentos especializados de pentest web.

## Como a vulnerabilidade funciona na prática

Em sistemas modernos, é comum que o backend retorne objetos completos em formato JSON. O frontend então decide quais campos serão exibidos ao usuário. Esse modelo cria um risco significativo, pois um atacante pode interceptar a comunicação e visualizar todos os dados retornados pela API.

Considere um sistema onde o usuário consulta o próprio perfil.

Requisição enviada pela aplicação:

GET /api/account/profile

Resposta retornada pelo servidor:

{  
"user_id": 812,  
"name": "Ana",  
"email": "[ana@email.com](mailto:ana@email.com)",  
"plan": "basic",  
"is_admin": false,  
"internal_score": 74,  
"credit_balance": 3800,  
"api_token": "tk_live_82ksd8"  
}

Embora o usuário devesse visualizar apenas nome, email e plano, a resposta inclui informações internas como saldo financeiro, score operacional e token de API. Isso caracteriza uma falha de autorização a nível de propriedade do objeto.

## Visualização conceitual da falha

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A1tJv9qc7_bR2hfZa1GcC0g.png)

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fdpvkqxamcw1umbbwulnw.png)

![Image](https://cdn.prod.website-files.com/623a17f293c65d02ed7b88bd/691dd3a7377f93c2b05986ba_Understanding%20Broken%20Object%20Property%20Level%20Authorization%20%28BOPLA%29.jpg)

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fh7vs84zgcxrnbt09bbym.png)

Essa situação ocorre porque o backend não filtra corretamente os campos antes de enviar a resposta ao cliente.

## Exploração prática durante um teste de segurança

Durante um pentest, o analista pode utilizar um proxy interceptador para capturar a comunicação entre o navegador e a aplicação. Uma das ferramentas mais utilizadas nesse processo é o Burp Suite.

Após configurar o proxy local e ativar a interceptação, o testador acessa funcionalidades do sistema relacionadas ao perfil do usuário ou a recursos personalizados. Ao capturar a requisição, ele pode enviá-la para um módulo de repetição e analisar cuidadosamente a resposta completa retornada pela API.

Nesse momento, o objetivo é identificar:

- propriedades administrativas
    
- dados financeiros
    
- identificadores internos
    
- tokens de autenticação
    
- indicadores operacionais
    

Se esses campos estiverem presentes sem necessidade funcional, já existe evidência de exposição indevida de propriedades.

## Exploração ativa da vulnerabilidade

Além da exposição passiva, o testador pode tentar modificar atributos internos do objeto. Isso geralmente é feito interceptando uma requisição de atualização de dados.

Exemplo de requisição original:

PUT /api/account/profile

Payload enviado pelo sistema:

{  
"phone": "21999999999"  
}

O analista então modifica o conteúdo para testar a autorização granular:

{  
"phone": "21999999999",  
"is_admin": true,  
"credit_balance": 999999,  
"plan": "enterprise"  
}

Se o servidor aceitar essas alterações sem validação adequada, pode ocorrer escalada de privilégio ou manipulação de dados sensíveis, confirmando a presença da vulnerabilidade.

## Impacto em ambientes corporativos

A exploração dessa falha pode gerar consequências graves, como:

- elevação de privilégios administrativos
    
- fraude financeira
    
- manipulação de limites ou planos de serviço
    
- exposição de dados confidenciais
    
- comprometimento total da conta do usuário
    

Em sistemas bancários, plataformas SaaS e aplicações empresariais, o impacto pode ser classificado como crítico.

## Como prevenir essa vulnerabilidade

A mitigação da autorização quebrada a nível de propriedade exige práticas seguras desde a fase de desenvolvimento e integração contínua.

Algumas medidas recomendadas incluem:

- retornar apenas os campos estritamente necessários nas respostas da API
    
- criar objetos seguros de transferência de dados em vez de expor entidades completas do banco
    
- validar explicitamente quais propriedades podem ser alteradas
    
- implementar listas de permissões para atualização de atributos
    
- aplicar controles de autorização granulares no backend
    
- registrar e monitorar tentativas de alteração de campos sensíveis
    

Em contextos DevSecOps, também é recomendável incluir testes automatizados de segurança para APIs no pipeline de entrega contínua, garantindo que falhas desse tipo sejam identificadas antes da implantação em produção.
