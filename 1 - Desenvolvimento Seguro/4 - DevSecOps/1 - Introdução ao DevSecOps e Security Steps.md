# Introdução ao DevSecOps e Security Steps

DevSecOps é uma abordagem de desenvolvimento de software que integra segurança diretamente no processo de desenvolvimento e entrega de aplicações. O objetivo é garantir que a segurança seja tratada como parte natural do ciclo de vida do software, e não apenas como uma etapa final antes da implantação.

Tradicionalmente, as equipes de desenvolvimento, operações e segurança trabalhavam de forma separada. Nesse modelo, a segurança era frequentemente aplicada apenas no final do processo, quando a aplicação já estava praticamente pronta. Isso gerava atrasos, retrabalho e aumento de custos para corrigir vulnerabilidades.

DevSecOps surge para resolver esse problema ao incorporar práticas de segurança ao longo de todo o ciclo de desenvolvimento, permitindo que vulnerabilidades sejam identificadas e corrigidas de forma mais rápida e eficiente.

---

# Visão geral do DevSecOps

![Image](https://images.openai.com/static-rsc-3/nXpxefJVsa4CSJcE8bU3IggdJ3Q6Ej_BTFZszTkvNQVSZxchMSoV25MMp81v4w_jkdEyGUNnSgEm8T0AxBWDV_NU8kES-iOsYdOtaKjkegw?purpose=fullsize&v=1)

![Image](https://www.xenonstack.com/hubfs/devsecops-pipeline.png)

![Image](https://www.watchmantower.com/_next/image?q=75&url=https%3A%2F%2Fcms.watchmantower.com%2Fuploads%2Flarge_devsecops_uptime_security_devops_strategy_5384878d3f.png&w=2048)

![Image](https://framerusercontent.com/images/0ZnN5hhdg8xJxtpI0k1FjpEBIAA.png?height=1330&width=2000)

O conceito de DevSecOps representa a integração entre três áreas principais:

Desenvolvimento  
Operações  
Segurança

Nesse modelo, as equipes trabalham de forma colaborativa para garantir que a segurança esteja presente em todas as fases do ciclo de vida da aplicação.

O DevSecOps também enfatiza o uso de automação para realizar testes de segurança continuamente durante o desenvolvimento.

---

# CI/CD no contexto de DevSecOps

![Image](https://images.openai.com/static-rsc-3/1JssT43dRnj6AmZc9EbXImzBQaSLk1WhEXVOojNss6t_YgTlxYCTq3I6Db7m8irYraKbjg60ChYTiVETgOUyVSEeJcorUjJVvTpLWL4BD6Q?purpose=fullsize&v=1)

![Image](https://images.openai.com/static-rsc-3/zWXJGRIHNxshhFjhTbhFu0iQTl6W_yFcHKgUKCJfb9ZIQfST2ryre7uTXdFVa3uXrgpoq0NKvA1JylyIDl6OiPuzIOh0ZSeNhrUaNjsbEbI?purpose=fullsize&v=1)

![Image](https://assets.bytebytego.com/diagrams/0140-ci-cd-pipeline.png)

![Image](https://ik.imagekit.io/upgrad1/abroad-images/imageCompo/images/1670422280981_DevOps_Pipeline_DiagramKK1LJX.webp?pr-true=)

Para compreender DevSecOps, é necessário entender o conceito de **CI/CD**, que é a base da automação no desenvolvimento moderno.

CI/CD representa duas práticas fundamentais no desenvolvimento de software.

Continuous Integration (CI)  
Continuous Delivery ou Continuous Deployment (CD)

Essas práticas permitem que o código seja desenvolvido, testado e implantado de forma automatizada.

---

# Continuous Integration (CI)

Continuous Integration é o processo de integrar frequentemente mudanças de código em um repositório central.

Sempre que um desenvolvedor realiza um commit no repositório, uma série de processos automáticos é executada.

Esses processos podem incluir:

compilação da aplicação  
execução de testes automatizados  
análise de qualidade de código  
verificação de segurança

Esse modelo permite identificar rapidamente erros ou vulnerabilidades introduzidas no código.

---

# Continuous Delivery e Continuous Deployment (CD)

Continuous Delivery é o processo de preparar automaticamente o software para implantação em produção.

Nesse modelo, o código que passou por todas as verificações da pipeline está sempre pronto para ser implantado.

Continuous Deployment vai um passo além.

Nesse caso, o software é implantado automaticamente em produção sempre que passa por todos os testes da pipeline.

Essas práticas permitem que novas versões da aplicação sejam entregues com maior frequência e menor risco.

---

# O que é um Security Step

Dentro de uma pipeline DevSecOps existem várias etapas responsáveis por validar diferentes aspectos do software.

Um **Security Step** é uma etapa da pipeline responsável por executar verificações de segurança.

Essas etapas são integradas diretamente na pipeline de CI/CD e são executadas automaticamente sempre que o código passa pelo processo de build ou integração.

Esses passos de segurança podem incluir diferentes tipos de testes automatizados.

Entre eles:

análise estática de código  
análise de dependências  
varredura de vulnerabilidades  
testes dinâmicos de segurança  
verificação de segredos no código

Esses passos ajudam a identificar vulnerabilidades antes que o software seja implantado em produção.

---

# Onde o Security Step entra na pipeline

![Image](https://cdnbbsr.s3waas.gov.in/s3dcf6070a4ab7f3afbfd2809173e0824b/uploads/2024/12/20241219704428476.png)

![Image](https://www.paloaltonetworks.com/content/dam/pan/en_US/images/cyberpedia/CI_CD%20Security%20-%201.png?imwidth=480)

![Image](https://sunbytes.io/app/uploads/2025/07/DevSecOps-Pipeline-Post--scaled.webp)

![Image](https://blog.gitguardian.com/content/images/2024/04/Vulnerability-Management-Lifecycle-in-DevSecOps-1-1.png)

Os Security Steps podem ser distribuídos em diferentes momentos da pipeline.

Normalmente eles são inseridos em pontos estratégicos do processo de desenvolvimento.

Durante o commit de código podem ser executadas verificações como secret scanning ou análise de dependências.

Durante a etapa de build podem ser executadas análises SAST para identificar vulnerabilidades no código fonte.

Durante a etapa de testes podem ser executadas análises dinâmicas da aplicação.

Antes da implantação em produção podem ser executadas varreduras adicionais para garantir que nenhuma vulnerabilidade crítica esteja presente.

Essa abordagem permite que problemas de segurança sejam identificados o mais cedo possível.

---

# Exemplos de Security Steps em uma pipeline

Uma pipeline DevSecOps pode incluir diversos tipos de testes de segurança.

Entre os mais comuns estão:

SAST  
DAST  
Software Composition Analysis (SCA)  
Secret Scanning  
Container Scanning  
Infrastructure as Code Security

Cada uma dessas etapas analisa um aspecto diferente da segurança da aplicação.

Essa abordagem permite uma cobertura mais completa das possíveis vulnerabilidades.

---

# Benefícios do DevSecOps

A adoção de DevSecOps traz diversos benefícios para organizações que desenvolvem software.

Entre os principais benefícios estão:

identificação precoce de vulnerabilidades  
redução de custos com correção de falhas  
automação de processos de segurança  
maior colaboração entre equipes  
entrega mais rápida e segura de software

Esses benefícios tornam o desenvolvimento mais eficiente e reduzem significativamente os riscos de segurança.

---

# Desafios na implementação

Apesar dos benefícios, a implementação de DevSecOps também apresenta alguns desafios.

Entre eles estão:

mudança cultural dentro da organização  
necessidade de automação de processos  
treinamento das equipes de desenvolvimento  
integração de ferramentas de segurança na pipeline

Superar esses desafios é fundamental para que a estratégia DevSecOps funcione corretamente.

---

# Conclusão

DevSecOps representa uma evolução no desenvolvimento de software ao integrar segurança diretamente no processo de criação e entrega de aplicações.

Ao incorporar testes de segurança automatizados dentro da pipeline de CI/CD, as organizações conseguem identificar vulnerabilidades mais cedo, reduzir riscos e entregar software mais seguro.

Os Security Steps desempenham um papel fundamental nesse processo, garantindo que a segurança seja verificada continuamente durante todo o ciclo de vida do software.