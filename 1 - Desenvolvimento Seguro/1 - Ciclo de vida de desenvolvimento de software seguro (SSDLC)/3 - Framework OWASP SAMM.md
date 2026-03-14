https://owasp.org/www-project-samm/

# OWASP SAMM (Software Assurance Maturity Model)

O **OWASP SAMM** é um framework criado pela OWASP para ajudar organizações a **avaliar, estruturar e evoluir a segurança no desenvolvimento de software**.

Enquanto o ASVS foca em **verificar se uma aplicação atende requisitos de segurança**, o SAMM tem um objetivo diferente: ele ajuda a organização a **construir um programa de segurança de software dentro do processo de desenvolvimento**.

O SAMM fornece um modelo estruturado para que empresas possam:

- entender o nível atual de maturidade em segurança de software
    
- definir melhorias realistas e progressivas
    
- medir evolução ao longo do tempo
    
- integrar segurança ao ciclo de desenvolvimento
    

Ele é projetado para ser **adaptável aos riscos específicos de cada organização**, permitindo que cada empresa construa um programa de segurança proporcional ao seu contexto tecnológico e de negócio.

---

# Estrutura geral do OWASP SAMM

![Image](https://owasp.org/www-project-samm/assets/images/OWASP-SAMM-model-800.png)

![Image](https://framerusercontent.com/images/8Z4oinFh88a967fzezGr2shy4.png?height=884&width=1920)

![Image](https://res.cloudinary.com/snyk/image/upload/v1729698442/OWASP_Blog.png)

O SAMM é organizado em **cinco pilares principais**, que representam áreas fundamentais do desenvolvimento seguro.

Cada pilar contém **práticas de segurança**, e cada prática possui **níveis de maturidade** que permitem medir a evolução da organização.

Os cinco pilares são:

- Governança
    
- Design
    
- Implementação
    
- Verificação
    
- Operação
    

Cada um deles cobre um conjunto de atividades relacionadas à segurança do software ao longo do ciclo de vida da aplicação.

---

# Pilar 1 – Governança

![Image](https://www.informit.com/content/images/chap2_9780134772806/elementLinks/02fig01_alt.jpg)

![Image](https://cdn1-public.infotech.com/infographics/uploads/43429/DESIGN-4714-Security_Governance_Methodology-1220w_sidenav.jpg?1693948718=)

![Image](https://www.slidegeeks.com/media/catalog/product/cache/560x315/I/n/Information_Security_Risk_Evaluation_Risk_Management_Dashboard_For_Information_Security_Summary_PDF_Slide_1.jpg)

![Image](https://www.inetsoft.com/images/website/data-governance-dashboard.png)

O pilar de governança trata da **gestão estratégica da segurança de software dentro da organização**.

Ele define como a segurança é planejada, medida e integrada às decisões corporativas.

Dentro desse pilar existem três práticas principais.

### Estratégia e métricas

Esta prática define como a organização estabelece objetivos de segurança e mede seu desempenho.

Inclui atividades como:

- definição de metas de segurança
    
- definição de indicadores de desempenho
    
- acompanhamento da evolução de maturidade
    
- alinhamento da segurança com objetivos do negócio
    

O objetivo é garantir que segurança de software não seja apenas uma atividade técnica isolada, mas sim parte da estratégia da organização.

---

### Política e compliance

Essa prática trata da definição de **políticas e requisitos de segurança que devem ser seguidos pelas equipes de desenvolvimento**.

Isso inclui:

- criação de políticas de desenvolvimento seguro
    
- definição de requisitos mínimos de segurança
    
- integração com requisitos regulatórios
    
- auditoria de conformidade
    

A política de segurança serve como base para orientar decisões técnicas e operacionais dentro dos projetos de software.

---

### Educação e orientação

Essa prática foca no desenvolvimento de conhecimento e conscientização em segurança.

Inclui:

- treinamento de desenvolvedores
    
- capacitação de arquitetos
    
- programas de awareness em segurança
    
- disponibilização de guias de desenvolvimento seguro
    

O objetivo é garantir que as equipes possuam conhecimento suficiente para implementar controles de segurança adequadamente.

---

# Pilar 2 – Design

![Image](https://www.researchgate.net/publication/224182618/figure/fig1/AS%3A566692936126464%401512121532861/llustration-of-the-WSAN4CIP-secure-software-architecture-It-allows-different-operating.png)

![Image](https://images.prismic.io/guardrails-01/YzkxYTU4MGMtYmRiZC00ZTg0LWJhM2EtODJjOGI5NDYwMTQ0_threatmodeling-1-1024x600.jpg?auto=compress%2Cformat&h=600&rect=0%2C0%2C1024%2C600&w=1024)

![Image](https://assets.nextwebi.com/assets/images/services/Services-img/Security-Architecture-review%28Build-%26-Production-phases%29.png)

![Image](https://lirp.cdn-website.com/97773f16/dms3rep/multi/opt/network%2Bdesign%2Band%2Barchitecture-640w.PNG)

O pilar de design aborda como a segurança é considerada **durante a fase de arquitetura e planejamento da aplicação**.

Ele busca garantir que vulnerabilidades estruturais sejam evitadas ainda antes da implementação.

As práticas principais deste pilar são as seguintes.

### Avaliação de ameaças

Envolve a identificação e análise de possíveis ameaças que podem afetar o sistema.

Isso inclui atividades como:

- modelagem de ameaças
    
- identificação de vetores de ataque
    
- análise de superfícies de ataque
    
- priorização de riscos
    

Essa prática permite compreender quais riscos precisam ser mitigados durante o desenvolvimento.

---

### Arquitetura segura

Trata da definição de uma arquitetura que incorpore controles de segurança desde o início.

Inclui:

- definição de mecanismos de autenticação
    
- definição de controle de acesso
    
- uso de criptografia adequada
    
- separação de componentes críticos
    

Uma arquitetura segura reduz significativamente a probabilidade de vulnerabilidades estruturais.

---

### Requisitos de segurança

Esta prática define quais requisitos de segurança devem ser atendidos pelas aplicações.

Esses requisitos podem incluir:

- requisitos de autenticação
    
- requisitos de proteção de dados
    
- requisitos de logging
    
- requisitos de comunicação segura
    

Eles são definidos durante a fase de análise de requisitos do projeto.

---

# Pilar 3 – Implementação

![Image](https://media.licdn.com/dms/image/v2/D4D12AQEfFwq64mjnmQ/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1711124770800?e=2147483647&t=Tta9sYiVAsHpt5h17Eh8h4EO5LUMU4gCLyFDODFNZyY&v=beta)

![Image](https://res.cloudinary.com/snyk/image/upload/v1646605793/wordpress-sync/three-pillars-for-secure-coding-learn.png)

![Image](https://miro.medium.com/1%2AtoOxi7_uIkSUR8qjXGQIYQ.png)

![Image](https://res.cloudinary.com/snyk/image/upload/f_auto%2Cw_2560%2Cq_auto/f_auto/q_auto/v1613516749/wordpress-sync/ssdlc-2.png)

O pilar de implementação trata das práticas de segurança aplicadas **durante a escrita do código**.

Ele busca garantir que o software seja desenvolvido seguindo boas práticas de segurança.

As principais práticas incluem:

### Desenvolvimento seguro

Define padrões e práticas que devem ser seguidos durante a codificação.

Inclui:

- padrões de codificação segura
    
- validação adequada de dados
    
- proteção contra injeção de código
    
- tratamento correto de erros
    

---

### Gestão de dependências

Essa prática busca controlar os riscos associados a bibliotecas externas e componentes de terceiros.

Inclui:

- monitoramento de vulnerabilidades em dependências
    
- atualização de bibliotecas
    
- análise de riscos em componentes externos
    

---

### Segurança no ambiente de desenvolvimento

Trata da proteção do próprio ambiente onde o software é desenvolvido.

Inclui:

- controle de acesso ao repositório
    
- proteção do pipeline de build
    
- segurança das ferramentas de desenvolvimento
    

---

# Pilar 4 – Verificação

![Image](https://www.datocms-assets.com/75231/1740769858-security-testing-techniques.png)

![Image](https://miro.medium.com/1%2ALZnRG6nlVid-tHQauJsz4g.png)

![Image](https://cdn-blog.getastra.com/2024/08/77901847-dynamic-application-security-testing-process.png)

![Image](https://www.blackduck.com/content/dam/black-duck/en-us/infographics/sast-vs-dast.jpg)

O pilar de verificação envolve atividades destinadas a **identificar vulnerabilidades antes que o software seja liberado para produção**.

As práticas desse pilar incluem:

### Testes de segurança

Abrange testes técnicos destinados a identificar vulnerabilidades na aplicação.

Podem incluir:

- análise estática de código (SAST)
    
- análise dinâmica (DAST)
    
- testes de penetração
    
- scanners de segurança
    

---

### Revisão de arquitetura

Envolve a análise da arquitetura da aplicação para identificar possíveis falhas estruturais.

Essa prática permite identificar problemas que não seriam detectados por ferramentas automatizadas.

---

### Revisão de código

Consiste na análise manual do código fonte para identificar vulnerabilidades ou implementações inseguras.

Esse processo é essencial para detectar falhas relacionadas à lógica de negócio ou erros de implementação.

---

# Pilar 5 – Operação

![Image](https://cdn.prod.website-files.com/5ff66329429d880392f6cba2/6787cbaf01695fa24edff5ca_6418a2ef0ff9b6424d29e410_Security%2520Operations%2520Center.jpeg)

![Image](https://cdn1-public.infotech.com/infographics/uploads/45454/DESIGN-5184__Develop_and_Implement_a_Security_Incident_Management_program_-_Refresh_1920w_original.png?1707218336=)

![Image](https://d1.awsstatic.com/onedam/marketing-channels/website/aws/en_US/product-categories/security-identity-compliance/security/approved/images/3decd49f8710b2fc2a9d95e7504d7373-aws-cncf-falco-security-hub-container-runtime-architecture-diagram-2940x1707.5853cbdb2249c28bc8fc0a4b156d7b40756e487c.png)

![Image](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2021/12/09/image1-v2-1.jpg)

O pilar de operação trata da segurança da aplicação **após sua implantação em produção**.

Ele garante que a aplicação continue protegida durante sua operação.

As principais práticas incluem:

### Monitoramento de segurança

Consiste em monitorar a aplicação em busca de comportamentos suspeitos ou incidentes.

Inclui:

- monitoramento de logs
    
- detecção de ataques
    
- análise de eventos de segurança
    

---

### Gestão de vulnerabilidades

Trata do processo contínuo de identificação e correção de vulnerabilidades após a implantação da aplicação.

Inclui:

- scanners de vulnerabilidade
    
- programas de bug bounty
    
- correção contínua de falhas
    

---

### Resposta a incidentes

Define como a organização deve responder quando um incidente de segurança ocorre.

Inclui:

- processos de investigação
    
- contenção de incidentes
    
- recuperação de sistemas
    

---

# Como usar o OWASP SAMM

O SAMM pode ser utilizado de diferentes formas para avaliar a maturidade de segurança de uma organização.

Uma abordagem comum consiste em utilizar o framework como **questionário de avaliação**. Nesse caso, especialistas em segurança analisam cada prática definida no modelo e verificam se a organização implementa os controles correspondentes.

Outra abordagem consiste em conduzir **entrevistas estruturadas com equipes técnicas**, como desenvolvedores, arquitetos, gestores de tecnologia e profissionais de segurança.

Durante essas entrevistas são avaliados aspectos como processos de desenvolvimento, práticas de segurança existentes, ferramentas utilizadas e mecanismos de controle adotados.

Também é possível realizar uma **autoavaliação interna**, na qual a própria organização utiliza o framework para identificar lacunas e definir um plano de melhoria.

Independentemente da abordagem utilizada, é fundamental compreender o contexto da organização avaliada. O SAMM não deve ser aplicado apenas como um checklist técnico. Ele deve considerar fatores como o tipo de aplicação desenvolvida, o modelo de negócio, os riscos envolvidos e a maturidade tecnológica da organização.

Quando aplicado corretamente, o OWASP SAMM permite construir um **programa de segurança de software estruturado, mensurável e alinhado aos riscos do negócio**, promovendo melhorias contínuas na segurança das aplicações desenvolvidas pela organização.