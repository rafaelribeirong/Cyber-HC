# Por que realizar uma Modelagem de Ameaças

A modelagem de ameaças é uma prática fundamental para reduzir riscos de segurança durante o desenvolvimento de sistemas. Ela permite identificar possíveis falhas antes que o sistema esteja em produção, reduzindo significativamente o impacto financeiro e operacional de incidentes de segurança.

Relatórios recentes demonstram a importância dessa prática. O relatório **IBM Cost of a Data Breach 2024** indica que o custo médio global de uma violação de dados atingiu aproximadamente **4,88 milhões de dólares**. Esse valor representa custos associados a investigação, interrupção de serviços, perda de reputação, multas regulatórias e recuperação de sistemas.

Entre as causas mais frequentes de incidentes estão erros que poderiam ser identificados previamente durante o design da aplicação ou da infraestrutura. Problemas comuns incluem:

senhas padrão ou fracas utilizadas em sistemas  
ativos expostos publicamente na internet sem proteção adequada  
permissões excessivas concedidas a usuários ou sistemas  
falta de criptografia para proteção de dados sensíveis  
ausência de atualizações e correções de segurança

Outro fator relevante apontado em estudos de segurança é a **má configuração de ambientes em nuvem**, que apresenta um custo médio de aproximadamente **3,98 milhões de dólares por incidente**. Esses números demonstram que grande parte dos problemas de segurança não está necessariamente em ataques sofisticados, mas em falhas de configuração ou arquitetura.

A modelagem de ameaças surge justamente para antecipar esses riscos.

---

# A modelagem de ameaças dentro do ciclo de vida do software

