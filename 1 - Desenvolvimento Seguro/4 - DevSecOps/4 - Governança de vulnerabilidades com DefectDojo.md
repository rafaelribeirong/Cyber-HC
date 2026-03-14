# Governança de vulnerabilidades com DefectDojo

A governança de vulnerabilidades é o processo de **centralizar, organizar, priorizar e acompanhar vulnerabilidades identificadas durante testes de segurança**. Em ambientes modernos de DevSecOps, diversas ferramentas geram resultados de segurança, como scanners SAST, DAST, SCA e ferramentas de infraestrutura.

Sem uma plataforma de gestão, essas vulnerabilidades acabam ficando espalhadas em diferentes relatórios e ferramentas, dificultando a priorização e o acompanhamento das correções.

O **DefectDojo** é uma plataforma open source criada para resolver esse problema. Ele permite centralizar resultados de diferentes ferramentas de segurança em um único sistema e gerenciar todo o ciclo de vida das vulnerabilidades.

---

# O que é DefectDojo

![Image](https://docs.defectdojo.com/images/dashboard.png)

![Image](https://wazuh.com/uploads/2024/12/defectdojo-findings-page.png)

![Image](https://img2.helpnetsecurity.com/posts2025/defectdojo-650.webp)

![Image](https://raw.githubusercontent.com/DefectDojo/django-DefectDojo/dev/docs/assets/images/screenshot1.png)

DefectDojo é uma plataforma de **Application Security Posture Management (ASPM)** focada em centralizar e gerenciar vulnerabilidades identificadas por diferentes ferramentas de segurança.

Ele permite importar resultados de scanners automáticos, organizar vulnerabilidades por aplicação e acompanhar o processo de correção.

A ferramenta também facilita a integração com pipelines de DevSecOps, permitindo que resultados de scans sejam automaticamente enviados para a plataforma.

---

# Objetivo da governança de vulnerabilidades

O principal objetivo da governança de vulnerabilidades é garantir que os problemas identificados em testes de segurança sejam efetivamente tratados.

Esse processo envolve diversas etapas, como:

identificação de vulnerabilidades  
classificação e priorização de riscos  
atribuição de responsáveis  
acompanhamento da correção  
validação da mitigação

Uma plataforma como o DefectDojo ajuda a estruturar esse processo de forma organizada.

---

# Fluxo de governança de vulnerabilidades

![Image](https://www.bitsight.com/sites/default/files/2023/03/09/Vulnerability%20Management%20Lifecycle.png)

![Image](https://docs.contrastsecurity.com/en/image/uuid-e8c52965-f198-6889-adf3-5212cf2761df.png)

![Image](https://blog.gitguardian.com/content/images/2024/04/Vulnerability-Management-Lifecycle-in-DevSecOps--1-.png)

![Image](https://civo-com-assets.ams3.digitaloceanspaces.com/content_images/2361.blog.png?1688384083=)

O ciclo de governança de vulnerabilidades normalmente segue algumas etapas principais.

Primeiro ocorre a execução dos testes de segurança, onde ferramentas automatizadas ou testes manuais identificam possíveis vulnerabilidades.

Os resultados desses testes são então enviados para uma plataforma de gestão, onde as vulnerabilidades são organizadas e classificadas.

Após essa etapa, as vulnerabilidades são analisadas e priorizadas com base em critérios como severidade, impacto e facilidade de exploração.

Em seguida, as vulnerabilidades são atribuídas às equipes responsáveis pela correção.

Após a correção, os testes são executados novamente para validar se o problema foi realmente resolvido.

---

# Como o DefectDojo organiza vulnerabilidades

O DefectDojo utiliza uma estrutura hierárquica para organizar as informações de segurança.

Essa estrutura normalmente inclui:

Product  
Engagement  
Test  
Finding

Product representa uma aplicação ou sistema dentro da organização.

Engagement representa uma atividade de segurança realizada naquele produto, como um pentest ou uma varredura automatizada.

Test representa um teste específico realizado dentro daquele engagement.

Finding representa a vulnerabilidade identificada durante o teste.

Essa estrutura ajuda a organizar os resultados de forma clara e rastreável.

---

# Integração com ferramentas de segurança

![Image](https://wazuh.com/uploads/2024/12/workflow-of-the-Wazuh-integration-with-defectdojo.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2AFw9EBPT2tlmCCcSqKIoh1A.jpeg)

![Image](https://blog.gitguardian.com/content/images/2024/04/Vulnerability-Management-Lifecycle-in-DevSecOps--1-.png)

![Image](https://assets.bytebytego.com/diagrams/0060-what-is-devsecops.png)

Uma das principais vantagens do DefectDojo é a capacidade de integrar resultados de diversas ferramentas de segurança.

Entre as ferramentas que podem ser integradas estão:

scanners SAST  
scanners DAST  
ferramentas de análise de dependências  
scanners de infraestrutura  
resultados de pentests

Esses resultados podem ser importados manualmente ou automaticamente através de pipelines de CI/CD.

Isso permite consolidar todos os resultados de segurança em um único local.

---

# Priorização de vulnerabilidades

Após a importação das vulnerabilidades, o DefectDojo permite priorizar os riscos com base em diferentes critérios.

Entre os fatores utilizados para priorização estão:

severidade da vulnerabilidade  
impacto no negócio  
facilidade de exploração  
exposição do sistema

Essa priorização permite que as equipes foquem primeiro nas vulnerabilidades que representam maior risco.

---

# Workflow de correção

A plataforma também permite acompanhar o processo de correção das vulnerabilidades.

Quando uma vulnerabilidade é identificada, ela pode ser atribuída a uma equipe responsável pela correção.

Durante o processo de correção, o status da vulnerabilidade pode ser atualizado.

Entre os estados comuns estão:

aberta  
em correção  
mitigada  
aceita como risco  
falso positivo

Esse controle ajuda a acompanhar o progresso da remediação.

---

# Benefícios do uso do DefectDojo

A utilização de uma plataforma como o DefectDojo traz diversos benefícios para a gestão de vulnerabilidades.

Entre eles estão:

centralização de resultados de segurança  
melhor organização das vulnerabilidades  
facilidade na priorização de riscos  
rastreamento do processo de correção  
integração com pipelines DevSecOps

Esses benefícios ajudam a tornar o processo de segurança mais estruturado e eficiente.

---

# Conclusão

A governança de vulnerabilidades é uma etapa fundamental para garantir que os problemas identificados em testes de segurança sejam tratados de forma adequada.

Ferramentas como o DefectDojo permitem centralizar resultados de diferentes scanners e estruturar o processo de gestão de vulnerabilidades dentro da organização.

Ao integrar essa plataforma com pipelines de DevSecOps, torna-se possível automatizar grande parte do processo de identificação, priorização e correção de vulnerabilidades, aumentando a eficiência e a maturidade da segurança no desenvolvimento de software.