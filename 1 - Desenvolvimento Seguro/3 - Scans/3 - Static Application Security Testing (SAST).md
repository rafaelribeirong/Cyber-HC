# Static Application Security Testing (SAST)

Static Application Security Testing (SAST) é uma técnica de segurança utilizada para **analisar o código fonte de uma aplicação sem executá-la**. O objetivo dessa abordagem é identificar vulnerabilidades diretamente no código durante o processo de desenvolvimento.

O SAST analisa o código proprietário da aplicação e identifica **padrões inseguros, falhas de lógica e vulnerabilidades conhecidas** que podem comprometer a segurança do sistema.

Diferente de testes dinâmicos, o SAST funciona como um **revisor automático de código**, analisando a estrutura do software antes mesmo da aplicação ser executada ou implantada em produção.

---

# Visão geral do SAST

![Image](https://res.cloudinary.com/snyk/image/upload/v1663714812/wordpress-sync/Learn-SAST-stages-graphic.png)

![Image](https://res.cloudinary.com/snyk/image/upload/f_auto%2Cw_2560%2Cq_auto/v1663714812/wordpress-sync/Learn-SAST-stages-graphic.png)

![Image](https://www.sei.cmu.edu/media/images/SCALe_Art1_EDN6JTX.original.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ASqv1UtIsKHsGtekKewlw3A.jpeg)

Durante o processo de análise, a ferramenta examina o código fonte e procura por padrões que indiquem falhas de segurança, como uso incorreto de funções, validação inadequada de dados ou manipulação insegura de informações sensíveis.

Essa análise pode ser integrada diretamente ao processo de desenvolvimento, permitindo que vulnerabilidades sejam identificadas **ainda nas primeiras etapas do ciclo de desenvolvimento de software**.

---

# Como o SAST funciona

O funcionamento do SAST baseia-se em várias técnicas de análise de código. Essas técnicas permitem que a ferramenta compreenda a estrutura do programa e identifique padrões de vulnerabilidades.

O processo geralmente ocorre em três etapas principais.

---

# Análise léxica e sintática

![Image](https://upload.wikimedia.org/wikipedia/commons/c/c7/Abstract_syntax_tree_for_Euclidean_algorithm.svg)

![Image](https://raw.githubusercontent.com/Codecademy/docs/main/media/abstract-syntax-tree.png)

![Image](https://i.sstatic.net/dhd3v.png)

A primeira etapa consiste na análise léxica e sintática do código.

Nesse processo, o código fonte é transformado em estruturas que permitem à ferramenta compreender sua lógica.

O código é dividido em **tokens**, que representam os elementos básicos da linguagem de programação, como variáveis, operadores, funções e estruturas de controle.

Esses tokens são organizados em uma estrutura chamada **Abstract Syntax Tree (AST)**, que representa a estrutura lógica do código.

A AST permite que a ferramenta entenda como o programa funciona e como as diferentes partes do código se relacionam.

---

# Aplicação de regras de segurança

Após a construção da árvore sintática, a ferramenta aplica um conjunto de regras de segurança para identificar possíveis vulnerabilidades.

Essas regras podem incluir diferentes tipos de análise.

Pattern matching  
A ferramenta busca padrões conhecidos de código vulnerável.

Análise de fluxo de dados  
Analisa como os dados se movem dentro da aplicação.

Análise de fluxo de controle  
Avalia a lógica do programa para identificar caminhos inseguros ou comportamentos inesperados.

Essa fase permite identificar vulnerabilidades que podem surgir a partir da interação entre diferentes partes do código.

---

# Detecção de vulnerabilidades

Após a análise estrutural do código, a ferramenta realiza a detecção de vulnerabilidades.

Esse processo envolve a comparação do código analisado com padrões conhecidos de vulnerabilidades.

Um conceito importante nessa etapa é o rastreamento de dados entre **source e sink**.

Source representa o ponto onde os dados entram no sistema, como entrada de usuário ou parâmetros de requisições.

Sink representa o ponto onde esses dados são utilizados em operações sensíveis, como consultas a banco de dados ou execução de comandos.

Se dados provenientes de uma fonte não confiável chegam a um ponto crítico do sistema sem validação adequada, a ferramenta pode identificar uma vulnerabilidade.

---

# Vulnerabilidades detectadas pelo SAST

O SAST é capaz de identificar diversos tipos de vulnerabilidades presentes no código fonte.

Entre as mais comuns estão:

SQL Injection  
Cross-Site Scripting (XSS)  
Command Injection  
Path Traversal  
uso inseguro de criptografia  
exposição de dados sensíveis  
validação incorreta de entrada  
problemas de controle de acesso

Essas vulnerabilidades geralmente estão relacionadas a falhas na implementação do código ou ao uso incorreto de bibliotecas e frameworks.

---

# Limitações do SAST

Apesar de ser uma ferramenta extremamente útil, o SAST também possui algumas limitações.

Uma das principais limitações é que ele analisa apenas o código estático da aplicação, sem considerar o comportamento real do sistema em execução.

Isso significa que algumas vulnerabilidades que dependem do ambiente de execução ou de interações específicas podem não ser detectadas.

Outra limitação é a possibilidade de falsos positivos.

Como a análise é baseada em padrões, algumas ferramentas podem identificar problemas que na prática não representam uma vulnerabilidade real.

Além disso, o SAST pode ter dificuldades para identificar vulnerabilidades relacionadas à lógica de negócio da aplicação.

---

# Ferramentas de SAST

Diversas ferramentas são utilizadas para realizar análises SAST em aplicações.

Cada uma possui características específicas, podendo oferecer suporte a diferentes linguagens de programação e níveis de integração com pipelines de desenvolvimento.

Entre as ferramentas mais utilizadas estão:

Semgrep  
Horussec  
SonarQube  
Veracode  
Checkmarx

---

# Semgrep

![Image](https://raw.githubusercontent.com/semgrep/semgrep/develop/images/semgrep-main-image.jpg)

![Image](https://semgrep.dev/assets/blog/2025/img_0646111.png)

![Image](https://raw.githubusercontent.com/semgrep/semgrep/develop/images/semgrep-example-rules-editor.jpg)

![Image](https://semgrep.dev/docs/assets/images/semgrep-ci-4c94be66f30fef156679254592d3e2b1.gif)

Semgrep é uma ferramenta moderna de análise estática de código que se tornou bastante popular entre equipes de segurança e desenvolvimento.

Ela possui versão gratuita com regras da comunidade e também uma versão paga com recursos avançados.

Entre suas principais características estão:

suporte a mais de 30 linguagens de programação  
alta velocidade de análise  
facilidade de criação de regras personalizadas  
integração com pipelines de CI/CD

Uma das principais vantagens do Semgrep é a possibilidade de criar regras de análise utilizando arquivos YAML.

Isso permite que equipes de segurança criem regras específicas para identificar vulnerabilidades dentro de seus próprios padrões de desenvolvimento.

---

# Conclusão

O Static Application Security Testing é uma das técnicas mais importantes para identificar vulnerabilidades durante o desenvolvimento de software.

Ao analisar o código fonte de forma automatizada, o SAST permite detectar falhas antes que a aplicação seja implantada em produção.

Apesar de possuir limitações, quando combinado com outras técnicas de segurança, como testes dinâmicos e análise de dependências, o SAST contribui significativamente para o desenvolvimento de aplicações mais seguras.