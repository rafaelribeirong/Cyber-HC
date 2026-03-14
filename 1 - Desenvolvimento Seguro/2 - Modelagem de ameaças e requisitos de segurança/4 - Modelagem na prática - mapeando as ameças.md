# Modelagem na prática – mapeando as ameaças

A modelagem de ameaças na prática consiste em transformar a arquitetura do sistema em um modelo visual que permita identificar os ativos, compreender o fluxo de dados e analisar quais ameaças podem surgir em cada ponto da aplicação.

A partir do momento em que o sistema já possui sua arquitetura definida — normalmente durante a fase de design do ciclo de desenvolvimento de software — é possível iniciar o processo de análise de segurança. Nesse momento, os componentes da aplicação são representados em um diagrama simples que mostra como os dados trafegam entre usuários, sistemas e infraestrutura.

Esse tipo de representação permite identificar pontos críticos do sistema e compreender quais elementos precisam de proteção.

---

# Exemplo visual simplificado de arquitetura

![Image](https://owasp.org/www-community/assets/images/Data_flow1.jpg)

![Image](https://cairis.org/images/DFD.jpg)

![Image](https://developer.ibm.com/developer/default/articles/threat-modeling-microservices-openshift-4/images/credit-card-architecture.png)

![Image](https://owasp.org/www-community/assets/images/UseAndMisuseCase.jpg)

O primeiro passo consiste em representar o sistema de forma simples.

```text
Usuário
   |
   v
Frontend Web (Aplicação)
   |
   v
Backend / API
   |
   v
Banco de Dados
```

Esse diagrama representa o fluxo básico de uma aplicação web.

---

# Identificando os ativos

Após a criação do diagrama, é necessário identificar quais componentes do sistema representam ativos.

Ativos são elementos que possuem valor para o negócio ou que armazenam informações sensíveis. Esses componentes precisam ser protegidos contra acessos indevidos, manipulação ou exposição de dados.

No exemplo apresentado, os principais ativos são:

Frontend Web  
Responsável pela interface da aplicação e pela interação com os usuários.

Backend / API  
Responsável pela lógica de negócio, autenticação, processamento de dados e comunicação com outros serviços.

Banco de Dados  
Responsável pelo armazenamento de informações críticas, como dados de usuários, registros do sistema e dados operacionais.

Esses componentes compõem a base funcional da aplicação e devem ser considerados ativos críticos dentro da modelagem de ameaças.

---

# Identificando as ameaças

Depois de identificar os ativos, o próximo passo é analisar quais ameaças podem afetar cada um desses componentes.

Essa análise pode ser feita utilizando o modelo STRIDE, que ajuda a classificar ameaças em diferentes categorias.

No caso do frontend web, algumas ameaças comuns incluem ataques de Cross-Site Scripting, manipulação de parâmetros enviados pelo usuário e roubo de sessão.

No backend, ameaças frequentes envolvem falhas de autenticação, falhas de autorização, injeção de comandos ou exposição de erros da aplicação que podem revelar informações sensíveis.

No banco de dados, os riscos normalmente estão relacionados à exposição de dados, alteração indevida de registros ou acesso não autorizado.

Ao mapear essas ameaças, é possível compreender quais partes do sistema representam maior risco.

---

# Definição de pontos de controle

Após a identificação das ameaças, são definidos pontos de controle que ajudam a reduzir os riscos.

Os controles de segurança são mecanismos que protegem os ativos contra exploração.

No frontend, controles podem incluir validação de entrada de dados, proteção contra execução de scripts maliciosos e uso de comunicação segura.

No backend, podem ser implementados mecanismos de autenticação forte, controle de acesso baseado em permissões e validação rigorosa das requisições recebidas.

No banco de dados, controles podem envolver criptografia de dados sensíveis, restrição de acessos administrativos e monitoramento de atividades suspeitas.

Esses controles ajudam a reduzir a superfície de ataque da aplicação.

---

# Exemplo prático de mapeamento

```text
Usuário
   |
   | envio de dados
   v
Frontend Web
   |
   | ameaça: XSS
   | ameaça: manipulação de parâmetros
   |
   | controle: validação de entrada
   | controle: política de segurança de conteúdo
   v
Backend / API
   |
   | ameaça: SQL Injection
   | ameaça: acesso não autorizado
   |
   | controle: prepared statements
   | controle: autenticação e autorização
   v
Banco de Dados
   |
   | ameaça: vazamento de dados
   | ameaça: alteração de registros
   |
   | controle: criptografia
   | controle: controle de acesso
```

Esse modelo demonstra como cada componente do sistema pode ser analisado para identificar riscos e definir mecanismos de proteção.

---

# Considerando o ecossistema completo

A modelagem de ameaças não deve considerar apenas o código da aplicação.

Também é necessário analisar todos os elementos que fazem parte do ecossistema do sistema, incluindo infraestrutura de rede, serviços externos, dispositivos físicos e processos organizacionais.

Uma falha em qualquer uma dessas camadas pode comprometer a segurança do sistema como um todo.

---

# Conclusão

A modelagem de ameaças aplicada na prática permite transformar a arquitetura de um sistema em uma análise estruturada de riscos.

Ao identificar ativos, ameaças e controles de segurança, as organizações conseguem antecipar problemas e fortalecer a proteção de suas aplicações antes mesmo da implementação ou da implantação em produção.

Esse processo exige conhecimento técnico sobre arquitetura de sistemas e também compreensão das técnicas utilizadas em ataques cibernéticos. Quanto maior for o conhecimento do analista sobre esses fatores, mais eficaz será a modelagem de ameaças na identificação e mitigação de riscos.