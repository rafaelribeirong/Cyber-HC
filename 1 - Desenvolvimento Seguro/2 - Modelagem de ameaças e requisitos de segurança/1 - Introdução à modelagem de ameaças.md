# Modelagem de Ameaças (Threat Modeling)

A **modelagem de ameaças** é uma prática essencial da segurança de aplicações e sistemas. O objetivo dessa atividade é **identificar riscos de segurança antes que o sistema seja implementado ou implantado**, permitindo que medidas de proteção sejam planejadas e aplicadas desde as fases iniciais do projeto.

Em vez de esperar que vulnerabilidades sejam descobertas apenas durante testes ou incidentes de segurança, a modelagem de ameaças permite antecipar possíveis problemas analisando como o sistema funciona e como ele pode ser atacado.

Essa abordagem busca responder uma pergunta central:

**Quais ameaças podem afetar este sistema e como podemos nos proteger delas?**

A modelagem de ameaças analisa **representações estruturadas de um sistema**, como diagramas de arquitetura e fluxos de dados, para identificar pontos críticos onde falhas de segurança podem ocorrer.

---

# Ecossistema analisado na modelagem de ameaças

![Image](https://shostack.org/blog/img/2024/aws-diagram-with-key.png)

![Image](https://www.researchgate.net/publication/339285993/figure/fig4/AS%3A903369547849729%401592391492279/Security-Architecture-for-IoT-ecosystems-supported-by-the-Handle-System.png)

![Image](https://cdn-images-1.medium.com/max/7898/1%2A8UMCCnUh4G1AtadlxQq4-w.jpeg)

![Image](https://community.arm.com/cfs-file/__key/communityserver-blogs-components-weblogfiles/00-00-00-19-89/5732.Slide35.png)

A modelagem de ameaças não se limita apenas à aplicação. Ela considera todo o **ecossistema tecnológico envolvido**, incluindo todos os componentes que manipulam ou processam informações.

Isso pode envolver diversos elementos, como:

sistemas de rede  
aplicações web  
aplicações móveis  
infraestrutura de identidade e acesso (IAM)  
dispositivos IoT  
APIs  
bancos de dados  
serviços em nuvem

Todos esses elementos compõem a superfície de ataque de um sistema.

Durante o processo de modelagem de ameaças, é importante compreender como os dados trafegam entre esses componentes. Ao identificar como as informações são criadas, processadas, armazenadas e transmitidas, torna-se possível entender quais ativos possuem maior valor e quais pontos do sistema podem se tornar alvos de ataques.

Esse entendimento permite identificar **ameaças potenciais antes que elas se tornem vulnerabilidades exploráveis**.

---

# Identificação de ativos e dados sensíveis

![Image](https://owasp.org/www-community/assets/images/Data_flow1.jpg)

![Image](https://www.security.uci.edu/files/2023/02/Level0-DataFlowDiagram.jpg)

![Image](https://www.researchgate.net/publication/353939407/figure/fig3/AS%3A1124762302582784%401645175638112/Data-flow-diagram-showing-how-data-from-various-sources-flows-through-the-system-to-be.ppm)

![Image](https://global-uploads.webflow.com/626906cc9bbea5926711ae5c/646e21088ac8fe73af75f389_Data%20flow_V5.jpg)

Um dos primeiros passos da modelagem de ameaças é identificar os **ativos de valor** presentes no sistema.

Ativos podem incluir:

informações pessoais de usuários  
credenciais de autenticação  
dados financeiros  
propriedade intelectual  
configurações críticas do sistema

Após identificar esses ativos, é necessário compreender como eles trafegam pela arquitetura do sistema. Esse processo geralmente é representado por meio de **diagramas de fluxo de dados (DFD)**.

Esses diagramas ajudam a visualizar:

onde os dados são criados  
onde são armazenados  
quais sistemas os processam  
como eles são transmitidos entre componentes

A partir dessa análise é possível identificar pontos onde dados podem ser expostos, interceptados ou manipulados.

---

# Objetivo da modelagem de ameaças

A modelagem de ameaças busca identificar riscos de segurança e planejar mecanismos de proteção que cubram toda a arquitetura do sistema.

Ela permite:

compreender a superfície de ataque do sistema  
identificar ativos críticos  
identificar pontos vulneráveis da arquitetura  
priorizar riscos de segurança  
definir controles de mitigação

Essa análise permite que as equipes de desenvolvimento e segurança adotem controles adequados ainda nas fases iniciais do projeto.

---

# Processo de análise da modelagem de ameaças

![Image](https://miro.medium.com/0%2AN6D4T-wTre0wiwk3.png)

![Image](https://owasp.org/www-community/assets/images/UseAndMisuseCase.jpg)

![Image](https://cdn-dynmedia-1.microsoft.com/is/image/microsoftcorp/response%3AVP1-539x349)

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fi48cyz6off7clrpzvqgd.webp)

Durante a modelagem de ameaças, os analistas normalmente seguem uma sequência lógica de perguntas que orienta a análise do sistema.

### 1 – No que estamos trabalhando

Nesta etapa é necessário entender profundamente o sistema analisado.

Isso inclui:

arquitetura da aplicação  
componentes envolvidos  
infraestrutura de rede  
fluxos de dados  
integrações externas

O objetivo é construir uma representação clara de como o sistema funciona.

---

### 2 – O que pode dar errado

Após entender a arquitetura, o próximo passo é identificar possíveis ameaças.

Isso envolve analisar como um atacante poderia explorar o sistema.

Alguns exemplos de ameaças incluem:

acesso não autorizado  
interceptação de dados  
manipulação de informações  
execução de código malicioso  
exposição de dados sensíveis

Ferramentas e metodologias como **STRIDE** ou **Attack Trees** são frequentemente utilizadas para apoiar essa análise.

---

### 3 – O que pode ser feito para reduzir o risco

Depois de identificar as ameaças, são definidos controles de segurança para mitigar os riscos.

Esses controles podem envolver diversas medidas técnicas ou arquiteturais, como:

implementação de autenticação forte  
uso de criptografia para proteger dados sensíveis  
segmentação de rede  
validação rigorosa de entradas  
monitoramento de eventos de segurança

Essas medidas reduzem a probabilidade ou o impacto de possíveis ataques.

---

### 4 – O trabalho foi bom o suficiente

A etapa final consiste em revisar o processo de modelagem de ameaças e validar se os riscos foram identificados adequadamente.

Isso pode incluir:

revisão da análise por especialistas em segurança  
validação das medidas de mitigação  
revisão da arquitetura do sistema  
documentação das decisões de segurança

A modelagem de ameaças não é uma atividade única. Ela deve ser revisada sempre que o sistema sofrer mudanças significativas, como novas funcionalidades, alterações na arquitetura ou integrações com novos serviços.

---

# Importância da modelagem de ameaças

A modelagem de ameaças é considerada uma das práticas mais eficazes de segurança em aplicações porque permite **identificar riscos antes que vulnerabilidades sejam introduzidas no sistema**.

Ao integrar essa prática ao processo de desenvolvimento, as organizações conseguem:

reduzir custos de correção de vulnerabilidades  
evitar falhas de segurança críticas  
melhorar a arquitetura do sistema  
fortalecer a proteção de dados sensíveis

Por esse motivo, frameworks como **OWASP SAMM, ASVS e Microsoft SDL** recomendam a modelagem de ameaças como uma atividade essencial no desenvolvimento seguro de software.