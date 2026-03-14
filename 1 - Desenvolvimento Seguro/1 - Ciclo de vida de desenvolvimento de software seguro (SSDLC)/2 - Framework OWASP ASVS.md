[OWASP Application Security Verification Standard (ASVS) | OWASP Foundation](https://owasp.org/www-project-application-security-verification-standard/)

# OWASP Application Security Verification Standard (ASVS)

O **OWASP Application Security Verification Standard (ASVS)** é um framework desenvolvido pela OWASP para estabelecer um padrão de verificação de segurança em aplicações. Ele fornece um conjunto estruturado de requisitos que permitem avaliar se uma aplicação foi projetada, desenvolvida e implantada seguindo boas práticas de segurança.

Diferentemente de guias conceituais, o ASVS é **orientado à verificação prática**. Isso significa que cada requisito pode ser testado, auditado ou validado durante revisões de segurança, testes de aplicação ou auditorias técnicas.

O objetivo principal do ASVS é servir como uma base comum entre equipes técnicas, desenvolvedores, auditores e especialistas em segurança para garantir que os controles necessários estejam presentes em uma aplicação.

---

# Visão geral do ASVS

![Image](https://pensivesecurity.io/blog/images/thc/owasp-asvs.png)

![Image](https://devguide.owasp.org/assets/images/logos/asvs.png)

![Image](https://owasp.org/www-project-integration-standards/writeups/owasp_in_sdlc/images/sdlc_diag.png)

![Image](https://sempf.net/FILES%2F2015%2F01%2FUntitled.png.axdx)

O ASVS organiza os requisitos de segurança em domínios técnicos e define níveis de verificação que determinam o grau de segurança esperado para uma aplicação.

Cada requisito descreve um controle que deve existir na aplicação ou no processo de desenvolvimento. Esses controles podem ser avaliados por meio de testes de segurança, revisão de código, análise de arquitetura ou verificação de configuração.

Em um projeto de segurança de aplicações, o uso do ASVS normalmente segue uma sequência lógica. Primeiro define-se o nível de verificação necessário para o sistema. Em seguida os requisitos correspondentes são analisados e testados. Parte dessas validações pode ser feita com ferramentas automatizadas, porém uma grande parte exige análise manual especializada.

---

# Como o ASVS funciona

O ASVS funciona como um catálogo de requisitos de segurança que podem ser utilizados para verificar se uma aplicação atende a um nível mínimo de proteção.

Cada requisito possui um identificador e uma descrição clara do controle esperado. Durante uma avaliação de segurança, o analista verifica se aquele requisito foi implementado corretamente e registra evidências da verificação.

Embora algumas verificações possam ser automatizadas, o próprio projeto ASVS destaca que a maioria das validações exige testes manuais. Isso ocorre porque muitos controles envolvem lógica de negócio, decisões arquiteturais ou análise de código que não podem ser avaliadas apenas por ferramentas.

---

# Utilização do ASVS no ciclo de vida do software

## Orientação para arquitetura de segurança

![Image](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2023/11/22/img2-8.png)

![Image](https://nocomplexity.com/documents/securityarchitecture/_images/image_8_OSA.png)

![Image](https://www.researchgate.net/publication/224182618/figure/fig1/AS%3A566692936126464%401512121532861/llustration-of-the-WSAN4CIP-secure-software-architecture-It-allows-different-operating.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A74q4li6V_7I2N6SnqY9yIg.jpeg)

O ASVS pode ser utilizado ainda na fase de arquitetura da aplicação. Os requisitos presentes no framework ajudam arquitetos e desenvolvedores a projetar sistemas que já nascem com controles de segurança adequados.

Durante essa fase, os requisitos do ASVS servem como referência para definir como mecanismos críticos devem ser implementados. Isso inclui aspectos como autenticação de usuários, gestão de sessões, criptografia de informações sensíveis, controle de permissões e validação adequada de dados de entrada.

Ao considerar esses elementos desde o design do sistema, muitas vulnerabilidades comuns podem ser evitadas antes mesmo da implementação.

---

## Revisão de código seguro

![Image](https://s3.us-east-1.amazonaws.com/static-production.uprootsecurity.com/website/strapi-content/uploads/Secure_Code_Review_Process_e2846b7db4.png)

![Image](https://cdn.prod.website-files.com/6407b983039e75f8fc39d439/64e33b8120624424875647f9_SecurityCodeReview.svg)

![Image](https://www.hackthebox.com/storage/blog/KAOku2OQ5HT8LfAnBKv2di6TBxbCbfrU.jpg)

![Image](https://docs.developer.tech.gov.sg/docs/secure-code-review-guidelines/code_review_checklist_final.png)

Durante revisões de código, o ASVS pode ser utilizado como um guia para identificar implementações inseguras. Os requisitos do framework ajudam a direcionar a análise do código para pontos críticos que frequentemente originam vulnerabilidades.

A verificação pode incluir a análise de como a aplicação processa entradas do usuário, como dados sensíveis são armazenados, como sessões são gerenciadas e como erros são tratados. Também permite avaliar se controles de autorização estão implementados corretamente e se a aplicação impede acessos indevidos a funcionalidades restritas.

Essa abordagem transforma o ASVS em um checklist técnico que ajuda equipes de desenvolvimento e segurança a identificar problemas antes da aplicação ser disponibilizada em produção.

---

## Treinamento em desenvolvimento seguro

![Image](https://www.procheckup.com/media/omffqx1t/a-group-of-developers-engaged-in-a-secure-coding-workshop.webp?height=429&rmode=max&width=750)

![Image](https://www.fortinet.com/content/dam/fortinet/images/cyberglossary/8-tools-of-application-security.png)

![Image](https://owasp.org/www-project-application-security-awareness-campaigns/assets/images/top_ten/00.jpg)

![Image](https://owasp.org/www-project-application-security-awareness-campaigns/assets/images/sec_roles/appsec.jpg)

O ASVS também pode ser utilizado como base para programas de treinamento em desenvolvimento seguro. Os requisitos presentes no framework refletem problemas recorrentes encontrados em aplicações reais, o que o torna um material útil para capacitação técnica.

Ao estudar os controles do ASVS, desenvolvedores aprendem como evitar vulnerabilidades comuns e passam a compreender melhor como implementar mecanismos de segurança adequados dentro das aplicações que desenvolvem.

Essa abordagem ajuda a incorporar segurança no processo de desenvolvimento desde o início do ciclo de vida do software.

---

## Base para testes automatizados

![Image](https://sunbytes.io/app/uploads/2025/07/DevSecOps-Pipeline-Post--scaled.webp)

![Image](https://www.paloaltonetworks.com/content/dam/pan/en_US/images/cyberpedia/CI_CD%20Security%20-%201.png?imwidth=480)

![Image](https://miro.medium.com/1%2A8NeLQL06BEoeesAjI9cFOw.png)

![Image](https://cdn.prod.website-files.com/5db35de024bb988f5fb4e168/6616842a741edaf919f6e7b1_61b1d60d59d29423d6f9dd12_yrTf3reuwAPYyzK5XPyx6j9ROBZ9tJUT7G1oHF7h2OH342EM8foAbAXkSp9uKC_JT-MyaquXDz7A93ZtsC7LpZNtAOepqRw8qiQfZnVwpps8RF3QbLdqOho9KMg9FB7y1YI_9ouy.png)

Alguns requisitos do ASVS podem ser verificados automaticamente por ferramentas de segurança integradas ao pipeline de desenvolvimento.

Ferramentas de análise estática, análise dinâmica e scanners de dependência podem ajudar a verificar determinados controles de segurança. Entretanto, esses testes automatizados não substituem a análise manual. Eles funcionam como um complemento que ajuda a detectar problemas rapidamente durante o desenvolvimento.

Integrar essas verificações ao processo de integração contínua permite identificar falhas de segurança ainda nas fases iniciais do desenvolvimento.

---

## Segurança em desenvolvimento ágil

![Image](https://miro.medium.com/1%2AtoOxi7_uIkSUR8qjXGQIYQ.png)

![Image](https://assets.community.aws/a/2ujxrJlEIpsZns5GkMTJ68vs0kn/devs.webp?imgSize=1000x697)

![Image](https://nullsweep.com/content/images/2019/04/security_with_agile_development.png)

![Image](https://www.researchgate.net/publication/321886359/figure/fig2/AS%3A572987033047040%401513622162687/McGraws-Secure-Software-Development-Life-Cycle-Process.png)

Equipes que utilizam metodologias ágeis também podem incorporar o ASVS em suas práticas de desenvolvimento.

Os requisitos do framework podem ser transformados em critérios de aceitação dentro das histórias de usuário. Dessa forma, cada funcionalidade desenvolvida precisa atender aos controles de segurança definidos antes de ser considerada concluída.

Essa prática permite integrar segurança ao fluxo de desenvolvimento contínuo sem comprometer a agilidade do processo.

---

## Avaliação e aquisição de software

![Image](https://www.leanix.net/hs-fs/hubfs/Downloads/Download-Files/EN/Templates/vendor-xls%402x.jpg?height=2462&name=vendor-xls%402x.jpg&width=2784)

![Image](https://cdn.prod.website-files.com/606250622ea3c948117b5755/67b8a2e7a968545c937bee4c_4%20-%20CRITERIA.png)

![Image](https://images.template.net/152520/it-procurement-compliance-checklist-sheet-template-2qu6z.png)

![Image](https://mammothsecurity.com/uploads/editor/blobid1743092115527.webp)

O ASVS também pode ser utilizado como referência para avaliar a segurança de softwares adquiridos de terceiros.

Organizações podem exigir que fornecedores demonstrem conformidade com determinado nível do ASVS antes da contratação. Isso cria um critério técnico para avaliar se o software possui controles adequados de segurança.

Esse uso do ASVS ajuda empresas a reduzir riscos associados à aquisição de aplicações externas.

---

# Níveis de verificação do ASVS

O ASVS define três níveis de verificação que representam diferentes graus de segurança.

---

## Nível 1

O nível 1 é voltado para aplicações que possuem requisitos básicos de segurança.

Ele busca garantir proteção contra vulnerabilidades simples e amplamente conhecidas, incluindo aquelas listadas no OWASP Top 10. Esse nível pode ser verificado principalmente por meio de testes externos e não exige necessariamente acesso ao código-fonte da aplicação.

Aplicações públicas simples ou serviços com baixo impacto geralmente são avaliados nesse nível.

---

## Nível 2

O nível 2 oferece proteção contra a maioria dos riscos associados ao desenvolvimento de software e é considerado o nível recomendado para a maioria das aplicações corporativas.

Ele exige controles de segurança mais robustos e uma verificação mais aprofundada da implementação dos mecanismos de proteção.

Aplicações que lidam com dados de usuários ou que fazem parte de sistemas corporativos normalmente devem atender a esse nível.

---

## Nível 3

O nível 3 é destinado a aplicações críticas que lidam com dados sensíveis ou suportam operações essenciais para a organização.

Nesse nível, espera-se uma verificação muito mais rigorosa dos controles de segurança, incluindo revisões detalhadas de arquitetura, validações profundas de lógica de negócio e testes extensivos.

Sistemas financeiros, governamentais ou que suportam infraestrutura crítica geralmente precisam atender a esse nível de verificação.

---

# Domínios de controle do ASVS

O ASVS organiza seus requisitos em **14 domínios principais de controle**, cada um abordando um aspecto específico da segurança de aplicações.

Esses domínios cobrem áreas como arquitetura da aplicação, autenticação, gestão de sessões, controle de acesso, validação de dados, criptografia, proteção de dados sensíveis, comunicação segura, tratamento de erros, registro de eventos, lógica de negócio, manipulação de arquivos, segurança de APIs e configuração segura da aplicação.

Cada domínio contém diversos subcontroles que descrevem de forma detalhada os requisitos que devem ser verificados para garantir que a aplicação esteja protegida contra vulnerabilidades comuns.
