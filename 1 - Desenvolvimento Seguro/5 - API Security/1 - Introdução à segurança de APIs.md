# OWASP crAPI (Completely Ridiculous API)

O **OWASP crAPI** (Completely Ridiculous API) é um projeto da OWASP criado para **treinamento prático de segurança em APIs**. Ele foi desenvolvido para permitir que profissionais de segurança, desenvolvedores e estudantes possam **praticar exploração de vulnerabilidades em APIs reais em um ambiente controlado**.

Diferente de aplicações de treinamento simples, o crAPI simula um sistema moderno composto por múltiplos serviços, incluindo backend, banco de dados e interfaces web. Ele contém diversas vulnerabilidades intencionalmente inseridas para permitir a prática de testes de segurança.

Esse projeto é amplamente utilizado para aprendizado de **API Security**, especialmente para estudar vulnerabilidades presentes no **OWASP API Security Top 10**.

OWASP crAPI:  
[https://owasp.org/www-project-crapi/](https://owasp.org/www-project-crapi/)

---

# Interface e ambiente da aplicação

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ALEVQYx4sirSUSQfo8grsyg.png)

![Image](https://cdn.prod.website-files.com/65c5190e5dd9c9f6dde799df/667fa69b54fd8006e6777edd_0%2A3NMy9Yru7D-xOCaO.webp)

![Image](https://opengraph.githubassets.com/d2f64f9208ff5790ee3dff7a8c43404be1f86dd982774338a66cd1dd3adcf1ed/OWASP/crAPI)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1358/format%3Awebp/1%2A6nQpoJzi4XKA_8n6MOzmww.png)

A aplicação simula uma plataforma onde usuários podem gerenciar veículos conectados. Dentro desse ambiente existem diversas funcionalidades que interagem com APIs internas.

Essas APIs possuem vulnerabilidades que podem ser exploradas durante exercícios de segurança, como falhas de autenticação, controle de acesso inadequado e exposição de dados sensíveis.

---

# Objetivo do crAPI

O principal objetivo do crAPI é permitir que profissionais pratiquem **testes de segurança em APIs modernas**.

Entre os cenários abordados no laboratório estão:

quebra de autenticação  
falhas de autorização  
exposição de dados sensíveis  
problemas de validação de entrada  
acesso indevido a recursos de outros usuários

Essas vulnerabilidades refletem problemas comuns encontrados em APIs reais.

---

# Tecnologias utilizadas

O crAPI utiliza uma arquitetura baseada em microsserviços.

Entre os componentes utilizados estão:

backend em aplicações web  
serviços de API  
banco de dados  
fila de mensagens  
interface web para interação

Toda essa estrutura é executada utilizando **containers Docker**, o que facilita a instalação e execução do laboratório.

---

# Arquitetura da aplicação

![Image](https://microservices.io/i/Microservice_Architecture.png)

![Image](https://miro.medium.com/1%2Aqxud6ywar_bt3OAjqL4Peg.png)

![Image](https://labs.iximiuz.com/content/files/tutorials/docker-security-introduction-a859718d/__static__/docker-security-docker-architecture-2.png)

![Image](https://media.springernature.com/lw1200/springer-static/image/art%3A10.1038%2Fs41598-025-16460-0/MediaObjects/41598_2025_16460_Fig1_HTML.png)

A arquitetura do crAPI normalmente inclui:

frontend web  
API gateway  
serviços backend  
banco de dados  
componentes auxiliares

Essa estrutura permite simular um ambiente real de aplicações baseadas em APIs.

---

# Ferramentas necessárias

Para executar o crAPI localmente são necessárias algumas ferramentas.

As principais são:

Docker Desktop  
Git  
Navegador web  
Burp Suite

Links oficiais:

Docker Desktop  
[https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)

Burp Suite Community Edition  
[https://portswigger.net/burp/communitydownload](https://portswigger.net/burp/communitydownload)

---

# O que é Docker

Docker é uma plataforma que permite executar aplicações dentro de containers.

Containers são ambientes isolados que possuem todas as dependências necessárias para executar um software.

Isso permite que aplicações complexas sejam executadas facilmente em diferentes sistemas operacionais sem necessidade de instalar manualmente todas as dependências.

---

# Instalação do Docker

![Image](https://www.docker.com/app/uploads/2022/06/Screen-Shot-2022-06-02-at-9.22.51-AM-1-1110x668.png)

![Image](https://www.researchgate.net/publication/369061128/figure/fig2/AS%3A11431281125201275%401678232029210/Docker-Container-vs-Virtual-Machine.png)

![Image](https://www.docker.com/app/uploads/2022/08/Dashboard-View-Container-Details-1110x665.png)

![Image](https://www.docker.com/app/uploads/2022/08/Dashboard-Integrated-CLI-1110x772.png)

Para instalar o Docker Desktop:

1. Acesse o site oficial
    

[https://docs.docker.com/desktop/](https://docs.docker.com/desktop/)

2. Baixe a versão correspondente ao seu sistema operacional.
    
3. Execute o instalador.
    
4. Após a instalação, abra o Docker Desktop.
    
5. Verifique se o Docker está funcionando executando no terminal:
    

```
docker --version
```

---

# Instalando o crAPI

A forma mais simples de instalar o crAPI é utilizando Docker.

Primeiro é necessário clonar o repositório do projeto.

No terminal execute:

```
git clone https://github.com/OWASP/crAPI.git
```

Depois entre na pasta do projeto:

```
cd crAPI
```

Em seguida execute o comando para iniciar os containers:

```
docker-compose up
```

Esse comando irá baixar as imagens necessárias e iniciar todos os serviços do laboratório.

---

# Executando a aplicação

Após iniciar os containers, a aplicação ficará disponível no navegador.

Normalmente o acesso é feito através do endereço:

```
http://localhost:8888
```

A interface da aplicação será carregada e já será possível começar a explorar as funcionalidades e as APIs do sistema.

---

# Utilizando o Burp Suite para testar a API

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-intercepted-request.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-proxy-history.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-repeater.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-product-page-request.png)

O Burp Suite é uma ferramenta amplamente utilizada para testes de segurança em aplicações web.

Ele funciona como um proxy entre o navegador e a aplicação, permitindo interceptar e modificar requisições HTTP.

Para utilizar o Burp com o crAPI:

1. Abra o Burp Suite.
    
2. Configure o navegador para utilizar o proxy do Burp.
    
3. Acesse o crAPI pelo navegador.
    
4. Intercepte as requisições enviadas para a API.
    
5. Analise e modifique os parâmetros das requisições.
    

Essa abordagem permite explorar vulnerabilidades presentes na aplicação.

---

# Exemplos de testes que podem ser realizados

Dentro do crAPI é possível praticar diversos tipos de ataques relacionados à segurança de APIs.

Entre eles:

testes de autenticação  
manipulação de tokens  
acesso a dados de outros usuários  
exploração de endpoints ocultos  
modificação de parâmetros de requisição

Esses exercícios ajudam a compreender como APIs podem ser exploradas quando não possuem controles de segurança adequados.

---

# Benefícios do uso do crAPI

O crAPI oferece diversas vantagens para aprendizado de segurança de aplicações.

Entre elas:

ambiente seguro para prática  
simulação de aplicações reais  
diversos cenários de vulnerabilidade  
integração com ferramentas de pentest

Essas características tornam o crAPI um laboratório bastante completo para treinamento em segurança de APIs.

---

# Conclusão

O OWASP crAPI é uma plataforma de treinamento projetada para ensinar segurança em APIs através de cenários práticos.

Executado localmente utilizando Docker, ele permite que profissionais pratiquem exploração de vulnerabilidades em um ambiente controlado, utilizando ferramentas reais de teste de segurança como o Burp Suite.

Essa abordagem facilita o aprendizado de técnicas de ataque e defesa em aplicações modernas baseadas em APIs.