![Image](https://images.openai.com/static-rsc-3/irNSweL-j_fAJgz5wltU10--pZj3nb1kcLHn8S5ojmFU1eiig2tHEfujUon1CDPiXaDDCpIiE51xl6umsO4-qQzNAxVXwhlchEEu_e0lArI?purpose=fullsize&v=1)

![Image](https://images.openai.com/static-rsc-3/vnjuTgcYKWu3m4UrMUc9gAcWkcSPBLlfb1hjXMTdopiGFulQ7yOdsiXo13UL6FedGQXgEdptazB8svEwZJcjpT78WbX5bTwVS0IRoJZqnwM?purpose=fullsize&v=1)

![Image](https://miro.medium.com/1%2Av7N0r1tnd6XDneL29-CN-g.png)

![Image](https://cdn.prod.website-files.com/68a4552adf4a460ade53ca38/694567b38d24ef5563176221_68d67f2ee5f2cd99c130123d_successfully-integrating-security-sdlc.png)

O ciclo de vida de desenvolvimento de software (SDLC) é normalmente dividido em seis etapas principais. Integrar segurança nesse ciclo é essencial para reduzir riscos e garantir a confiabilidade das aplicações.

A modelagem de ameaças deve ser incluída nesse processo para apoiar a identificação de riscos antes da implementação do sistema.

---

## Planejamento

A fase de planejamento define os fundamentos do projeto.

Nesta etapa são definidos:

objetivos do projeto  
escopo do sistema  
requisitos gerais  
viabilidade técnica  
viabilidade econômica

O planejamento estabelece as bases sobre as quais o sistema será desenvolvido.

---

## Análise

Na fase de análise são levantados os requisitos funcionais e não funcionais do sistema.

Isso inclui:

definição das funcionalidades da aplicação  
identificação dos sistemas que serão utilizados  
definição das tecnologias envolvidas  
levantamento de requisitos operacionais

Essa etapa é responsável por definir como o sistema deverá funcionar.

---

## Design

![Image](https://d1pnnwteuly8z3.cloudfront.net/images/ae7f7c8d-97db-47a0-b325-f3fd4c2fdbf7/ca87e117-c176-4d59-aa68-ae9b5819b66d.png)

![Image](https://view.subpage.app/app/company/C532b8873cc5442e2b1f2265b77a7d7dc/domain/MTiT0jFlGh/page/M6K4TirmGh/glossary/M6591825d061a008f9913990bb300c0d71726724016880/file/Mef66e3a47505001b8b6d4ed1f5b56f611726725910339.webp)

![Image](https://www.researchgate.net/publication/261619675/figure/fig3/AS%3A736163044290560%401552526355068/DFD-Data-Flow-Diagram-of-the-software-architecture.ppm)

![Image](https://images.ctfassets.net/w6r2i5d8q73s/4ACdYH8UEWFsOUTSA9XEqj/a24d132585820616bf5aebb8dac05791/diagramming_suppy_and_demand_hero_image_EN_standard_4_3.png?fm=webp&q=75)

A fase de design é responsável pela criação da arquitetura da aplicação.

Nesta etapa são produzidos:

diagramas de arquitetura  
diagramas de fluxo de dados  
modelos de interação entre sistemas  
definição da lógica de negócio

É nesse momento que a **modelagem de ameaças deve ser aplicada**.

Com a arquitetura do sistema definida e os ativos identificados, torna-se possível analisar quais ameaças podem afetar cada componente do ecossistema.

A modelagem de ameaças consiste em analisar esses ativos e identificar possíveis riscos que possam comprometer o sistema.

---

## Desenvolvimento

A fase de desenvolvimento corresponde à implementação do sistema.

Nesta etapa os desenvolvedores escrevem o código da aplicação com base nos requisitos definidos durante o design.

A segurança deve ser considerada durante essa fase por meio da adoção de boas práticas de desenvolvimento seguro.

---

## Testes e Integração

![Image](https://www.tutorialspoint.com/security_testing/images/security_testing_sec_testing_processes.jpg)

![Image](https://dz2cdn1.dzone.com/storage/temp/15203594-ssengupta-figure-1.png)

![Image](https://www.compassitc.com/hs-fs/hubfs/Penetration%20Test%20Phases.webp?height=604&name=Penetration+Test+Phases.webp&width=610)

![Image](https://www.redscan.com/media/web-application-penetration-testing-process.svg)

A fase de testes busca verificar a qualidade e a segurança da aplicação antes de sua implantação.

Isso pode incluir:

testes funcionais  
testes automatizados  
testes de segurança  
testes de integração entre sistemas

Durante essa etapa podem ser identificadas vulnerabilidades que precisam ser corrigidas antes da liberação do sistema.

---

## Manutenção

A fase de manutenção ocorre após a aplicação entrar em produção.

Ela envolve:

correção de bugs  
correção de vulnerabilidades  
atualizações de segurança  
melhorias de desempenho

A segurança continua sendo monitorada durante todo o ciclo de vida do sistema.

---

# Como a modelagem de ameaças é aplicada na fase de design

![Image](https://owasp.org/www-community/assets/images/Data_flow1.jpg)

![Image](https://shostack.org/blog/img/2024/aws-diagram-with-key.png)

![Image](https://www.blackduck.com/glossary/what-is-threat-modeling/_jcr_content/root/synopsyscontainer/column_301182190_cop/colRight/image_2140332079_cop.coreimg.svg/1727200446662/threat-modeling-security-system.svg)

![Image](https://images.prismic.io/guardrails-01/YzkxYTU4MGMtYmRiZC00ZTg0LWJhM2EtODJjOGI5NDYwMTQ0_threatmodeling-1-1024x600.jpg?auto=compress%2Cformat&h=600&rect=0%2C0%2C1024%2C600&w=1024)

Após a definição da arquitetura da aplicação, os componentes do sistema são mapeados.

Isso inclui:

servidores  
bancos de dados  
aplicações  
APIs  
infraestrutura de rede  
serviços externos

Com esses elementos identificados, é possível analisar como os dados circulam entre os componentes do sistema.

A partir desse entendimento, são identificadas possíveis ameaças que podem afetar esses ativos.

Para cada ameaça identificada são definidos **pontos de controle** que devem ser implementados para reduzir o risco.

Esses controles podem incluir mecanismos de autenticação, criptografia, validação de dados ou monitoramento de atividades.

---

# Componentes de uma modelagem de ameaças

![Image](https://owasp.org/www-community/assets/images/Data_flow1.jpg)

![Image](https://shostack.org/blog/img/2024/aws-diagram-with-key.png)

![Image](https://www.researchgate.net/publication/338727979/figure/fig1/AS%3A956330936397836%401605018471743/ATTACK-SURFACE-ANALYSIS-FOR-CYBER-MANUFACTURING-SYSTEM.png)

![Image](https://www.researchgate.net/publication/264707910/figure/fig1/AS%3A295866117181442%401447551387880/Example-attack-surface-model-used-for-analysis.png)

Uma modelagem de ameaças normalmente inclui diferentes componentes que ajudam a representar o sistema analisado.

Um dos elementos mais importantes é a criação de diagramas que representem a arquitetura do sistema. Esses diagramas ajudam a visualizar como os dados fluem pela rede e quais sistemas participam do processamento das informações.

Durante essa análise podem ser identificadas diversas vulnerabilidades potenciais, como falhas que permitam ataques de injeção, ataques de cross-site scripting ou exploração de interfaces mal protegidas.

As ameaças identificadas nem sempre estão relacionadas apenas a ataques técnicos. Elas também podem envolver riscos organizacionais.

Entre esses riscos podem estar:

espionagem industrial  
uso indevido de marca ou propriedade intelectual  
dependência de conhecimento concentrado em uma única pessoa  
perda de conhecimento crítico dentro da organização

Esses fatores também devem ser considerados durante a modelagem de ameaças.

---

# Definição de pontos de controle

![Image](https://www.researchgate.net/publication/330913307/figure/fig1/AS%3A723428390756353%401549490177238/An-architectural-Overview-of-Information-Security-Management-System-for-Home-Users-B-The.ppm)

![Image](https://images.openai.com/static-rsc-3/EFhbD_cfGXw_v_Um-uN_bOPeNVvb05sr-81b2etWrlu1hAqyiZn6MQ61ByGbu4KZO0tsLN96xVDU8y46DkzpNERVQvmhx0TH0q3BJvkb9uo?purpose=fullsize&v=1)

![Image](https://media.licdn.com/dms/image/v2/C4D12AQH0jEfO02uc0Q/article-inline_image-shrink_1500_2232/article-inline_image-shrink_1500_2232/0/1612337911317?e=1774483200&t=bWMmRhiXAvyFWP673LynshlEN8BlxFPiqKj6yctFEc0&v=beta)

![Image](https://figures.semanticscholar.org/2d8e0f376510878082f4db5a32da513fdf0fe73d/8-Figure2-1.png)

Após identificar as ameaças, o próximo passo é definir controles que reduzam os riscos.

Esses controles podem existir em diferentes camadas do ambiente tecnológico.

Na camada física podem existir controles como:

controle de acesso a ambientes críticos  
uso de crachás e autenticação física  
segurança patrimonial  
proteção de equipamentos

Na camada de infraestrutura podem ser implementados controles como:

firewalls  
segmentação de rede  
sistemas de monitoramento  
gestão de acessos

Já na camada de aplicação podem ser adotados mecanismos como:

criptografia de dados  
validação de entradas  
controle de permissões  
gestão de autenticação

Além disso, é importante implementar processos de **monitoramento e resposta a incidentes**, que permitem detectar e responder rapidamente a possíveis ataques.

---

# A modelagem de ameaças não se limita apenas ao software

Um erro comum é considerar que a modelagem de ameaças se aplica apenas ao código da aplicação.

Na realidade, ela deve considerar todo o ambiente que suporta o sistema.

Isso inclui:

infraestrutura de rede  
servidores  
dispositivos físicos  
serviços em nuvem  
processos organizacionais

Qualquer elemento que possa impactar a segurança do sistema deve ser considerado na análise.

---

# Conclusão

A modelagem de ameaças é uma atividade essencial para o desenvolvimento seguro de software.

Ela permite identificar riscos antes que vulnerabilidades sejam exploradas, ajudando a reduzir custos associados a incidentes de segurança e melhorar a proteção dos sistemas.

Esse processo exige análise técnica, entendimento da arquitetura e conhecimento sobre ataques cibernéticos.

Por esse motivo, a modelagem de ameaças pode ser considerada também um **exercício de análise e criatividade**. Quanto maior for o conhecimento do analista sobre técnicas de ataque, vetores de exploração e riscos tecnológicos, mais eficaz será a identificação de ameaças e a definição de controles adequados para proteger o sistema.