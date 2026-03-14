# Modelagem na prática – classificando e priorizando ameaças

Depois de identificar os ativos, mapear ameaças e definir controles, a próxima etapa da modelagem de ameaças consiste em **classificar e priorizar os riscos identificados**. Essa etapa é essencial porque normalmente um sistema pode apresentar dezenas de ameaças possíveis, e nem todas possuem o mesmo nível de risco.

Para que a organização consiga tratar os riscos de forma eficiente, é necessário utilizar um **modelo estruturado de classificação**.

Uma abordagem bastante utilizada combina:

Classificação da ameaça pelo modelo STRIDE  
Avaliação de severidade utilizando CVSS  
Definição do vetor CVSS para contextualizar o risco

Essa combinação permite identificar não apenas o tipo da ameaça, mas também o impacto real que ela pode causar no ambiente analisado.

---

# Estrutura de classificação de ameaças

Na prática, após a modelagem de ameaças, pode-se construir uma tabela contendo algumas colunas principais:

Ativo analisado  
Ameaça identificada  
Categoria STRIDE  
Severidade  
Vetor CVSS

Essa estrutura ajuda a transformar a análise qualitativa em um modelo que pode ser priorizado e tratado pela equipe de segurança ou desenvolvimento.

---

# O que é o modelo STRIDE

STRIDE é um modelo criado pela Microsoft para classificar ameaças em sistemas computacionais. O objetivo do modelo é ajudar analistas de segurança a identificar quais tipos de ataques podem afetar cada componente de um sistema.

O nome STRIDE é um acrônimo formado pelas iniciais de seis categorias de ameaças.

Cada categoria representa um tipo específico de risco que pode comprometer a segurança de uma aplicação ou infraestrutura.

---

# Categorias do modelo STRIDE

