# Visão geral do DefectDojo

O **DefectDojo** é uma plataforma open source utilizada para **gestão de vulnerabilidades e centralização de resultados de testes de segurança**. Ele foi projetado para ajudar equipes de segurança, desenvolvimento e operações a organizar e acompanhar vulnerabilidades identificadas em aplicações e infraestruturas.

Em ambientes modernos de DevSecOps, diversas ferramentas de segurança são utilizadas, como scanners SAST, DAST, SCA e ferramentas de análise de infraestrutura. Cada uma dessas ferramentas gera relatórios com vulnerabilidades identificadas. Sem uma plataforma centralizada, essas informações ficam distribuídas em diferentes sistemas, dificultando a priorização e o acompanhamento das correções.

O DefectDojo resolve esse problema ao funcionar como um **hub central de gestão de vulnerabilidades**, consolidando resultados de diferentes ferramentas e permitindo o gerenciamento completo do ciclo de vida das falhas de segurança.

---

# Interface e funcionamento da plataforma

![Image](https://docs.defectdojo.com/images/dashboard.png)

![Image](https://docs.defectdojo.com/images/similar_finding_1.png)

![Image](https://raw.githubusercontent.com/DefectDojo/Documentation/master/doc/img/screenshot1.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ACU3_mmtwhJhsYq0umRPYqA.png)

A plataforma possui uma interface web onde é possível visualizar vulnerabilidades identificadas, acompanhar o status de correções e gerar relatórios de segurança.

A interface permite filtrar vulnerabilidades por diversos critérios, como severidade, aplicação afetada, data do teste ou status da correção.

Essa visão centralizada facilita o trabalho das equipes de segurança ao permitir identificar rapidamente os riscos mais críticos.

---

# Objetivo do DefectDojo

O objetivo principal do DefectDojo é **organizar e gerenciar vulnerabilidades ao longo de todo o ciclo de desenvolvimento de software**.

Ele permite que vulnerabilidades identificadas por diferentes ferramentas sejam consolidadas em uma única plataforma, facilitando a análise e a tomada de decisão.

Além disso, a plataforma também permite acompanhar o processo de correção dessas vulnerabilidades, garantindo que problemas de segurança sejam efetivamente tratados.

---

# Estrutura organizacional dentro da plataforma

![Image](https://docs.defectdojo.com/images/dd-hierarchy.png)

![Image](https://www.slideteam.net/media/catalog/product/cache/1280x720/b/u/business_application_security_testing_flow_chart_slide01.jpg)

![Image](https://www.sei.cmu.edu/media/images/10apptools_scanlon_figure1.original.jpg)

O DefectDojo organiza as informações de segurança utilizando uma estrutura hierárquica.

Essa estrutura normalmente inclui quatro níveis principais.

Product  
Representa uma aplicação ou sistema que está sendo analisado.

Engagement  
Representa uma atividade de segurança realizada naquele produto, como um pentest, auditoria ou varredura automatizada.

Test  
Representa um teste específico executado dentro do engagement.

Finding  
Representa a vulnerabilidade identificada durante aquele teste.

Essa estrutura permite organizar resultados de segurança de forma clara e rastreável.

---

# Integração com ferramentas de segurança

![Image](https://wazuh.com/uploads/2024/12/workflow-of-the-Wazuh-integration-with-defectdojo.png)

![Image](https://blog.gitguardian.com/content/images/2024/04/Vulnerability-Management-Lifecycle-in-DevSecOps--1-.png)

![Image](https://civo-com-assets.ams3.digitaloceanspaces.com/content_images/2361.blog.png?1688384083=)

O DefectDojo possui suporte para integração com diversas ferramentas de segurança.

Entre elas estão scanners de código, scanners de vulnerabilidade e ferramentas de análise de dependências.

Alguns exemplos incluem:

ferramentas SAST  
ferramentas DAST  
scanners de infraestrutura  
ferramentas de análise de dependências  
resultados de pentests manuais

Esses resultados podem ser importados manualmente ou automaticamente através de pipelines de CI/CD.

Essa integração permite consolidar informações de segurança provenientes de diferentes fontes.

---

# Gestão do ciclo de vida das vulnerabilidades

O DefectDojo também permite acompanhar todo o ciclo de vida das vulnerabilidades identificadas.

Quando uma vulnerabilidade é encontrada, ela pode ser registrada na plataforma e classificada de acordo com sua severidade.

Em seguida, essa vulnerabilidade pode ser atribuída a uma equipe responsável pela correção.

Durante o processo de remediação, o status da vulnerabilidade pode ser atualizado para refletir o progresso da correção.

Entre os estados mais comuns estão:

aberta  
em correção  
corrigida  
aceita como risco  
falso positivo

Esse acompanhamento ajuda a garantir que as vulnerabilidades sejam tratadas de forma adequada.

---

# Benefícios da utilização do DefectDojo

A utilização do DefectDojo traz diversos benefícios para equipes de segurança e desenvolvimento.

Entre os principais benefícios estão:

centralização dos resultados de segurança  
melhor organização das vulnerabilidades  
facilidade na priorização de riscos  
rastreamento do processo de correção  
integração com pipelines de DevSecOps

Essas características ajudam a tornar o processo de gestão de vulnerabilidades mais eficiente e estruturado.

---

# Conclusão

O DefectDojo é uma plataforma importante para organizações que precisam gerenciar vulnerabilidades de forma estruturada.

Ao centralizar resultados de testes de segurança e permitir o acompanhamento do processo de correção, ele ajuda a transformar relatórios de segurança em ações concretas de melhoria.

Integrado a pipelines de DevSecOps, o DefectDojo contribui para aumentar a maturidade da segurança no desenvolvimento de software e melhorar o controle sobre vulnerabilidades ao longo do ciclo de vida das aplicações.