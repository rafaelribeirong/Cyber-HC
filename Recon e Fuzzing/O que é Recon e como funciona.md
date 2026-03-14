# O que é Recon (Intelligence Gathering) e como funciona

## 1) O que é Recon

**Recon (Reconnaissance)**, também chamado de **Intelligence Gathering**, é a **fase de coleta sistemática de informações** sobre um alvo **antes** de qualquer teste mais profundo.

Objetivo:

- Entender **o que existe**
    
- Mapear **superfície de ataque**
    
- Descobrir **tecnologias, endpoints, rotas, APIs e comportamentos**
    
- Reduzir achismos e aumentar precisão
    

> Em pentest web, **quem faz um bom recon, testa melhor e erra menos**.

---

## 2) Onde o Recon entra no processo de pentest

Fluxo simplificado:

```
Recon  →  Mapeamento  →  Testes  →  Validação  →  Relatório
```

Sem recon:

- testes às cegas
    
- tempo perdido
    
- falsos positivos
    

Com recon:

- foco
    
- contexto
    
- evidência técnica clara
    

---

## 3) Tipos de Recon

### Recon passivo

- Não interage diretamente com o alvo
    
- Usa fontes públicas
    
- Menor risco de ruído
    

Exemplos:

- DNS público
    
- certificados TLS
    
- headers HTTP
    
- JavaScript público
    
- motores de busca
    

---

### Recon ativo

- Interage com o alvo
    
- Envia requisições
    
- Pode gerar logs
    

Exemplos:

- enumeração de diretórios
    
- fuzzing
    
- requisições para APIs
    
- varredura de endpoints
    

---

## 4) Visão geral do Recon Web

![Image](https://attaxion.com/wp-content/uploads/2023/09/active-cyber-reconnaissance-techniques.png)

![Image](https://pentester.land/blog/compilation-of-recon-workflows/lazyrecon-workflow_hu773dabb9dc1de4f986240d4a4bdeab62_76039_932x0_resize_q75_h2_box_3.webp)

![Image](https://outpost24.com/wp-content/uploads/2023/05/Scout-AS-transparent.png)

```
Domínio
 ├── Subdomínios
 │    ├── Apps
 │    │    ├── Rotas
 │    │    ├── APIs
 │    │    └── Uploads
 │    └── Painéis
 └── Infra (CDN, WAF, LB)
```

---

## 5) Subdomain Discovery (descoberta de subdomínios)

### O que é

Processo de identificar **subdomínios associados a um domínio principal**.

Exemplo:

```
example.com
api.example.com
admin.example.com
dev.example.com
staging.example.com
```

### Por que é crítico

- Ambientes de teste esquecidos
    
- APIs não documentadas
    
- Painéis internos expostos
    
- Regras de segurança diferentes
    

---

### Técnicas comuns

- DNS brute force
    
- Certificados TLS (CT logs)
    
- Arquivos públicos (JS, config)
    
- Resolução de wildcard
    

---

### O que observar

- Subdomínios com nomes:
    
    - dev
        
    - test
        
    - staging
        
    - beta
        
    - old
        
- Subdomínios com resposta diferente
    
- Subdomínios sem autenticação
    

---

## 6) Application Discovery (descoberta de aplicações)

### O que é

Identificar **quais aplicações existem dentro do mesmo domínio ou subdomínio**.

Exemplo:

```
/login
/admin
/dashboard
/painel
/api
/uploads
```

---

### Técnicas

- Análise de HTML
    
- Análise de JavaScript
    
- Respostas HTTP
    
- Redirecionamentos
    
- Headers
    

---

### Perguntas-chave

- Existe painel administrativo?
    
- Existe área interna?
    
- Existe área de upload?
    
- Existe versão antiga da aplicação?
    

---

## 7) Descoberta de APIs (API Discovery)

### Como identificar APIs

Sinais comuns:

- Rotas como `/api`, `/v1`, `/v2`
    
- Respostas em JSON
    
- Headers `application/json`
    
- Chamadas feitas via JavaScript
    

---

### Exemplo prático

Você abre o site e observa no navegador:

```
GET /api/users/me
GET /api/orders
POST /api/login
```

Isso indica:

- Backend separado
    
- Lógica concentrada na API
    
- Alto valor para análise
    

---

### APIs “padrão” comuns

- `/api`
    
- `/api/v1`
    
- `/rest`
    
- `/graphql`
    
- `/auth`
    
- `/login`
    
- `/users`
    

---

## 8) Web Fuzzing (descoberta por força controlada)

### O que é Web Fuzzing

Envio automatizado de requisições com **listas de palavras (wordlists)** para descobrir:

- diretórios
    
- arquivos
    
- endpoints
    
- parâmetros
    

---

### Exemplo conceitual

```
/admin
/admin/login
/admin/old
/backup
/config
```

---

### Para que serve no recon

- Descobrir áreas não linkadas
    
- Identificar funcionalidades escondidas
    
- Mapear superfície de ataque real
    

---

## 9) Automation no Recon

### Por que automatizar

- Muitos alvos
    
- Muitos subdomínios
    
- Muitas rotas
    
- Pouco tempo
    

Automação permite:

- consistência
    
- repetibilidade
    
- menos erro humano
    

---

### O que geralmente é automatizado

- Subdomain discovery
    
- Resolução DNS
    
- Verificação de HTTP status
    
- Coleta de headers
    
- Identificação de tecnologias
    
- Fuzzing básico
    

---

## 10) Recon em JavaScript (ponto crítico)

Arquivos `.js` públicos são **mina de ouro**.

Você pode encontrar:

- Endpoints de API
    
- Rotas internas
    
- Feature flags
    
- URLs antigas
    
- Chaves públicas
    
- Nomes de funções sensíveis
    

---

## 11) Como extrair o máximo de informação de um site

Checklist mental de recon web:

- Domínio principal
    
- Subdomínios ativos
    
- Tecnologias usadas
    
- CDN / WAF / Load Balancer
    
- Headers HTTP
    
- Cookies
    
- Rotas visíveis
    
- Rotas escondidas
    
- APIs
    
- Versões
    
- Ambientes paralelos
    

---

## 12) Recon + Infraestrutura

Durante o recon, identifique:

- CDN presente?
    
- WAF presente?
    
- Respostas alteradas?
    
- Rate limit?
    
- IP real oculto?
    

Isso muda **como você interpreta os testes depois**.

---

## 13) Recon não é ataque

Importante reforçar:

> Recon é **observação e mapeamento**, não exploração.

O objetivo é:

- entender o sistema
    
- documentar o que existe
    
- reduzir risco e ruído
    

---

## 14) Exemplo de recon bem feito (visão prática)

```
Domínio principal encontrado
 → 12 subdomínios
 → 5 aplicações web
 → 2 APIs
 → 1 GraphQL
 → CDN + WAF presentes
 → Painel admin em subdomínio
```

Com isso, o pentest:

- fica direcionado
    
- evita testes inúteis
    
- gera relatório mais forte
    

---

## 15) Erros comuns em Recon

- Pular recon e ir direto para teste
    
- Ignorar JavaScript
    
- Não mapear APIs
    
- Não documentar
    
- Não correlacionar infra + app
    

---

## 16) Resumo final (anotação de curso)

- Recon = coleta de informações
    
- Base de todo pentest web
    
- Inclui subdomínios, apps, APIs
    
- Usa técnicas passivas e ativas
    
- Automação é essencial
    
- JavaScript é fonte rica
    
- Sem recon, o teste perde qualidade
    

---

## Conclusão (mentalidade correta)

> **Pentest web não começa explorando.  
> Começa entendendo.**