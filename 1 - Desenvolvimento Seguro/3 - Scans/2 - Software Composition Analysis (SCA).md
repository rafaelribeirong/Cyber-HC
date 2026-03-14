# Software Composition Analysis (SCA)

## O que é SCA

**Software Composition Analysis (SCA)** é um tipo de análise de segurança focada em **bibliotecas e componentes de terceiros utilizados em aplicações**.

Hoje, a maioria das aplicações modernas não é construída totalmente do zero. Elas utilizam diversas **dependências externas**, como bibliotecas, frameworks e pacotes open source.

O SCA analisa essas dependências para identificar:

- bibliotecas utilizadas pela aplicação
    
- versão exata dos componentes
    
- vulnerabilidades conhecidas (CVE)
    
- componentes obsoletos
    
- problemas de licença de software
    

---

## O que o SCA analisa

![Image](https://cdn.prod.website-files.com/642adcaf364024654c71df23/677fb364936d137a3150d858_frame-1321313977_2a20468c3fa965ed53a527ce930fd951_2000.png)

![Image](https://res.cloudinary.com/snyk/image/upload/v1663494673/wordpress-sync/learn-expectation-for-open-source-vulnerability-fixes.png)

![Image](https://beehiiv-images-production.s3.amazonaws.com/uploads/asset/file/cf8f3105-89b3-4a4a-b7c9-30cf8b5e647e/ssc_blog.png?t=1694537033)

![Image](https://substackcdn.com/image/fetch/%24s_%211W7m%21%2Cf_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F9015cb33-70f4-4f77-bd9b-43afc0adb6a3_1132x605.png)

O funcionamento básico do SCA:

1. A ferramenta analisa arquivos de dependência da aplicação  
    (ex: package.json, pom.xml, requirements.txt)
    
2. Identifica todas as bibliotecas utilizadas
    
3. Compara essas bibliotecas com bancos de vulnerabilidades como:
    

- NVD (National Vulnerability Database)
    
- CVE
    
- GitHub Security Advisories
    

4. Gera relatórios com vulnerabilidades detectadas.
    

---

# Principais ferramentas de SCA

## OWASP Dependency Check

Ferramenta **open source** mantida pelo **OWASP**.

Objetivo  
Identificar dependências vulneráveis em projetos de software.

Principais características

- Open source
    
- Baseada em banco de dados NVD
    
- Suporta várias linguagens
    
- Pode ser executada localmente ou no CI/CD
    

Modos de execução

- CLI (linha de comando)
    
- Plugin Maven
    
- Plugin Gradle
    
- Plugin Jenkins
    
- Integração com CI/CD
    

Linguagens suportadas

- Java
    
- .NET
    
- Node.js
    
- Python
    
- Ruby
    
- PHP
    

Relatórios gerados

- HTML
    
- XML
    
- JSON
    
- JUnit
    

Exemplo de resultado

A ferramenta identifica:

Biblioteca  
Versão  
CVE associado  
Nível de severidade

Exemplo

Biblioteca: Log4j  
Versão: 2.14  
Vulnerabilidade: CVE-2021-44228  
Severidade: Crítica

---

## GitLab Dependency Scanning

Ferramenta integrada ao **GitLab CI/CD**.

Objetivo  
Realizar análise automática de dependências dentro do pipeline de desenvolvimento.

Características principais

- Integrado diretamente no GitLab
    
- Execução automática no pipeline
    
- Identificação de vulnerabilidades em bibliotecas
    
- Integração com dashboards de segurança
    

Modo de execução

- Executado dentro do **GitLab CI pipeline**
    
- Utiliza templates de segurança do GitLab
    

Exemplo de pipeline

```
include:
  - template: Security/Dependency-Scanning.gitlab-ci.yml
```

Relatórios gerados

- Security Dashboard
    
- Relatório de vulnerabilidades
    
- Sugestões de correção
    

Benefícios

- totalmente integrado ao DevOps
    
- fácil automação
    
- visibilidade centralizada
    

---

## Veracode SCA

Ferramenta comercial utilizada em ambientes corporativos.

Objetivo  
Analisar dependências open source utilizadas pela aplicação.

Características

- análise automática de bibliotecas
    
- identificação de vulnerabilidades
    
- monitoramento contínuo
    
- análise de risco da cadeia de suprimentos
    

Modos de execução

- SaaS (plataforma cloud)
    
- CLI
    
- integração com CI/CD
    

Integrações

- GitHub
    
- GitLab
    
- Jenkins
    
- Azure DevOps
    

Relatórios gerados

- vulnerabilidades por severidade
    
- componentes afetados
    
- recomendações de atualização
    

Diferencial

Veracode também fornece **priorização baseada em risco explorável**.

---

## Snyk

Ferramenta muito popular para **DevSecOps**.

Objetivo  
Detectar vulnerabilidades em dependências open source.

Características

- versão gratuita disponível
    
- integração com GitHub e GitLab
    
- monitoramento contínuo
    
- correções automáticas sugeridas
    

Modos de execução

- CLI
    
- integração com repositório Git
    
- integração CI/CD
    

Exemplo de execução

```
snyk test
```

Relatórios

- vulnerabilidades por severidade
    
- sugestões de correção
    
- pull requests automáticos para atualização
    

Diferencial

O Snyk pode **abrir automaticamente um Pull Request corrigindo a dependência vulnerável**.

---

## Black Duck

Ferramenta corporativa da **Synopsys**.

Objetivo  
Gerenciar segurança e compliance de software open source.

Características

- análise profunda de dependências
    
- verificação de licenças open source
    
- análise da cadeia de suprimentos de software
    

Modos de execução

- SaaS
    
- On-premise
    
- CLI
    
- integração com CI/CD
    

Recursos avançados

- Software Bill of Materials (SBOM)
    
- análise de risco de licenças
    
- monitoramento contínuo de vulnerabilidades
    

Relatórios

- vulnerabilidades detectadas
    
- análise de licenças
    
- risco da cadeia de software
    

---

# Comparação das ferramentas

|Ferramenta|Tipo|Open Source|Execução|Integração CI/CD|
|---|---|---|---|---|
|Dependency Check|SCA|Sim|CLI / Plugins|Sim|
|GitLab Dependency Scan|SCA|Parcial|Pipeline GitLab|Sim|
|Veracode SCA|Comercial|Não|SaaS / CLI|Sim|
|Snyk|Freemium|Parcial|CLI / SaaS|Sim|
|Black Duck|Comercial|Não|SaaS / On-prem|Sim|

---

# Benefícios do uso de SCA

Identificação rápida de vulnerabilidades em bibliotecas  
Monitoramento contínuo de dependências  
Redução de risco na cadeia de suprimentos de software  
Verificação de licenças open source  
Integração com pipelines DevSecOps

---

Se quiser, posso também montar a próxima seção:

**SAST – Static Application Security Testing**

com:

- explicação técnica
    
- ferramentas (Semgrep, SonarQube, Checkmarx, Fortify)
    
- exemplos de scans reais
    
- fluxo no CI/CD
    
- imagens do processo.