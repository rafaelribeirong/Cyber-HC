Para melhorar o documento e deixar didático (como você pediu: com explicação visual e organizado), o ideal é estruturar em **3 partes**: conceito, modelo visual e planilha de controle. Assim ele vira um material reutilizável para projetos de segurança, desenvolvimento seguro ou auditoria.

---

# Testes de requisitos – criando um checklist para os controles

Quando identificamos controles de segurança ou requisitos técnicos, uma forma eficiente de verificar se eles estão implementados corretamente é **quebrar cada controle em subcontroles verificáveis**.

Isso permite:

- testar o controle de forma objetiva
    
- acompanhar o progresso da implementação
    
- atribuir responsáveis
    
- registrar evidências para auditoria
    
- priorizar correções
    

A melhor forma de organizar isso inicialmente é utilizando **uma planilha de checklist de implementação de controles**.

---

# Estrutura lógica do controle

![Image](https://www.researchgate.net/publication/348241431/figure/fig4/AS%3A976772229238788%401609892055311/Diagram-on-the-Security-by-Design-Hierarchy-of-Controls-Source-Office-for-Nuclear.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AyQxiKLdOZuxUVBdXWmFn2g.png)

![Image](https://www.researchgate.net/publication/284509993/figure/tbl9/AS%3A667601147539460%401536179925151/Simple-Assessment-Checklist-for-Application-Security-Architecture.png)

![Image](https://dz2cdn1.dzone.com/storage/temp/15203594-ssengupta-figure-1.png)

O processo funciona da seguinte forma:

Controle → Subcontroles → Testes → Evidência

Exemplo:

Controle  
Validação de entrada de dados do usuário

Esse controle é dividido em subcontroles técnicos.

Subcontroles possíveis:

Validação de tipo de dado  
Validação de tamanho máximo  
Validação de caracteres especiais  
Sanitização de entrada  
Prevenção de injeção de código

Cada um desses itens pode ser **testado individualmente**.

---

# Exemplo de decomposição de controle

Controle  
Filtro de entrada de dados do usuário

Subcontrole 1.1  
Validar tipo de dados do usuário

Verificação esperada

- string
    
- inteiro
    
- booleano
    
- data
    

Subcontrole 1.2  
Validar tamanho máximo de entrada

Verificação esperada

- limite definido para cada campo
    
- bloqueio de payload excessivo
    

Subcontrole 1.3  
Validar caracteres especiais

Verificação esperada

- sanitização de caracteres perigosos
    
- bloqueio de scripts ou comandos
    

Subcontrole 1.4  
Sanitização da entrada

Verificação esperada

- escape de caracteres especiais
    
- prevenção de SQL Injection e XSS
    

---

# Modelo de planilha para controle de implementação

A planilha serve para **acompanhar o status real da implementação**.

Estrutura recomendada:

Controle  
ID do Subcontrole  
Descrição do Subcontrole  
Critério de verificação  
Status  
Responsável  
Data prevista  
Data de conclusão  
Evidência  
Observações

---

# Exemplo de preenchimento da planilha

|Controle|ID|Subcontrole|Critério de verificação|Status|Responsável|Data prevista|Evidência|Observação|
|---|---|---|---|---|---|---|---|---|
|Validação de entrada|1.1|Validar tipo de dado|Sistema valida string, inteiro ou booleano|Implementado|Dev Backend|10/04|Código de validação|Validado no backend|
|Validação de entrada|1.2|Limite de tamanho|Campos possuem limite definido|Em implementação|Dev Backend|12/04|Teste unitário|Limite 255 caracteres|
|Validação de entrada|1.3|Filtrar caracteres especiais|Bloqueio de scripts|Planejado|Dev Backend|15/04|Teste de segurança|Prevenir XSS|

---

# Status recomendados

Para padronizar o acompanhamento:

Não iniciado  
Planejado  
Em implementação  
Implementado  
Testado  
Validado

---

# Evidências recomendadas

Para comprovar a implementação do controle:

- código implementado
    
- teste unitário
    
- relatório de teste de segurança
    
- captura de tela
    
- documentação técnica
    
- pipeline de CI/CD
    
- ferramenta de análise estática
    

---

# Benefícios dessa abordagem

Rastreabilidade do requisito  
Controle de implementação  
Base para auditoria de segurança  
Facilidade para priorização de correções  
Visão clara de maturidade do controle