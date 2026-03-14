# Modelagem de Ameaças na Prática

A modelagem de ameaças não deve ficar apenas no conceito teórico. Na prática, ela consiste em **mapear a arquitetura do sistema**, identificar **ativos**, analisar **ameaças possíveis** e definir **pontos de controle** que reduzam os riscos.

O primeiro passo é criar um **desenho simples da arquitetura**, representando como os componentes da aplicação interagem. Esse desenho normalmente inclui:

- usuário
    
- frontend (interface web ou mobile)
    
- backend (API ou aplicação)
    
- banco de dados
    
- serviços externos
    
- infraestrutura de rede
    

Depois disso, cada componente é analisado para identificar:

**Ativos (Assets)**  
Elementos de valor que precisam ser protegidos.

**Ameaças (Threats)**  
Possíveis ataques ou falhas que podem comprometer esses ativos.

**Controles de segurança (Security Controls)**  
Mecanismos implementados para reduzir ou impedir as ameaças.

---

# Exemplo visual de modelagem de ameaças

![Image](https://shostack.org/blog/img/2017/DFD-framed-1.png)

![Image](https://owasp.org/www-community/assets/images/UseAndMisuseCase.jpg)

![Image](https://owasp.org/www-community/assets/images/Data_flow1.jpg)

![Image](https://www.windriver.com/sites/default/files/2022-02/data-flow-diagram-full.png)

Esses diagramas mostram como arquiteturas de aplicação podem ser analisadas para identificar riscos e controles de segurança.

---

# Exemplo prático simplificado

Abaixo está um exemplo de arquitetura básica de aplicação web para demonstrar como a modelagem de ameaças pode ser aplicada.

```
        Usuário
           |
           v
     [ Frontend Web ]
           |
           v
        [ API ]
           |
           v
      [ Banco de Dados ]
```

Agora vamos classificar cada elemento.

---

# Identificando os Ativos

Os ativos são os elementos que possuem valor e precisam ser protegidos.

No exemplo acima podemos identificar:

**Frontend (Aplicação Web)**  
Contém interface do usuário e pode processar dados sensíveis.

**API / Backend**  
Responsável pela lógica da aplicação e controle de acesso.

**Banco de dados**  
Armazena informações críticas como:

- dados pessoais
    
- credenciais
    
- registros de transações
    
- dados internos da empresa
    

Esses componentes são considerados **ativos críticos** do sistema.

---

# Identificando possíveis ameaças

Após identificar os ativos, o próximo passo é analisar quais ameaças podem afetá-los.

## Ameaças no Frontend

Exemplos de ameaças:

Cross-Site Scripting (XSS)  
injeção de scripts maliciosos na interface  
roubo de sessão de usuário  
manipulação de requisições no navegador

---

## Ameaças no Backend

Possíveis riscos:

SQL Injection  
exposição de APIs sem autenticação  
falhas de controle de acesso  
execução de comandos não autorizados

---

## Ameaças no Banco de Dados

Possíveis ataques incluem:

acesso não autorizado ao banco  
exfiltração de dados  
perda de integridade de informações  
exposição de dados sensíveis

---

# Definindo pontos de controle

Depois de identificar ameaças, são definidos **controles de segurança**.

Esses controles podem ser aplicados em diferentes camadas da arquitetura.

---

## Controles no Frontend

Validação de entrada no cliente  
proteção contra XSS  
uso de Content Security Policy  
proteção contra manipulação de requisições

---

## Controles no Backend

autenticação forte  
controle de acesso baseado em permissões  
validação de entrada no servidor  
tratamento seguro de erros

---

## Controles no Banco de Dados

criptografia de dados sensíveis  
controle de acesso ao banco  
segmentação de rede  
backup e monitoramento

---

# Exemplo visual completo

A modelagem prática pode ser representada assim:

```
Usuário
   |
   v
[Frontend Web]  ---- ameaça: XSS
   |
   |--- controle: validação de entrada
   |--- controle: CSP
   v
[API / Backend] ---- ameaça: SQL Injection
   |
   |--- controle: prepared statements
   |--- controle: autenticação
   v
[Banco de Dados] ---- ameaça: vazamento de dados
   |
   |--- controle: criptografia
   |--- controle: controle de acesso
```

Nesse modelo conseguimos visualizar claramente:

- **onde estão os ativos**
    
- **quais ameaças podem ocorrer**
    
- **quais controles devem ser implementados**
    

---

# Considerando frontend e backend na modelagem

Uma boa modelagem de ameaças deve considerar todo o fluxo da aplicação.

Isso inclui:

frontend  
backend  
infraestrutura  
banco de dados  
serviços externos  
APIs  
infraestrutura de rede

Cada ponto da arquitetura pode apresentar riscos diferentes.

---

# Como analistas normalmente fazem isso

Na prática, especialistas em segurança seguem este processo:

1. desenham a arquitetura da aplicação
    
2. identificam os ativos críticos
    
3. analisam como os dados trafegam no sistema
    
4. identificam possíveis ameaças em cada ponto
    
5. definem controles de segurança para mitigar esses riscos
    

Esse processo permite antecipar problemas de segurança **antes mesmo de o software ser desenvolvido ou implantado**.

---

# Conclusão

A modelagem de ameaças aplicada na prática transforma um desenho de arquitetura em uma análise de segurança.

Ela permite identificar:

ativos críticos do sistema  
possíveis vetores de ataque  
controles necessários para proteção

Quanto maior for o conhecimento do analista sobre arquitetura, redes e técnicas de ataque, mais eficaz será a modelagem de ameaças na identificação e mitigação de riscos.

---

# DFD real de Threat Modeling com STRIDE

A forma mais usada por equipes de arquitetura e segurança é desenhar um **DFD (Data Flow Diagram)** e, em cima dele, mapear as ameaças usando **STRIDE**. No DFD, normalmente usamos **retângulos para atores**, **círculos para processos**, **duas linhas paralelas para armazenamento**, **setas para fluxos de dados** e **linhas tracejadas para trust boundaries**. Esse é exatamente o tipo de representação recomendado pela OWASP e também usado nas orientações da Microsoft.

---

## Legenda visual para o seu documento

Como aqui no chat eu não consigo pintar de verdade, abaixo vai um padrão que você pode levar para Word, slide ou PDF:

- **Azul** = Ativos
    
- **Vermelho** = Ameaças
    
- **Verde** = Pontos de controle
    
- **Linha tracejada** = Trust boundary
    
- **Setas** = Fluxo de dados
    

---

## Exemplo prático de uma aplicação web

Vamos imaginar um sistema simples com frontend, backend e banco de dados.

```text
                         [ATOR]
                     Usuário / Navegador
                             |
                             |  Login / Consulta / Envio de dados
                             v
---------------------------------------------------------------
 TRUST BOUNDARY 1 - Internet / Aplicação pública
---------------------------------------------------------------
                             |
                             v
                  [ATIVO - FRONTEND WEB]
                     Portal / Aplicação Web
                             |
                             |  Requisições HTTPS
                             v
---------------------------------------------------------------
 TRUST BOUNDARY 2 - Camada pública / Camada interna
---------------------------------------------------------------
                             |
                             v
                  [ATIVO - BACKEND / API]
                 Autenticação, regras de negócio,
                    processamento e integrações
                      /                     \
                     /                       \
                    v                         v
        [ATIVO - BANCO DE DADOS]     [ATIVO - SERVIÇO EXTERNO]
         usuários, pedidos, logs         gateway / e-mail / IAM
```

---

## Como marcar os elementos na prática

### 1. O que é ativo

Ativo é tudo aquilo que tem valor para o negócio e precisa ser protegido.

No desenho acima, os ativos são:

**Frontend Web**  
É um ativo porque recebe entrada do usuário e expõe a aplicação ao mundo externo.

**Backend / API**  
É um ativo porque processa autenticação, autorização, regras de negócio e integrações.

**Banco de Dados**  
É um ativo crítico porque armazena dados de usuários, credenciais, registros e informações do negócio.

**Serviço Externo**  
Também pode ser um ativo dependente, porque uma falha nele pode impactar sua segurança ou disponibilidade.

---

### 2. O que é ameaça

Ameaça é tudo aquilo que pode comprometer confidencialidade, integridade, disponibilidade, rastreabilidade ou privilégios do sistema.

No modelo STRIDE, as ameaças são:

- **S — Spoofing**: se passar por outro usuário ou sistema
    
- **T — Tampering**: alterar dados ou código
    
- **R — Repudiation**: negar uma ação sem trilha confiável
    
- **I — Information Disclosure**: expor informação indevida
    
- **D — Denial of Service**: tornar o serviço indisponível
    
- **E — Elevation of Privilege**: ganhar privilégios além do permitido
    

---

### 3. O que é ponto de controle

Ponto de controle é o mecanismo de proteção aplicado para reduzir uma ameaça.

Exemplos:

- MFA
    
- validação de entrada
    
- rate limit
    
- RBAC
    
- logs
    
- criptografia
    
- WAF
    
- segmentação de rede
    
- backup
    
- monitoramento
    

---

# Exemplo completo com marcação de ameaças e controles

```text
[ATOR] Usuário
   |
   | envia credenciais e dados
   v
[ATIVO - FRONTEND WEB]
   |-----------------------------------------------|
   | AMEAÇAS                                       |
   | [S] falsificação de sessão                    |
   | [T] manipulação de parâmetros                 |
   | [I] exposição de dados no navegador           |
   | [D] excesso de requisições                    |
   |-----------------------------------------------|
   | CONTROLES                                     |
   | [C] HTTPS                                     |
   | [C] CSP                                       |
   | [C] validação de entrada no cliente           |
   | [C] proteção de cookies                       |
   |-----------------------------------------------|
   |
   v
================= TRUST BOUNDARY ===================
   |
   v
[ATIVO - BACKEND / API]
   |-----------------------------------------------|
   | AMEAÇAS                                       |
   | [S] uso de token roubado                      |
   | [T] alteração de payload                      |
   | [R] ausência de trilha de auditoria           |
   | [I] vazamento em resposta de erro             |
   | [D] flood de requisições                      |
   | [E] bypass de autorização                     |
   |-----------------------------------------------|
   | CONTROLES                                     |
   | [C] autenticação forte                        |
   | [C] RBAC / controle de acesso                 |
   | [C] validação server-side                     |
   | [C] logs e trilhas de auditoria               |
   | [C] rate limit                                |
   | [C] tratamento seguro de erro                 |
   |-----------------------------------------------|
   |
   +-----------------------> [ATIVO - SERVIÇO EXTERNO]
   |
   v
[ATIVO - BANCO DE DADOS]
   |-----------------------------------------------|
   | AMEAÇAS                                       |
   | [T] alteração indevida de registros           |
   | [I] vazamento de dados sensíveis              |
   | [D] indisponibilidade do banco                |
   | [E] acesso administrativo indevido            |
   |-----------------------------------------------|
   | CONTROLES                                     |
   | [C] criptografia em repouso                   |
   | [C] contas segregadas                         |
   | [C] backup                                    |
   | [C] hardening                                 |
   | [C] monitoramento                             |
   |-----------------------------------------------|
```

---

# Como aplicar o STRIDE no DFD

A OWASP recomenda modelar o sistema, marcar fluxos de dados, identificar trust boundaries e então avaliar ameaças por categoria. O STRIDE é usado justamente para guiar essa análise de forma sistemática.

Uma forma prática de fazer isso é esta:

## No ator externo

Você olha principalmente para **Spoofing**.  
Pergunta: alguém pode se passar por um usuário legítimo?

## No fluxo entre usuário e frontend

Você olha para **Tampering** e **Information Disclosure**.  
Pergunta: os dados podem ser alterados em trânsito ou expostos?

## No frontend

Você olha para **Spoofing, Tampering, Information Disclosure e DoS**.  
Pergunta: há risco de XSS, roubo de sessão, abuso de interface ou sobrecarga?

## No backend

Aqui normalmente entram as seis categorias.  
Pergunta: a API valida entrada, controla acesso, registra ações e protege respostas?

## No banco

Você olha principalmente para **Tampering, Information Disclosure, DoS e Elevation of Privilege**.  
Pergunta: alguém pode alterar, ler, indisponibilizar ou administrar dados sem permissão?

---

# Exemplo de tabela pronta para colocar no documento

## DFD – Mapeamento de ativos, ameaças e controles

**Ativo: Frontend Web**  
Função: interface com o usuário  
Ameaças: XSS, roubo de sessão, manipulação de parâmetros, negação de serviço  
Controles: HTTPS, CSP, validação de entrada, cookies seguros, rate limit

**Ativo: Backend / API**  
Função: autenticação, autorização e regras de negócio  
Ameaças: bypass de autenticação, IDOR, injeção, falha de logging, enumeração de erros  
Controles: MFA, RBAC, validação server-side, logs, tratamento seguro de erro, rate limit

**Ativo: Banco de Dados**  
Função: armazenamento de dados críticos  
Ameaças: vazamento de dados, alteração indevida, abuso de privilégio, indisponibilidade  
Controles: criptografia, segregação de contas, backup, hardening, monitoramento

**Ativo: Serviço Externo**  
Função: integração com terceiro  
Ameaças: confiança excessiva, vazamento em integração, indisponibilidade do parceiro  
Controles: autenticação mútua, validação de origem, timeout, monitoramento, segregação de segredos

---

# Exemplo de conclusão profissional

Com base no DFD da aplicação, foram identificados os principais ativos do ecossistema, os fluxos de dados entre frontend, backend, banco de dados e integrações externas, bem como os limites de confiança existentes entre as camadas. A partir dessa decomposição, foi aplicada a metodologia STRIDE para identificar ameaças relacionadas à falsificação de identidade, alteração indevida de dados, ausência de rastreabilidade, exposição de informações, indisponibilidade e elevação de privilégios. Para cada ativo e fluxo relevante, foram definidos pontos de controle de segurança com o objetivo de reduzir a probabilidade de exploração e aumentar a resiliência da aplicação.

---

# Modelo curto de legenda para imagem

Você pode colocar embaixo do desenho assim:

**Legenda:** azul representa ativos, vermelho representa ameaças identificadas e verde representa controles de segurança. As linhas tracejadas indicam mudanças de confiança entre camadas do sistema.