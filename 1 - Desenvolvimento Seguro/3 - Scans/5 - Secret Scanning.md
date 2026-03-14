# Secret Scanning

Secret Scanning é uma técnica de segurança utilizada para identificar **credenciais, tokens, chaves de API e outros segredos sensíveis expostos dentro do código fonte ou em repositórios de versionamento**.

Esse tipo de análise é fundamental porque aplicações modernas utilizam diversas integrações com serviços externos, como provedores de cloud, APIs, bancos de dados e serviços de autenticação. Cada uma dessas integrações geralmente depende de algum tipo de credencial para funcionar.

Quando essas credenciais são inseridas diretamente no código e posteriormente enviadas para um repositório, elas podem ser expostas e utilizadas por atacantes.

---

# Visão geral do Secret Scanning

![Image](https://blog.gitguardian.com/content/images/2022/07/pipeline-steps-pre-receive-focus.png)

![Image](https://connect.coveo.com/servlet/rtaImage?eid=ka6VO00000042EX&feoid=00N0d000003GnER&refid=0EMVO00000Es65B)

![Image](https://substackcdn.com/image/fetch/%24s_%21GNf3%21%2Cf_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F6e212817-db49-4a2b-b12c-93c0500719e4_1734x802.jpeg)

![Image](https://blog.gitguardian.com/content/images/2022/04/22W15-A-practical-guide-on-how-to-investigate-1.jpg)

O Secret Scanning analisa o conteúdo do repositório procurando padrões que indiquem a presença de credenciais ou dados sensíveis.

Entre os elementos mais comuns detectados estão:

tokens de autenticação  
chaves de API  
credenciais de acesso a banco de dados  
tokens de acesso a serviços cloud  
certificados privados  
segredos utilizados em integrações de sistemas

Essas informações podem ser utilizadas por atacantes para comprometer sistemas, acessar dados sensíveis ou assumir o controle de serviços críticos.

---

# O problema dos segredos expostos

Um dos principais problemas relacionados a segredos expostos é que muitas vezes eles permanecem no histórico do repositório mesmo após serem removidos do código.

Isso ocorre porque sistemas de versionamento, como Git, mantêm o histórico completo de alterações realizadas no projeto.

Isso significa que, mesmo que uma credencial seja removida em um commit posterior, ela ainda pode existir em versões anteriores do repositório.

Outro fator importante é que repositórios públicos são constantemente monitorados por atacantes utilizando ferramentas automatizadas que procuram credenciais expostas.

Basta que um único segredo seja exposto para que toda a infraestrutura associada àquela credencial seja comprometida.

---

# Importância do Secret Scanning

![Image](https://media2.dev.to/dynamic/image/width%3D1000%2Cheight%3D420%2Cfit%3Dcover%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fgdd8ja3xviyb2crilvs7.png)

![Image](https://miro.medium.com/1%2AhHKqIhTRffg0DDE3-InarQ.png)

![Image](https://www.paloaltonetworks.com/content/dam/pan/en_US/images/cyberpedia/CI_CD%20Security%20-%201.png?imwidth=480)

![Image](https://res.cloudinary.com/snyk/image/upload/f_auto%2Cw_2560%2Cq_auto/v1688058589/blog-secure-cicd-integrate-early-graphic.jpg)

O Secret Scanning é um processo essencial para identificar rapidamente segredos expostos dentro de repositórios.

Essa análise pode ser aplicada em diferentes momentos do ciclo de desenvolvimento.

Ela pode ser executada durante o processo de desenvolvimento, antes que o código seja enviado para o repositório, ou pode ser aplicada posteriormente para analisar o histórico completo do projeto.

O processo de detecção normalmente utiliza uma combinação de técnicas.

Uma das técnicas mais utilizadas é a identificação de padrões utilizando expressões regulares.

Essas expressões permitem identificar formatos conhecidos de credenciais, como chaves de API ou tokens de autenticação.

Outra técnica comum é a análise de entropia.

Credenciais geralmente possuem um alto nível de aleatoriedade, e a análise de entropia permite identificar sequências de caracteres que apresentam esse comportamento.

Além disso, muitas ferramentas também utilizam listas de padrões conhecidos de credenciais utilizadas por serviços populares.

---

# Onde o Secret Scanning pode ser aplicado

O Secret Scanning pode ser aplicado em diferentes momentos do processo de desenvolvimento.

Ele pode ser utilizado como um controle preventivo durante o desenvolvimento ou como uma análise retrospectiva para identificar segredos que já foram expostos.

Entre os cenários mais comuns estão:

análise antes do commit do código  
análise durante pipelines de integração contínua  
análise do histórico completo de repositórios  
monitoramento de repositórios públicos

Essa abordagem permite identificar rapidamente possíveis exposições de credenciais e reduzir o impacto de vazamentos.

---

# Ferramentas de Secret Scanning

Existem diversas ferramentas utilizadas para realizar secret scanning em repositórios.

Entre as mais conhecidas estão:

Gitleaks  
TruffleHog

Essas ferramentas são amplamente utilizadas por equipes de segurança e desenvolvimento para identificar credenciais expostas em projetos.

---

# Gitleaks

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AQN982nzMTFQa6ymtk7qnXQ.png)

![Image](https://camo.githubusercontent.com/b3b28d30d78edee4f02f6aefdb8a5a15d62fcef9824efaeb79fa40464c2d34c2/68747470733a2f2f61736369696e656d612e6f72672f612f3435353638332e737667)

![Image](https://opengraph.githubassets.com/07a189ce857edf9ff302cd12ce1cfb6366590c4e2df89b03a095f869d70d00da/gitleaks/gitleaks)

![Image](https://miro.medium.com/1%2AhnyOvQI_MxqcqXYS3ayvFA.png)

Gitleaks é uma ferramenta de secret scanning especializada em repositórios Git.

Ela foi desenvolvida utilizando a linguagem Go, o que permite alto desempenho durante a análise de grandes repositórios.

Entre suas principais características estão:

análise rápida de repositórios  
suporte a análise de histórico completo de commits  
regras personalizáveis  
integração com pipelines de CI/CD

A ferramenta possui uma comunidade ativa que contribui constantemente com novas regras para identificar diferentes tipos de segredos.

---

# TruffleHog

![Image](https://framerusercontent.com/images/3jysw0g9cOerR8lk4u4oq56EQ.png?height=854&width=1600)

![Image](https://storage.googleapis.com/truffle-demos/non-interactive.svg)

![Image](https://blog.openreplay.com/images/scanning-repo-secrets-trufflehog/images/hero.png)

![Image](https://storage.googleapis.com/trufflehog-static-sources/pixel_pig.png)

TruffleHog é uma das ferramentas pioneiras em secret scanning.

Ela se tornou bastante popular por utilizar técnicas de análise de entropia para identificar credenciais potencialmente expostas.

Entre suas características principais estão:

detecção de credenciais com alta entropia  
suporte a diferentes sistemas de versionamento  
capacidade de análise de histórico completo de commits  
ampla adoção na comunidade de segurança

Essa abordagem permite identificar credenciais que não seguem padrões conhecidos, aumentando a capacidade de detecção de segredos expostos.

---

# Conclusão

Secret Scanning é uma prática fundamental para proteger aplicações e infraestruturas modernas contra vazamentos de credenciais.

Ao identificar segredos expostos em repositórios de código, as organizações conseguem agir rapidamente para revogar credenciais comprometidas e evitar que atacantes utilizem essas informações para acessar sistemas críticos.

Quando integrado ao processo de desenvolvimento, o Secret Scanning ajuda a reduzir significativamente o risco de exposição de dados sensíveis e fortalece a segurança do ambiente de software.