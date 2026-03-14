# Modelagem na prática – definindo os controles

Após identificar os ativos e mapear as possíveis ameaças em cada componente do sistema, a etapa final da modelagem de ameaças consiste em **definir os pontos de controle de segurança**. Esses controles são mecanismos técnicos, arquiteturais ou processuais que têm como objetivo reduzir a probabilidade de exploração das ameaças identificadas ou minimizar seus impactos caso ocorram.

Essa fase é essencial porque transforma a análise de riscos em **ações concretas de proteção do sistema**. Cada ameaça identificada durante a modelagem deve possuir pelo menos um controle associado capaz de mitigá-la.

---

# Visão geral da definição de controles

![Image](https://images.openai.com/static-rsc-3/EFhbD_cfGXw_v_Um-uN_bOPeNVvb05sr-81b2etWrlu1hAqyiZn6MQ61ByGbu4KZO0tsLN96xVDU8y46DkzpNERVQvmhx0TH0q3BJvkb9uo?purpose=fullsize&v=1)

![Image](https://community.sap.com/legacyfs/online/storage/blog_attachments/2021/12/defense-in-depth-s4ahana-diagram-1.png)

![Image](https://cdn2.hubspot.net/hubfs/99242/Blog_Images/7%20layers%20of%20cybersecurity.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A74q4li6V_7I2N6SnqY9yIg.jpeg)

A definição de controles normalmente segue o princípio de **defesa em profundidade**, onde múltiplas camadas de segurança são implementadas para proteger o sistema.

Essas camadas podem incluir:

controles na interface da aplicação  
controles no backend  
controles na infraestrutura  
controles de rede  
controles no armazenamento de dados  
controles operacionais e de monitoramento

Essa abordagem garante que, mesmo que um controle falhe, outras camadas continuem protegendo o sistema.

---

# Exemplo prático com base na arquitetura analisada

Considerando o modelo simplificado utilizado anteriormente:

```text
Usuário
   |
Frontend Web
   |
Backend / API
   |
Banco de Dados
```

Cada componente foi analisado para identificar ameaças potenciais. Agora, para cada ameaça identificada, serão definidos os controles correspondentes.

---

# Controles para o Frontend

O frontend é responsável pela interação direta com o usuário e por isso está exposto a diversas ameaças originadas no navegador ou em manipulação de requisições.

### Ameaça: Cross-Site Scripting (XSS)

O XSS ocorre quando scripts maliciosos são inseridos em páginas da aplicação e executados no navegador do usuário.

Controles recomendados:

validação e sanitização de entradas de dados  
implementação de Content Security Policy  
codificação segura de dados exibidos na interface  
uso de frameworks que previnem injeção de scripts

---

### Ameaça: manipulação de parâmetros

Usuários podem modificar parâmetros enviados em requisições HTTP para tentar acessar funcionalidades indevidas.

Controles recomendados:

validação de dados no servidor  
verificação de integridade de parâmetros  
uso de tokens de segurança  
controle de acesso baseado em permissões

---

# Controles para o Backend

O backend representa a camada onde são executadas as regras de negócio da aplicação. Vulnerabilidades nessa camada podem permitir acesso indevido ou manipulação de dados.

### Ameaça: SQL Injection

Essa vulnerabilidade ocorre quando entradas do usuário são utilizadas diretamente em consultas ao banco de dados.

Controles recomendados:

uso de consultas parametrizadas  
uso de ORM seguro  
validação rigorosa de entradas  
princípio de menor privilégio no acesso ao banco

---

### Ameaça: acesso não autorizado

Pode ocorrer quando usuários conseguem acessar funcionalidades sem possuir as permissões adequadas.

Controles recomendados:

implementação de autenticação forte  
controle de acesso baseado em papéis  
verificação de autorização em todas as requisições  
gestão segura de sessões

---

# Controles para o Banco de Dados

O banco de dados é um dos ativos mais críticos da aplicação, pois armazena informações sensíveis.

### Ameaça: vazamento de dados

Dados sensíveis podem ser expostos por falhas de configuração, acesso indevido ou exploração de vulnerabilidades.

Controles recomendados:

criptografia de dados em repouso  
criptografia de dados em trânsito  
controle rigoroso de acesso ao banco  
monitoramento de atividades suspeitas

---

### Ameaça: alteração indevida de registros

Ataques podem tentar modificar dados críticos armazenados no banco.

Controles recomendados:

controle de acesso baseado em privilégios  
registro de logs de alteração de dados  
verificação de integridade de registros  
backup e versionamento de dados

---

# Representação prática de ameaças e controles

```text
Usuário
   |
   v
Frontend Web
   ameaça: XSS
   ameaça: manipulação de parâmetros
   controles: validação de entrada, CSP, codificação de dados
   |
   v
Backend / API
   ameaça: SQL Injection
   ameaça: acesso não autorizado
   controles: queries parametrizadas, autenticação, RBAC
   |
   v
Banco de Dados
   ameaça: vazamento de dados
   ameaça: alteração de registros
   controles: criptografia, controle de acesso, monitoramento
```

Essa estrutura permite visualizar claramente:

os ativos do sistema  
as ameaças associadas a cada ativo  
os controles definidos para reduzir os riscos

---

# Controles adicionais em outras camadas

Além dos controles diretamente relacionados ao código da aplicação, a modelagem de ameaças também pode incluir controles em outras camadas do ambiente tecnológico.

Esses controles podem incluir:

firewalls para proteção da rede  
segmentação de rede entre serviços  
gestão de identidades e acessos  
monitoramento de eventos de segurança  
processos de resposta a incidentes

Essas medidas complementam os controles implementados na aplicação e ajudam a fortalecer a segurança do sistema.

---

# Conclusão

A definição de controles representa a última etapa da modelagem de ameaças. Nessa fase, as ameaças identificadas são transformadas em requisitos de segurança que devem ser implementados no sistema.

Esse processo permite que o desenvolvimento da aplicação já incorpore mecanismos de proteção capazes de reduzir riscos e prevenir vulnerabilidades antes que o sistema seja colocado em produção.

Ao integrar a modelagem de ameaças ao ciclo de desenvolvimento de software, as organizações conseguem construir aplicações mais seguras e reduzir significativamente o impacto de incidentes de segurança ao longo do tempo.