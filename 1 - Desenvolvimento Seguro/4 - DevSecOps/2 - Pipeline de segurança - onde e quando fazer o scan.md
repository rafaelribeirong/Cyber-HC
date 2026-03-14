# Pipeline de segurança – onde e quando fazer o scan

Uma pipeline de segurança em DevSecOps define **em quais momentos do ciclo de desenvolvimento de software os testes de segurança devem ser executados**. O objetivo é detectar vulnerabilidades o mais cedo possível, reduzindo o custo de correção e evitando que falhas cheguem ao ambiente de produção.

A segurança deve ser distribuída ao longo de toda a pipeline de CI/CD, desde o momento em que o desenvolvedor escreve o código até a aplicação estar em produção.

Essa abordagem é conhecida como **shift left security**, onde as verificações de segurança são realizadas o mais cedo possível no processo de desenvolvimento.

---

# Visão geral da pipeline de segurança

![Image](https://res.cloudinary.com/snyk/image/upload/f_auto/q_auto/v1613516895/wordpress-sync/DevSecOps-Pipeline.png)

![Image](https://www.paloaltonetworks.com.br/content/dam/pan/en_US/images/cyberpedia/various-steps-in-the-ci-cd-pipeline.png?imwidth=480)

![Image](https://sunbytes.io/app/uploads/2025/07/DevSecOps-Pipeline-Post--scaled.webp)

![Image](https://sunbytes.io/app/uploads/2025/06/DevSecOps-pipeline-k21academy.webp)

Uma pipeline DevSecOps normalmente possui várias etapas, e cada uma delas pode incluir verificações específicas de segurança.

Entre as principais fases da pipeline estão:

desenvolvimento  
commit de código  
build da aplicação  
testes  
deploy  
produção

Cada fase permite aplicar diferentes tipos de análise de segurança.

---

# Fase de desenvolvimento

A primeira camada de segurança acontece ainda durante o desenvolvimento da aplicação.

Nesse momento, o desenvolvedor está escrevendo o código e já pode utilizar ferramentas que ajudam a evitar vulnerabilidades.

Nessa fase podem ser utilizados:

linters de segurança  
plugins de análise estática no IDE  
verificação de dependências inseguras

Essas ferramentas ajudam a detectar problemas básicos antes mesmo do código ser enviado para o repositório.

Essa etapa reduz significativamente o número de vulnerabilidades que chegam à pipeline.

---

# Fase de commit

![Image](https://owasp.org/www-project-devsecops-guideline/latest/assets/images/pre-commit.png)

![Image](https://blog.gitguardian.com/content/images/2022/07/pipeline-steps-pre-receive-focus.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/0%2AzItq4H7RnwVzOAJ8.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1200/1%2AzWZTALUXb971Oyof_n2tCA.png)

Quando o desenvolvedor realiza um commit no repositório, a pipeline pode executar verificações automáticas.

Essas verificações podem incluir:

secret scanning  
verificação de dependências vulneráveis  
checagem de qualidade de código

Um exemplo comum é a utilização de **pre-commit hooks**, que executam verificações antes que o código seja aceito no repositório.

Essa abordagem evita que credenciais ou códigos inseguros sejam adicionados ao projeto.

---

# Fase de build

Durante o processo de build da aplicação, novas verificações de segurança podem ser executadas.

Essa etapa é ideal para executar análises mais profundas do código.

Entre os testes comuns nessa fase estão:

SAST – análise estática de código  
SCA – análise de dependências  
verificação de bibliotecas vulneráveis

Esses testes ajudam a identificar vulnerabilidades estruturais presentes no código ou em bibliotecas utilizadas pelo projeto.

---

# Fase de testes

![Image](https://cdn-blog.getastra.com/2024/08/77901847-dynamic-application-security-testing-process.png)

![Image](https://www.paloaltonetworks.com/content/dam/pan/en_US/images/cyberpedia/CI_CD%20Security%20-%201.png?imwidth=480)

![Image](https://media2.dev.to/dynamic/image/width%3D1280%2Cheight%3D720%2Cfit%3Dcover%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fnybog81s9setu5wbshg8.png)

![Image](https://media.licdn.com/dms/image/v2/D5612AQFD9ZejQyF4cQ/article-cover_image-shrink_600_2000/article-cover_image-shrink_600_2000/0/1726893749322?e=2147483647&t=W2L0FFHfFwJ5ZGMS8y8JJ12PbpvS3Zn_Bs4UfCC90dM&v=beta)

Após o build da aplicação, a pipeline normalmente executa testes automatizados.

Nesse momento também podem ser executados testes dinâmicos de segurança.

Entre os testes mais comuns estão:

DAST – análise dinâmica da aplicação  
testes automatizados de segurança  
fuzzing de parâmetros  
análise de APIs

Esses testes verificam o comportamento da aplicação em execução, simulando possíveis ataques.

---

# Fase de deploy

Antes de implantar a aplicação em produção, podem ser executadas verificações adicionais de segurança.

Essa etapa pode incluir:

container scanning  
verificação de infraestrutura  
análise de configurações de segurança

Esses testes ajudam a identificar problemas relacionados ao ambiente onde a aplicação será executada.

---

# Fase de produção

Mesmo após a implantação da aplicação, a segurança deve continuar sendo monitorada.

Essa etapa envolve monitoramento contínuo do ambiente.

Entre as práticas comuns estão:

monitoramento de logs de segurança  
detecção de atividades suspeitas  
varreduras periódicas de vulnerabilidades  
análise de comportamento da aplicação

Essa abordagem permite identificar rapidamente possíveis incidentes de segurança.

---

# Exemplo de pipeline de segurança completa

```text
Desenvolvimento
│
├─ verificação de código no IDE
│
Commit
│
├─ secret scanning
├─ análise de dependências
│
Build
│
├─ SAST
├─ SCA
│
Testes
│
├─ DAST
├─ testes de segurança automatizados
│
Deploy
│
├─ container scanning
├─ verificação de infraestrutura
│
Produção
│
├─ monitoramento
├─ detecção de ameaças
```

Esse modelo mostra como diferentes tipos de análise podem ser distribuídos ao longo da pipeline.

---

# Benefícios de distribuir os scans na pipeline

Executar testes de segurança em diferentes fases da pipeline traz diversos benefícios.

Entre eles:

detecção precoce de vulnerabilidades  
redução do custo de correção  
automatização da segurança  
maior confiabilidade no processo de entrega de software

Quando a segurança é integrada ao processo de desenvolvimento, torna-se possível identificar e corrigir problemas rapidamente.

---

# Conclusão

Uma pipeline de segurança bem estruturada distribui verificações de segurança ao longo de todo o ciclo de desenvolvimento de software.

Ao aplicar diferentes tipos de análise em cada etapa da pipeline, as organizações conseguem detectar vulnerabilidades mais cedo, reduzir riscos e garantir que aplicações sejam entregues com maior nível de segurança.