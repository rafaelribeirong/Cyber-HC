# Dynamic Application Security Testing (DAST)

Dynamic Application Security Testing (DAST) é uma técnica de segurança utilizada para analisar aplicações **em execução**. Diferente do SAST, que examina o código fonte, o DAST testa a aplicação a partir de fora, simulando o comportamento de um atacante real.

Esse tipo de teste interage diretamente com a aplicação através de requisições HTTP, analisando como o sistema responde a diferentes entradas e comportamentos inesperados.

O DAST trabalha em **modo black box**, ou seja, a análise ocorre sem acesso ao código fonte da aplicação. A ferramenta apenas interage com a aplicação da mesma forma que um usuário ou atacante faria.

---

# Visão geral do DAST

![Image](https://cdn.acunetix.com/wp_content/uploads/2017/08/image2-1.png)

![Image](https://cdn-blog.getastra.com/2024/08/77901847-dynamic-application-security-testing-process.png)

![Image](https://www.opentext.com/assets/images/products-solutions/product-details/opentext-image-ov-products-dynamic-application-security-testing-en.jpg)

Durante a execução de um teste DAST, a ferramenta envia diferentes tipos de requisições para a aplicação e observa as respostas retornadas.

Essas respostas são analisadas para identificar comportamentos que indiquem vulnerabilidades, como erros inesperados, exposição de dados ou falhas de validação.

Esse método permite identificar vulnerabilidades que apenas aparecem quando a aplicação está em funcionamento.

---

# Como o DAST funciona

O processo de análise DAST normalmente segue algumas etapas principais.

Primeiro, a ferramenta realiza um processo de **crawling**, identificando páginas, endpoints, parâmetros e funcionalidades da aplicação.

Após mapear a estrutura da aplicação, a ferramenta começa a enviar requisições com diferentes tipos de entradas maliciosas, tentando explorar possíveis vulnerabilidades.

Durante esse processo, a ferramenta analisa as respostas do servidor para identificar sinais de exploração bem-sucedida.

Esse comportamento permite detectar vulnerabilidades como falhas de validação, erros de configuração e problemas de lógica de aplicação.

---

# Tipos de vulnerabilidades detectadas

![Image](https://cdn.acunetix.com/wp_content/uploads/2012/10/image01.png)

![Image](https://cdn.prod.website-files.com/5ff66329429d880392f6cba2/67614de3b9a2a1125eb4caaf_613afbb3f677add6ebeb2123_Cross-Site%2520Scripting%2520%28XSS%29%2520example.png)

![Image](https://cdn.acunetix.com/wp_content/uploads/2020/02/v13_dashboard_narrow.png)

![Image](https://portswigger.net/web-security/images/os-command-injection.svg)

O DAST pode identificar diversas vulnerabilidades presentes em aplicações web.

Entre as mais comuns estão:

SQL Injection  
Cross-Site Scripting (XSS)  
Command Injection  
File Inclusion  
exposição de diretórios  
configurações inseguras do servidor  
problemas de autenticação  
problemas de autorização

Essas vulnerabilidades são detectadas através da interação direta com a aplicação.

---

# Importância do DAST

O DAST é extremamente importante porque analisa o comportamento real da aplicação durante sua execução.

Esse tipo de teste permite identificar problemas que não aparecem apenas analisando o código.

Entre os principais benefícios dessa abordagem estão:

identificação de problemas de configuração do ambiente  
detecção de vulnerabilidades exploráveis em tempo de execução  
validação do funcionamento de mecanismos de segurança  
simulação de ataques reais contra a aplicação

Além disso, o DAST permite validar se mecanismos de defesa estão funcionando corretamente.

Isso inclui, por exemplo:

validação do comportamento de firewalls de aplicação (WAF)  
verificação de respostas do servidor a entradas maliciosas  
identificação de falhas na lógica de negócio da aplicação

Esse tipo de teste permite entender como um atacante externo enxergaria a aplicação.

---

# Limitações do DAST

Apesar de ser extremamente útil, o DAST também possui algumas limitações.

Uma das principais limitações é que ele não possui acesso ao código fonte da aplicação. Isso significa que algumas vulnerabilidades internas podem não ser identificadas.

Outra limitação é que o DAST depende da cobertura da aplicação durante o teste.

Se determinadas funcionalidades não forem descobertas durante o crawling, elas podem não ser analisadas pela ferramenta.

Além disso, o DAST pode ter dificuldade para identificar problemas relacionados à lógica interna do código ou vulnerabilidades que dependem de condições específicas de execução.

---

# Ferramentas de DAST

Diversas ferramentas são utilizadas para realizar testes dinâmicos de segurança em aplicações.

Cada uma possui características específicas e pode ser utilizada em diferentes cenários.

Entre as ferramentas mais utilizadas estão:

Nuclei  
OWASP ZAP  
Burp Suite  
Dastardly  
Fortify

---

# Nuclei

![Image](https://escape.tech/blog/content/images/2021/11/image-8.png)

![Image](https://user-images.githubusercontent.com/17493961/184608061-62946978-7969-439b-a5fb-b6db08ffdcfb.png)

![Image](https://user-images.githubusercontent.com/8293321/205839007-b18a1dc2-5b4e-4ee4-9051-c13b30089ee3.png)

![Image](https://www.bleepstatic.com/content/hl-images/2025/01/04/nuclei-header.jpg)

Nuclei é uma ferramenta de escaneamento de vulnerabilidades desenvolvida pela ProjectDiscovery.

Ela funciona utilizando **templates de vulnerabilidade**, que descrevem como testar diferentes tipos de falhas de segurança.

Esses templates podem ser utilizados para identificar problemas em aplicações web, serviços de rede e infraestrutura.

O Nuclei é conhecido por sua velocidade e pela grande quantidade de templates disponíveis na comunidade.

---

# OWASP ZAP

![Image](https://devopedia.org/images/article/72/2450.1523863706.jpg)

![Image](https://miro.medium.com/0%2AjCFrG9pCJQcti4_F)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2AQP77yDHTPcnLxaPOgUZ6kQ.jpeg)

OWASP ZAP é uma das ferramentas de DAST mais populares.

Ela atua como um proxy de interceptação que permite analisar o tráfego entre o navegador e a aplicação.

Entre suas funcionalidades estão:

varredura automatizada de vulnerabilidades  
interceptação de requisições HTTP  
fuzzing de parâmetros  
descoberta de endpoints da aplicação

Por ser um projeto da OWASP, o ZAP é amplamente utilizado em ambientes de teste de segurança.

---

# Burp Suite

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/pro-qsg-4-crawl-and-audit.png)

![Image](https://portswigger.net/cms/images/6c/1f/ff52e6c1d69e-article-dashboard_-_small.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-intercepted-request.png)

![Image](https://portswigger.net/burp/documentation/desktop/images/getting-started/quick-start-pro-proxy-history.png)

Burp Suite é uma das ferramentas mais utilizadas por profissionais de pentest.

Ela possui diversas funcionalidades para análise de segurança em aplicações web.

Entre seus principais recursos estão:

proxy de interceptação  
scanner de vulnerabilidades  
ferramentas de fuzzing  
análise manual de requisições HTTP

A ferramenta possui versões comunitária e profissional.

---

# Dastardly

![Image](https://miro.medium.com/1%2A6GB_IrGKSkWUEbs06f8plQ.png)

![Image](https://opengraph.githubassets.com/b61ae063280225a824eba442632402f67091cf863c4cda16fa8cb982bfb98bc3/Apetree333/Dastardly)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2A6GB_IrGKSkWUEbs06f8plQ.png)

![Image](https://images.softwaresuggest.com/latest_screenshots/1686227981_Scan%2BWith%2BDastardly.jpg)

Dastardly é uma ferramenta de DAST desenvolvida pela PortSwigger.

Ela foi projetada principalmente para integração com pipelines de CI/CD.

Seu objetivo é automatizar testes de segurança em aplicações web durante o processo de desenvolvimento.

---

# Fortify

![Image](https://www.microfocus.com/documentation/fortify-webinspect/2220/WI_Help_22.2.0/Content/Resources/Images/Panes.png)

![Image](https://www.microfocus.com/documentation/fortify-webinspect/2220/WI_Help_22.2.0/Content/Resources/Images/Dashboard2.png)

![Image](https://www.microfocus.com/documentation/fortify-ScanCentral-DAST/2310/SC_DAST_Help_23.1.0/Content/Resources/Images/Dyn_Arch.png)

![Image](https://www.opentext.com/assets/images/products-solutions/product-details/opentext-image-ov-products-dynamic-application-security-testing-en.jpg)

Fortify é uma plataforma comercial de segurança de aplicações que oferece soluções para análise estática e dinâmica de segurança.

Na parte de DAST, o Fortify permite realizar testes automatizados em aplicações web para identificar vulnerabilidades exploráveis em tempo de execução.

---

# Conclusão

Dynamic Application Security Testing é uma abordagem fundamental para avaliar a segurança de aplicações em execução.

Ao simular ataques reais contra o sistema, o DAST permite identificar vulnerabilidades que podem não ser detectadas por análises de código.

Quando utilizado em conjunto com outras técnicas de segurança, como SAST e análise de dependências, o DAST contribui para a construção de aplicações mais seguras e resilientes contra ataques.