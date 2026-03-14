# Introdução aos Scans de Segurança

No contexto de **segurança de aplicações**, é comum utilizar ferramentas automatizadas chamadas **scanners de segurança** para identificar vulnerabilidades no código, nas dependências e na própria aplicação.

Essas ferramentas fazem parte da abordagem conhecida como **Shift Left Security**, onde a segurança é aplicada **o mais cedo possível no ciclo de desenvolvimento**, reduzindo riscos e custos de correção.

---

# O que são scans de segurança

![Image](https://res.cloudinary.com/snyk/image/upload/f_auto%2Cw_2560%2Cq_auto/v1663714812/wordpress-sync/Learn-SAST-stages-graphic.png)

![Image](https://owasp.org/www-project-devsecops-guideline/latest/assets/images/Pipeline-view.png)

![Image](https://www.sei.cmu.edu/media/images/10apptools_scanlon_figure2.original.jpg)

![Image](https://www.sei.cmu.edu/media/images/07092018_testingtools_scanlon_.max-1280x720.format-webp_ogBP0kk.webp)

Scans de segurança são **ferramentas automatizadas que analisam código, dependências e aplicações em busca de vulnerabilidades**.

Essas ferramentas ajudam a identificar:

- falhas de segurança no código
    
- bibliotecas vulneráveis
    
- credenciais expostas
    
- comportamentos inseguros da aplicação
    

Principais características:

- automatizam análises de segurança
    
- permitem identificação precoce de problemas
    
- reduzem custo de correção de vulnerabilidades
    
- integram-se ao pipeline de desenvolvimento
    

---

# Importância no Secure SDLC

Os scans são elementos importantes dentro do **Secure Software Development Life Cycle (S-SDLC)**.

Eles permitem aplicar segurança de forma:

- contínua
    
- automatizada
    
- escalável
    
- integrada ao desenvolvimento
    

Fases típicas do ciclo de desenvolvimento:

PLAN / DESIGN  
CODE  
TEST  
DEPLOY

Na prática, muitos testes de segurança são incluídos **já na fase de desenvolvimento**, seguindo o conceito de **Shift Left**.

---

# Tipos de scans de segurança

Existem diferentes tipos de scanners, cada um focado em um aspecto específico da aplicação.

|Tipo|Nome|Objetivo|
|---|---|---|
|SCA|Software Composition Analysis|Analisar dependências e bibliotecas utilizadas pela aplicação|
|SAST|Static Application Security Testing|Analisar o código-fonte em busca de vulnerabilidades|
|DAST|Dynamic Application Security Testing|Testar a aplicação em execução|
|Secret Scan|Detecção de segredos|Identificar credenciais expostas no código ou repositório|

---

# Quando utilizar cada tipo de scan

|Tipo|Nome|Quando usar|Fase no CI/CD|
|---|---|---|---|
|SCA|Software Composition Analysis|Ao adicionar ou atualizar dependências|Build|
|SAST|Static Application Security Testing|Durante o desenvolvimento e antes do commit|Pré-commit / Build|
|DAST|Dynamic Application Security Testing|Após o deploy em ambiente de teste|Pós-deploy|
|Secret Scan|Detecção de segredos|Antes de commits e analisando histórico do repositório|Pré-commit / Build|

---

# Exemplos práticos

SCA  
Identifica bibliotecas vulneráveis.

Exemplo:  
Uma aplicação usa uma versão vulnerável de **Log4j**.

SAST  
Analisa o código procurando vulnerabilidades como:

- SQL Injection
    
- XSS
    
- falhas de validação de entrada
    

DAST  
Testa a aplicação rodando e tenta explorar vulnerabilidades como:

- falhas de autenticação
    
- endpoints inseguros
    
- falhas de configuração
    

Secret Scan  
Procura por informações sensíveis no código, como:

- senhas
    
- tokens de API
    
- chaves privadas
    
- credenciais de banco de dados
    

---

# Desafios no uso de ferramentas de scan

Apesar de serem muito úteis, essas ferramentas também apresentam desafios.

Principais desafios:

Falsos positivos  
Alertas incorretos que consomem tempo da equipe.

Configuração  
Ferramentas precisam ser ajustadas conforme a tecnologia utilizada.

Integração  
Nem sempre é simples integrar scanners com pipelines CI/CD.

Prioritização  
Nem todas as vulnerabilidades têm o mesmo impacto.

Adoção pela equipe  
Desenvolvedores precisam entender e confiar nas ferramentas.