![Image](https://www.researchgate.net/publication/347880901/figure/fig2/AS%3A972470580412416%401608866462141/Example-of-STRIDE-threat-model-25.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AXKca6LtbfdSSNelyEbuUsg.png)

![Image](https://dz2cdn1.dzone.com/storage/temp/18224099-stride-threat-model-mc-slide2.png)

![Image](https://www.slideteam.net/media/catalog/product/cache/1280x720/s/t/stride_threat_model_ppt_powerpoint_presentation_infographic_template_smartart_cpb_slide01.jpg)

---

# Spoofing (Falsificação de identidade)

Spoofing ocorre quando um atacante consegue se passar por outra entidade dentro do sistema.

Isso pode acontecer, por exemplo, quando um invasor consegue utilizar credenciais roubadas ou falsificar a identidade de um usuário legítimo.

Exemplos de ataques dessa categoria incluem:

uso de credenciais comprometidas  
roubo de sessão  
falsificação de tokens de autenticação  
impersonação de serviços ou usuários

Esse tipo de ameaça está diretamente relacionado à falha em mecanismos de autenticação.

Controles normalmente utilizados para mitigar esse risco incluem autenticação forte, proteção de sessão e gestão segura de identidades.

---

# Tampering (Adulteração de dados)

Tampering refere-se à modificação não autorizada de dados ou informações dentro de um sistema.

Esse tipo de ataque pode ocorrer durante o armazenamento dos dados ou durante sua transmissão.

Alguns exemplos incluem:

modificação de parâmetros em requisições  
alteração de dados em banco de dados  
modificação de arquivos críticos do sistema  
manipulação de dados em APIs

Esse tipo de ameaça compromete a **integridade da informação**.

Para reduzir esse risco, normalmente são utilizados controles como verificação de integridade de dados, criptografia, validação de entrada e assinatura digital.

---

# Repudiation (Repúdio)

Repudiation ocorre quando um usuário realiza uma ação dentro do sistema e posteriormente nega ter executado essa atividade.

Esse problema geralmente está relacionado à ausência de registros adequados ou à falta de mecanismos de auditoria.

Exemplos incluem:

negação de transações realizadas  
ausência de logs de atividades  
falta de rastreabilidade de ações críticas

Quando o sistema não possui mecanismos de auditoria adequados, torna-se difícil comprovar quem realizou determinada ação.

Controles comuns incluem registros de log, trilhas de auditoria e mecanismos de rastreamento de atividades.

---

# Information Disclosure (Divulgação de informações confidenciais)

Essa categoria refere-se à exposição não autorizada de informações sensíveis.

Esse tipo de falha pode ocorrer por diversos motivos, como erros de configuração, vulnerabilidades na aplicação ou falhas de controle de acesso.

Exemplos incluem:

exposição de dados pessoais  
vazamento de informações confidenciais  
exposição de arquivos internos  
retorno de mensagens de erro contendo informações sensíveis

Esse tipo de ameaça compromete diretamente a **confidencialidade da informação**.

Controles frequentemente utilizados incluem criptografia de dados, controle de acesso e mascaramento de informações sensíveis.

---

# Denial of Service (Negação de serviço)

Denial of Service ocorre quando um sistema é sobrecarregado ou explorado de forma a impedir que usuários legítimos consigam acessar o serviço.

Esse tipo de ataque pode causar indisponibilidade parcial ou total da aplicação.

Exemplos incluem:

envio massivo de requisições para um servidor  
exploração de falhas que causam travamento da aplicação  
consumo excessivo de recursos do sistema

Esse tipo de ameaça compromete a **disponibilidade do sistema**.

Medidas de mitigação incluem balanceamento de carga, mecanismos de limitação de requisições e monitoramento de tráfego.

---

# Elevation of Privilege (Elevação de privilégio)

Essa ameaça ocorre quando um usuário consegue obter permissões maiores do que aquelas que foram originalmente atribuídas a ele.

Esse tipo de ataque pode permitir que usuários comuns obtenham acesso administrativo ou executem ações críticas dentro do sistema.

Exemplos incluem:

exploração de falhas de autorização  
execução de código com privilégios elevados  
acesso indevido a funcionalidades administrativas

Esse tipo de risco está relacionado diretamente a falhas no controle de acesso da aplicação.

Controles comuns incluem validação rigorosa de permissões, segregação de funções e verificação constante de privilégios.

---

# Classificação utilizando CVSS

Após identificar a categoria STRIDE de cada ameaça, é possível avaliar a severidade utilizando o **Common Vulnerability Scoring System (CVSS)**.

O CVSS é um modelo padronizado utilizado mundialmente para medir a gravidade de vulnerabilidades de segurança.

A pontuação CVSS considera diversos fatores, como:

facilidade de exploração  
impacto na confidencialidade  
impacto na integridade  
impacto na disponibilidade

A pontuação final varia normalmente entre 0 e 10.

Quanto maior a pontuação, maior a severidade da vulnerabilidade.

---

# Vetor CVSS

Além da pontuação numérica, o CVSS utiliza um vetor que descreve as características da vulnerabilidade.

Esse vetor indica fatores como:

tipo de acesso necessário  
complexidade do ataque  
necessidade de interação do usuário  
impacto causado

A utilização do vetor CVSS permite contextualizar melhor o risco dentro do ambiente analisado.

---

# Exemplo prático de classificação

Após a modelagem de ameaças, a classificação pode ser estruturada da seguinte forma:

Ativo: API de autenticação  
Ameaça: bypass de autenticação  
Categoria STRIDE: Spoofing  
Severidade CVSS: 8.8  
Vetor CVSS: AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H

---

Ativo: banco de dados  
Ameaça: exposição de dados sensíveis  
Categoria STRIDE: Information Disclosure  
Severidade CVSS: 9.1  
Vetor CVSS: AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:N/A:N

---

Essa classificação permite que a organização identifique rapidamente quais vulnerabilidades representam maior risco e devem ser tratadas com prioridade.

---

# Priorização das ameaças

Após classificar todas as ameaças identificadas na modelagem, elas podem ser organizadas por ordem de severidade.

Normalmente as organizações priorizam:

vulnerabilidades críticas primeiro  
depois vulnerabilidades de alto impacto  
em seguida vulnerabilidades médias  
e por último vulnerabilidades de baixo risco

Esse processo ajuda a direcionar os esforços de segurança para os pontos mais críticos do sistema.

---

# Conclusão

A classificação e priorização de ameaças é uma etapa fundamental da modelagem de ameaças. Ela permite transformar uma análise conceitual em uma visão clara dos riscos que realmente precisam ser tratados.

Utilizando o modelo STRIDE para categorizar ameaças e o CVSS para avaliar severidade, as organizações conseguem identificar quais vulnerabilidades representam maior risco e definir prioridades de mitigação de forma estruturada e eficiente.