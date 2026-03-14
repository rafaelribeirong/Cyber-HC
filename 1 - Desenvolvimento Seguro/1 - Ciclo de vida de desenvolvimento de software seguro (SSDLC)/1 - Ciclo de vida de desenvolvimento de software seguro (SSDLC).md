# Segurança de Aplicações (Application Security – AppSec)

## Introdução

A segurança de aplicações (Application Security – AppSec) consiste no conjunto de práticas, processos e tecnologias utilizados para proteger aplicações contra vulnerabilidades e ataques ao longo de todo o seu ciclo de vida.

Com o crescimento de aplicações web, APIs e arquiteturas baseadas em microserviços, tornou-se essencial integrar segurança diretamente no processo de desenvolvimento de software.

Uma frase muito utilizada na área de segurança resume bem esse conceito:

**“A gente só protege aquilo que conhece. Não tem como proteger algo se não conhecemos.”**

Isso significa que, para proteger uma aplicação, precisamos compreender:

- como ela foi desenvolvida
    
- quais tecnologias utiliza
    
- quais dependências externas possui
    
- quais dados processa
    
- qual é sua superfície de ataque
    

Para estruturar essas práticas, diversas organizações utilizam frameworks como:

OWASP Proactive Controls  
[https://owasp.org/www-project-proactive-controls/](https://owasp.org/www-project-proactive-controls/)

OWASP SAMM  
[https://owasp.org/www-project-samm/](https://owasp.org/www-project-samm/)

OWASP ASVS  
[https://owasp.org/www-project-application-security-verification-standard/](https://owasp.org/www-project-application-security-verification-standard/)

---

# SDLC – Software Development Life Cycle

O **Software Development Life Cycle (SDLC)** representa o ciclo completo de desenvolvimento de software.

Ele define as etapas que uma aplicação percorre desde sua concepção até sua operação e evolução.

Etapas comuns do SDLC:

Requirement Analysis  
Design  
Implementation  
Testing  
Deployment  
Evolution / Maintenance

![Image](https://images.openai.com/static-rsc-3/WPJuUySipL23safvxEbXBgcRMYTr3zKhAPaWZeh4F8-DXgx9KDYl6gjrsQAdyZJonFrJCywULrqSqH9dyY89EUOJw0B5TCqQ4GGgxHlpEZs?purpose=fullsize&v=1)

![Image](https://images.openai.com/static-rsc-3/vnjuTgcYKWu3m4UrMUc9gAcWkcSPBLlfb1hjXMTdopiGFulQ7yOdsiXo13UL6FedGQXgEdptazB8svEwZJcjpT78WbX5bTwVS0IRoJZqnwM?purpose=fullsize&v=1)

![Image](https://miro.medium.com/1%2A1Om5oPGlLVI3KjS01vQi5A.jpeg)

![Image](https://axify.io/hs-fs/hubfs/Axify%20blogue%20header%20%286%29-1.png?height=960&name=Axify+blogue+header+%286%29-1.png&width=1584)

Cada etapa gera **entregáveis importantes**, que serão utilizados na próxima fase.

---

# Por que surgiu o DevOps

Historicamente existia uma separação entre duas equipes:

**Dev (Desenvolvimento)**  
Responsável por criar o software.

**Ops (Operações)**  
Responsável por implantar e manter o sistema.

Esse modelo gerava problemas como:

- demora na entrega de software
    
- conflitos entre equipes
    
- dificuldade de implantação
    
- ambientes inconsistentes
    

Para resolver isso surgiu o **DevOps**, que integra desenvolvimento e operações.

Fluxo DevOps:

DEV  
Plan → Code → Build → Test

OPS  
Release → Deploy → Operate → Monitor

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ATXiF3fEEUgpfLN2U9-iLJw.png)

![Image](https://images.openai.com/static-rsc-3/I1q6KmhKrZQaFQkXtvRWa29tbI52CAlNZCXrQB5R_7dQfm9IRMlIguW5eJT8gy9DqloUkkViiP2jdQVI0BDgv8eA1f_4jZu_Wb5-4s-rZmk?purpose=fullsize&v=1)

![Image](https://images.openai.com/static-rsc-3/YTZGcsDB0FUrLKxuSYh0KcLCAplWIJ12WWR4mt-Onvyyp2MxK_yp1pKagaCp1hKOm88C3MoupXM0TgglAwWgzA7jbxTT1hnfmnRDJdIskQA?purpose=fullsize&v=1)

![Image](https://images.openai.com/static-rsc-3/VsMwkDtvRIbtsAcRlVvuNbTqTF-aVckhiCNG48z0MERH3SZEqCS9qOpgka1MbOut8U2Nl2Chwu_hvO_hs5l3uZZ7rWqQKnAw_ZekVBE6oEk?purpose=fullsize&v=1)

Quando segurança é integrada ao processo temos o modelo **DevSecOps**.

---

# PLAN – Planejamento

Nesta fase são definidos os requisitos da aplicação.

Atividades realizadas:

- definição de requisitos funcionais
    
- definição de requisitos de segurança
    
- definição da arquitetura
    
- identificação de riscos iniciais
    

### Entregáveis

Documento de requisitos  
Documento de requisitos de segurança  
Arquitetura da aplicação  
Modelo inicial de ameaças

---

# Modelagem de Ameaças (Threat Modeling)

A modelagem de ameaças consiste em analisar o design da aplicação para identificar possíveis ameaças.

A pergunta central dessa etapa é:

**“O que pode dar errado?”**

Uma metodologia muito utilizada é o modelo **STRIDE**.

![Image](https://media.licdn.com/dms/image/v2/D4D12AQGFDNtZDzBdJw/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1678508679780?e=2147483647&t=hSHXttvK_HVYgeNEalKsk--dcq_tV-JlORPS9-c78_c&v=beta)

![Image](https://dz2cdn1.dzone.com/storage/temp/18224099-stride-threat-model-mc-slide2.png)

![Image](https://entail.jit.io/en-assets/jit/fit-in/440x396/image3-1745828898756.png)

![Image](https://developer.ibm.com/developer/default/articles/threat-modeling-microservices-openshift-4/images/STRIDE.png)

STRIDE identifica seis categorias de ameaças:

Spoofing  
Tampering  
Repudiation  
Information Disclosure  
Denial of Service  
Elevation of Privilege

Após identificar ameaças, são definidos **requisitos de segurança da aplicação**.

---

# CODE – Desenvolvimento

Durante essa etapa os desenvolvedores escrevem o código da aplicação.

O código deve ser armazenado em um **Version Control System (VCS)**.

Exemplos:

Git  
GitHub  
GitLab  
Bitbucket

O desenvolvedor armazena o código nesses repositórios para garantir:

- histórico de alterações
    
- colaboração entre desenvolvedores
    
- rastreabilidade
    

---

# Git Flow

Um modelo comum de desenvolvimento é o **Git Flow**.

![Image](https://images.openai.com/static-rsc-3/oKK1l5T0sxYKFaMAq8bDSAix7QxlSL4evzSuEV4WT5tfcv5igF8uD7V0JYHhHtssOv_zu7THcCYdzUD7oHcr8vQ7aM7xamA-GEauC_H9Wmk?purpose=fullsize&v=1)

![Image](https://wac-cdn.atlassian.com/dam/jcr%3Acc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=3238)

![Image](https://images.openai.com/static-rsc-3/tTKRcZlB4p3Ubru_TQDTKj89Jh1I48n4hjzkZPLibcQXpvC3VGz6anWQvrMQwMMIDGxkQ-ahXCdPcC71k0sWzucliuvKYqdKU_8Vii5F6qc?purpose=fullsize&v=1)

![Image](https://docs.aws.amazon.com/images/prescriptive-guidance/latest/choosing-git-branch-approach/images/gitflow-diagram.png)

Principais branches:

main  
develop  
feature  
release  
hotfix

---

# Pull Request e Code Review

Quando um desenvolvedor finaliza uma alteração no código, é recomendado criar um **Pull Request**.

Outro desenvolvedor ou líder técnico realiza um **Code Review**.

Objetivos:

- garantir qualidade do código
    
- identificar falhas de segurança
    
- validar padrões de desenvolvimento
    

---

# SAST – Static Application Security Testing

Ferramentas de **SAST** realizam análise estática do código.

Elas analisam o código sem executar a aplicação.

Exemplos de vulnerabilidades detectadas:

SQL Injection  
XSS  
Credenciais hardcoded  
Uso inseguro de criptografia

Ferramentas:

SonarQube  
Semgrep  
Checkmarx  
Snyk Code

---

# BUILD – Construção da aplicação

Durante o build o código é compilado.

Exemplo Node.js:

```bash
npm install
npm run build
```

Durante essa etapa também são instaladas dependências externas.

---

# Dependências e Supply Chain Attack

Aplicações modernas utilizam bibliotecas externas.

Exemplos:

curl  
wget  
libcurl  
libxml

Essas bibliotecas podem conter vulnerabilidades.

Ataques que exploram dependências externas são chamados de **Supply Chain Attacks**.

---

# SCA – Software Composition Analysis

Ferramentas de **SCA** analisam dependências do projeto.

Elas identificam bibliotecas vulneráveis.

Exemplo:

OWASP Dependency Check

---

# Container Security

Aplicações modernas frequentemente utilizam containers como Docker.

![Image](https://dz2cdn1.dzone.com/storage/temp/10561741-vm-container-figure1.jpg)

![Image](https://miro.medium.com/1%2Av-BncAkY0kE9vlPki5P--Q.png)

![Image](https://www.researchgate.net/publication/344449717/figure/fig1/AS%3A1000674766635009%401615590864555/Container-security-network-configuration-diagram.jpg)

![Image](https://securitypatterns.io/images/02-container/solution-build.png)

Ferramentas utilizadas para scan de containers:

Trivy  
Aqua Security  
Anchore

Exemplo:

```bash
trivy image minha-aplicacao
```

---

# TEST – Testes de segurança

Nesta etapa são realizados testes dinâmicos na aplicação.

## DAST – Dynamic Application Security Testing

Ferramentas DAST atacam a aplicação em execução.

Exemplo:

```
https://site.com?id=1
```

Ferramentas testam vulnerabilidades como:

SQL Injection  
XSS  
IDOR

Ferramentas comuns:

OWASP ZAP  
Burp Suite  
Nuclei

---

# RELEASE – Publicação do artefato

Após o build, o artefato da aplicação é armazenado em um repositório.

Exemplos:

Artifactory  
Nexus  
Docker Registry

Durante essa etapa é gerado um **hash criptográfico** do artefato.

Exemplo:

SHA256

Esse hash garante a **integridade do artefato**.

Isso evita ataques onde um invasor substitui a imagem original por uma imagem maliciosa.

---

# DEPLOY – Implantação

A implantação geralmente ocorre por meio de pipelines **CI/CD**.

CI – Continuous Integration  
CD – Continuous Delivery

![Image](https://www.infracloud.io/assets/img/blog/devsecops-pipeline/devsecops-pipeline-diagram.webp)

![Image](https://www.paloaltonetworks.com.br/content/dam/pan/en_US/images/cyberpedia/various-steps-in-the-ci-cd-pipeline.png?imwidth=480)

![Image](https://media.licdn.com/dms/image/v2/D4E12AQEm0l2S0hE9vw/article-inline_image-shrink_400_744/article-inline_image-shrink_400_744/0/1721195687948?e=2147483647&t=6oMS98zrFPtrR-wkHKz3RD_XLpPYvU7wTpVQcEzujYA&v=beta)

![Image](https://dz2cdn1.dzone.com/storage/temp/17279177-getting-started-cicd-pipe-sec-figure-3-2023.png)

Durante o deploy podemos criar regras de segurança.

Exemplos:

não permitir container rodando como root  
não permitir deploy com vulnerabilidade crítica  
não permitir deploy sem logs

Essas políticas são chamadas de **Workload Security Policies**.

---

# OPERATE – Operação da aplicação

Após o deploy, mecanismos de proteção devem ser aplicados.

Exemplos:

WAF  
WAAP  
RASP

Eles ajudam a bloquear ataques direcionados à aplicação.

Exemplos de ataques:

SQL Injection  
XSS  
IDOR

---

# MONITORAMENTO

Após a aplicação entrar em produção, é necessário monitorar seu comportamento.

Ferramentas comuns:

APM – Application Performance Monitoring  
ASM – Attack Surface Management

ASM identifica ativos expostos na internet e possíveis vulnerabilidades.

---

# OWASP Proactive Controls

Controles recomendados para desenvolvedores:

Define Security Requirements  
Leverage Security Frameworks  
Secure Database Access  
Encode and Escape Data  
Validate All Inputs  
Implement Digital Identity  
Enforce Access Controls  
Protect Data Everywhere  
Implement Security Logging and Monitoring  
Handle Errors and Exceptions

---

# OWASP SAMM – Avaliação de Maturidade

OWASP SAMM permite medir a maturidade da segurança no desenvolvimento.

Domínios:

Governance  
Design  
Implementation  
Verification  
Operations

![Image](https://res.cloudinary.com/snyk/image/upload/f_auto%2Cw_2560%2Cq_auto/v1729698442/OWASP_Blog.png)

![Image](https://owasp.org/www-project-samm/assets/images/OWASP-SAMM-model-800.png)

![Image](https://owaspsamm.org//img/pages/SAMM_v2_diagram.svg)

![Image](https://owaspsamm.org//img/pages/SAMM_v2.svg)

Cada domínio recebe uma pontuação que representa o nível de maturidade da organização.

---

# Conclusão

A segurança de aplicações deve ser integrada desde o início do desenvolvimento.

A adoção de práticas como:

SSDLC  
DevSecOps  
OWASP SAMM  
OWASP ASVS

permite reduzir riscos e aumentar significativamente a segurança das aplicações.

